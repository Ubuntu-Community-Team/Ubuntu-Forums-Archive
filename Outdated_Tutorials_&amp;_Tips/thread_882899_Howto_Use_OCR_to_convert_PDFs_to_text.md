---
title: "Howto: Use OCR to convert PDFs to text"
date: 2008-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by RequinB4 on 2008-08-07
As anyone who has tried knows, using optical character recognition on pdf files can be confusing, especially since [Tesseract]("http://code.google.com/p/tesseract-ocr/"), repeatedly hailed as the best free ocr software, can only do *tif files.  This method isn't really that hard, it just converts everything to the proper format automatically.

**Step 1: Install needed packages**
```

sudo apt-get install tesseract-ocr tesseract-ocr-eng xpdf-reader xpdf imagemagick xpdf-utils

```

[SIZE="2"]Side Note: You will need to install language packages for tesseract for every other language you wish to use.  For example, package tesseract-ocr-fra allows you to ocr the french language.  Check synaptic package manager[/SIZE]

**Step 2: See if you actually need ocr**

xpdf-utils (which you just installed) provides a pdftotext utility:
```
pdftotext *"Name of PDF file"*
```
If it works, congratulations and don't move on :)

**Step 3: OCR'd**

The following shell script will attempt to ocr your file.  I suggest placing it somewhere in your $PATH so you can run it from the same directory as the pdf file and not have weird filenames.

**NOTE: This program works by converting each page of the PDF file into a 100MB TIFF image.  That means a temporary 100MB increase of hard drive usage per page in your pdf while the program is running.**  If it's an issue, this can be decreased/changed by editing the shell script - either decrease the quality number in pdftoppm or make it do only a few pages at a time - check man pdftoppm

```

#!/bin/sh
mkdir tmp
file=$1
cp ${file} tmp
cd tmp
pdftoppm * -f 1 -l 10 -r 600 ocrbook
for i in *.ppm; do convert "$i" "`basename "$i" .ppm`.tif"; done
for i in *.tif; do tesseract "$i" "`basename "$i" .tif`" -l eng; done
for i in *.txt; do cat $i >> ${file}.txt; echo "[pagebreak]" >> ${file}.txt; done
mv ${file}.txt ../${2}
rm *
cd ..
rmdir tmp

```

**Usage:**
1) Copy the script into gedit or your favorite text editing program and save it.
2)
```
cd */path/to/saved/file/*
chmod +x filename
```
3) Run the script: If it is saved in your $PATH, just type the filename in the console, followed by the name of the file you wish to ocr.  Otherwise, you have to cd to the */path/to/saved/file* and ```
./filename *"Name of PDF File"* *"Name of Output File"*
```

---

### Post by kalaharix on 2008-08-25
RequinB4,

Thanks for this. 

The nld in the script (line 7) should be changed to eng

I am not too hot on scripts but the {name} did not resolve itself either. This left a .txt file in the tmp directory which then prevented its removal.

I ended up simplifying the script to:

> #!/bin/sh
mkdir tmp
cp $@ tmp
cd tmp
pdftoppm $@ -f 1 -l 10 -r 600 ocrbook
convert ocrbook-000001.ppm ocrbook-000001.tif
tesseract ocrbook-000001.tif ocrbook-000001 -l eng
mv ocrbook-000001.txt ..
rm *
cd ..
rmdir tmp

Only does one doc at a time though.
Thanks once again

---

### Post by RequinB4 on 2008-08-25
Thanks for noticing the problem with {name}; and about nld, forgot to mention the language changes; fixing now.

The script you provided will **only do the first page of any one file** - even the old script in the OP only did one file ;)

EDIT: also fixed another typo in the script - it works correctly now ;)

---

### Post by Lucho77 on 2008-08-26
Thank you RequinB4, I had my OCR working fine right after the second step.
I just want to let you know that when the pdf document is coming from scanned, the command 'pdftotext' will not work and creates a blank document.

---

### Post by RequinB4 on 2008-08-26
> **Lucho77 said:**
> 
I just want to let you know that when the pdf document is coming from scanned, the command 'pdftotext' will not work and creates a blank document.

This is because the pdftotext utility ONLY extracts existing "embedded" text from a pdf - i.e. it'll work on pdfs you find, not pdfs you create (unless you create them a certain way, but that's beyond the scope of this thread :)).  

Therefore, if you scan a file, all you have is a bunch of images of the pages in pdf form, not the text itself.  That's what step 3 is for.

---

