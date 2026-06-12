---
title: "Problem running Python with PyPDF"
date: 2011-08-01
forum: Programming Talk
---

### Post by YouBurntYou on 2011-08-01
Hi,

I have made a simple code to test a Python module called pyPDF, which allows you to play with PDF files.

I have installed PyDev on Eclipse and set it up. 

I'm having a problem.. it's not allowing me to run the code, giving me this error:

```
Traceback (most recent call last):
  File "/home/brian/pdfm.py", line 5, in <module>
    pdfOne = PdfFileReader(file("/home/brian/PDFs/pdf1.pdf", "rb"))
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/pdf.py", line 374, in __init__
    self.read(stream)
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/pdf.py", line 775, in read
    newTrailer = readObject(stream, self)
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/generic.py", line 67, in readObject
    return DictionaryObject.readFromStream(stream, pdf)
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/generic.py", line 531, in readFromStream
    value = readObject(stream, pdf)
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/generic.py", line 58, in readObject
    return ArrayObject.readFromStream(stream, pdf)
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/generic.py", line 153, in readFromStream
    arr.append(readObject(stream, pdf))
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/generic.py", line 69, in readObject
    return readHexStringFromStream(stream)
  File "/usr/local/lib/python2.7/dist-packages/pyPdf/generic.py", line 276, in readHexStringFromStream
    txt += chr(int(x, base=16))
ValueError: invalid literal for int() with base 16: '\x00\x00'

```


This is the code I tried to run:
```
from pyPdf import PdfFileWriter, PdfFileReader #@UnresolvedImport

output = PdfFileWriter()

pdfOne = PdfFileReader(file("/home/brian/PDFs/pdf1.pdf", "rb"))
pdfTwo = PdfFileReader(file("/home/brian/PDFs/pdf2.pdf", "rb"))
 
output.addPage(pdfOne.getPage(0))
output.addPage(pdfTwo.getPage(0))
 
outputStream = file(r"output.pdf", "wb")
output.write(outputStream)
```

I have also tried to run it from IDLE and from Terminal (I'm using Linux)

Can anyone help please?

Thanks & Regards,
blivori

---

