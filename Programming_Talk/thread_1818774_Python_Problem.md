---
title: "Python Problem"
date: 2011-08-05
forum: Programming Talk
---

### Post by YouBurntYou on 2011-08-05
I created a Python script using the pyPDF module that basically scans a root directory and all of its sub-directories and merges all the files and puts them in an output folder and renames them according to the folder they where in.

When I'm trying to run the code, when it is going to start processing the sub-folders, it is giving me this error:

```
File "C:\Documents and Settings\student3\Desktop\Test\pdfMergerV1_bkp.py", line 74, in <module>
files_recursively(path)
File "C:\Documents and Settings\student3\Desktop\Test\pdfMergerV1_bkp.py", line 72, in files_recursively
os.path.walk(os.path.realpath(topdir), process_file, ())
File "C:\Python27\lib\ntpath.py", line 263, in walk
walk(name, func, arg)
File "C:\Python27\lib\ntpath.py", line 259, in walk
func(arg, top, names)
File "C:\Documents and Settings\student3\Desktop\Test\pdfMergerV1_bkp.py", line 38, in process_file
pdf = PdfFileReader(file( filename, "rb"))
File "C:\Python27\lib\site-packages\pyPdf\pdf.py", line 374, in __init__
self.read(stream)
File "C:\Python27\lib\site-packages\pyPdf\pdf.py", line 775, in read
newTrailer = readObject(stream, self)
File "C:\Python27\lib\site-packages\pyPdf\generic.py", line 67, in readObject
return DictionaryObject.readFromStream(stream, pdf)
File "C:\Python27\lib\site-packages\pyPdf\generic.py", line 531, in readFromStream
value = readObject(stream, pdf)
File "C:\Python27\lib\site-packages\pyPdf\generic.py", line 58, in readObject
return ArrayObject.readFromStream(stream, pdf)
File "C:\Python27\lib\site-packages\pyPdf\generic.py", line 153, in readFromStream
arr.append(readObject(stream, pdf))
File "C:\Python27\lib\site-packages\pyPdf\generic.py", line 69, in readObject
return readHexStringFromStream(stream)
File "C:\Python27\lib\site-packages\pyPdf\generic.py", line 276, in readHexStringFromStream
txt += chr(int(x, base=16))
ValueError: invalid literal for int() with base 16: '\x00\x00'
```

[IMG]http://s1.postimage.org/qnr99rswp/error_msg.jpg[/IMG]

This is the source code:
```
#----------------------------------------------------------------------------------------------
# Name:        pdfMerger
# Purpose:     Automatic merging of all PDF files in a directory and its sub-directories and
#              rename them according to the folder itself. Requires the pyPDF Module
#
# Current:     Processes all the PDF files in the current directory
# To-Do:       Process the sub-directories.
#
# Version: 1.0
# Author:      Brian Livori
#
# Created:     03/08/2011
# Copyright:   (c) Brian Livori 2011
# Licence:     Open-Source
#---------------------------------------------------------------------------------------------
#!/usr/bin/env <strong class="highlight">python</strong>

import os
import glob
import sys
import fnmatch

from pyPdf import PdfFileReader, PdfFileWriter

output = PdfFileWriter()

path = str(os.getcwd())

x = 0

def process_file(_, path, filelist):
    for filename in filelist:
        if filename.endswith('.pdf'):

            filename = os.path.join(path, filename)
            print "Merging " + filename

            pdf = PdfFileReader(file( filename, "rb"))

            x = pdf.getNumPages()

            i = 0

            while (i != x):

                output.addPage(pdf.getPage(i))
                print "Merging page: " + str(i+1) + "/" + str(x)

                i += 1

                output_dir = "\Output\\"

                ext = ".pdf"
                dir =  os.path.basename(path)
                outputpath = str(os.getcwd()) + output_dir
                final_output = outputpath

                if os.path.exists(final_output) != True:

                                os.mkdir(final_output)
                                outputStream = file(final_output + dir + ext, "wb")
                                output.write(outputStream)
                                outputStream.close()

                else:

                                outputStream = file(final_output + dir + ext, "wb")
                                output.write(outputStream)
                                outputStream.close()

def files_recursively(topdir):
        os.path.walk(os.path.realpath(topdir), process_file, ())

files_recursively(path)

```

---

### Post by LemursDontExist on 2011-08-05
Do you know if it fails on the first file, or if there's a specific file causing trouble?  I would guess this is either a bug in the pdf library, or a corrupt or non-standard pdf.

If you haven't already, try running the script on a folder with only files you've manually opened with pyPdf and know work.

Also, you might consider using [mimetypes]("http://docs.python.org/library/mimetypes.html") instead of file extensions for identifying pdfs - it's very easy to end up with a file with a bad extension.  Mimetypes aren't infallible, but should be a lot more reliable.

Ohh!  and a minor stylistic thing

```
x = some_number
i = 0
while (i != x):
    do_stuff()
    i += 1
```

is a common C idiom, but not really very pythonic - try

```
x = some_number
for i in range(x):
    do_stuff()
```

instead!  It's much cleaner!

---

### Post by YouBurntYou on 2011-08-08
> **LemursDontExist said:**
> Do you know if it fails on the first file, or if there's a specific file causing trouble?  I would guess this is either a bug in the pdf library, or a corrupt or non-standard pdf.

If you haven't already, try running the script on a folder with only files you've manually opened with pyPdf and know work.

Also, you might consider using [mimetypes]("http://docs.python.org/library/mimetypes.html") instead of file extensions for identifying pdfs - it's very easy to end up with a file with a bad extension.  Mimetypes aren't infallible, but should be a lot more reliable.

Ohh!  and a minor stylistic thing

```
x = some_number
i = 0
while (i != x):
    do_stuff()
    i += 1
```

is a common C idiom, but not really very pythonic - try

```
x = some_number
for i in range(x):
    do_stuff()
```

instead!  It's much cleaner!

I tried to open all of the files. It has to be a problem with two nulls (i.e. it is given two nulls).

I don't understand at this level.

---

### Post by LemursDontExist on 2011-08-08
Does it fail on the very first file?  Or does it go through several first?

You're printing the file name right before the error, so it should be easy to figure out which file it's failing on in any case.  Have you tried opening that file manually using pyPdf in the python interpreter?

```
>>> from pyPdf import PdfFileReader
>>> pdf = PdfFileReader(file('file.pdf', 'rb'))
```

The pdf standard is quite complicated and it's very possible that pyPdf doesn't entirely support it.  It's also quite probable that some files aren't made to standard, but that your pdf reader can correct for some errors that pyPdf doesn't know how to handle.

The '\x00\x00' is coming straight from the pdf file - I don't know enough about the pdf spec to know if that's a bug in pyPdf or in the file, but I'm reasonably confident the problem isn't in your code.

If the problem is just with some corrupt files:

```
try:
    pdf = PdfFileReader(file( filename, "rb"))
except ValueError:
    continue
```

should let you skip the bad files.

---

