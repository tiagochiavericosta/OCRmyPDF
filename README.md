OCRmyPDF
========

OCRmyPDF adds an OCR text layer to scanned PDF files, allowing them to be searched

To get the script usage, call: sh ./OCRmyPDF.sh -h

Main features
-------------

- Generates a searchable [PDF/A](https://en.wikipedia.org/?title=PDF/A) file from a PDF file containing only images
- Places OCRed text accurately below the image to ease copy / paste
- Keeps the exact resolution of the original embedded images
    - or if requested oversamples the images before OCRing so as to get better results 
- If requested deskews and / or clean the image before performing OCR
- Validates the generated file against the PDF/A-1b specification using [JHOVE](http://jhove.sourceforge.net/)
- Provides debug mode to enable easy verification of the OCR results
- Processes several pages in parallel if more than one CPU core is available

For details: please consult the release notes

Motivation
----------

I searched the web for a free command line tool to OCR PDF files on Linux/UNIX:
I found many, but none of them were really satisfying.
- Either they produced PDF files with misplaced text under the image (making copy/paste impossible)
- Or they did not display correctly some escaped HTML characters located in the hocr file produced by the OCR engine
- Or they changed the resolution of the embedded images
- Or they generated PDF file having a ridiculous big size
- Or they crashed when trying to OCR some of my PDF files
- Or they did not produce valid PDF files (even though they were readable with my current PDF reader) 
- On top of that none of them produced PDF/A files (format dedicated for long time storage / archiving)

... so I decided to develop my own tool (using various existing scripts as an inspiration)

Install
-------

Download OCRmyPDF here: https://github.com/fritz-hh/OCRmyPDF/releases

Copy the file in onto your Linux/*nix machine and extract it.

For usage information, run: 
```shell
sh ./OCRmyPDF.sh -h
```

If not yet installed, the script will notify you about dependencies that need to be installed.
The script requires specific versions of the dependencies. Older version than the ones mentioned in the release notes are likely not to be compatible to OCRmyPDF.

### Docker container

A Docker container is [also available](https://registry.hub.docker.com/u/paulstaab/ocrmypdf/). This includes all of the dependencies and may be easier to set up.
- Install [Docker](https://docs.docker.com/installation/) for your platform
- Run `docker pull paulstaab/ocrmypdf`
- To run OCRmyPDF through Docker:
```shell
docker run -t -i -v "</path/to/pdfdir>:/home/docker/" paulstaab/ocrmypdf \
  OCRmyPDF <additional options> <pdf> <out.pdf>
```

For example:
```shell
cd /home/user/Documents/PDFs
docker run -t -i -v "/home/user/Documents/PDFs:/home/docker/" paulstaab/ocrmypdf \
  OCRmyPDF test.pdf test_ocr.pdf
```

Support
-------

In case you detect an issue, please:

- Check if your issue is already known
- If no problem report exists on github, please create one here: https://github.com/fritz-hh/OCRmyPDF/issues
- Describe your problem thoroughly
- Append the console output of the script when running the debug mode (-g option)
- If possible provide your input PDF file as well as the content of the temporary folder (using a file sharing service like www.file-upload.net)

Press & Media
-------------

- [c't 1-2014, page 59](http://www.heise.de/ct/inhalt/2014/1/58/): Detailed presentation of OCRmyPDF v1.0 in the leading German IT magazine c't 
- [heise Open Source, 09/2014: Texterkennung mit OCRmyPDF](http://www.heise.de/-2356670)

Disclaimer
----------

The software is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
