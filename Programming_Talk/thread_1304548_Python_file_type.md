---
title: "Python: file type"
date: 2009-10-29
forum: Programming Talk
---

### Post by jesuisbenjamin on 2009-10-29
Hello there,

what i would like to achieve is to find out the type of a file (which is extension-less).
In the shell i would simply type:
```
file filename
```
Which would return eg.
```
filename: Macromedia Flash Video
```

Now i would like to be able to do this with Python, and can think of two ways only:
[LIST]
[*]Calling an equivalent function (which i searched for in vain);
[*]Run os.system('file filename') and retrieve the output (which i don't know how to do)
[/LIST]

Any advice? :-k
Thanks

---

### Post by Arndt on 2009-10-29
> **jesuisbenjamin said:**
> Hello there,

what i would like to achieve is to find out the type of a file (which is extension-less).
In the shell i would simply type:
```
file filename
```
Which would return eg.
```
filename: Macromedia Flash Video
```

Now i would like to be able to do this with Python, and can think of two ways only:
[LIST]
[*]Calling an equivalent function (which i searched for in vain);
[*]Run os.system('file filename') and retrieve the output (which i don't know how to do)
[/LIST]

Any advice? :-k
Thanks

There is the 'commands' module. You can do commands.getoutput instead of os.system and get the output as a string.

---

### Post by unutbu on 2009-10-29
Install the python-magic package (~124KB).
It comes with this example (I've modified it very slightly): /usr/share/doc/python-magic/examples/example.py:

[PHP]#!/usr/bin/env python
import magic
import sys
filename=sys.argv[1]
ms = magic.open(magic.MAGIC_NONE)
ms.load()
ftype =  ms.file(filename)
print ftype
ms.close()
[/PHP]

Running it yields:
```
% test.py file.flv 
Macromedia Flash Video
```

---

### Post by jesuisbenjamin on 2009-10-29
> **Arndt said:**
> There is the 'commands' module. You can do commands.getoutput instead of os.system and get the output as a string.

Thanks for that. I tried and it works like a charm. 
However, the Python Library explains:
> The subprocess module provides more powerful facilities for spawning new processes and retrieving their results. Using the subprocess module is preferable to using the commands module.

But the documentation on subprocess.Popen() is a big riddle to me and the module and its function seem much more complex than the commands.getstatusoutput()

I tried to play around with the the function and its arguments, but i can't get anything out of it. Can anyone coach me on this?

> **Unutbu said:**
> Install the python-magic package etc...

Thanks Unutbu, but is that not more convoluted than using commands.getstatusoutput()? Or are there some advantages i am missing?

Thanks

---

### Post by unutbu on 2009-10-30
jesuisbenjamin, python's magic module is faster than using subprocess, os.system, or the commands module because the magic module does not open a shell, spawn a subprocess, etc.

In general, if a python module is available to perform a task, it is better to use it than one of those shell-spawning tools.

---

### Post by jesuisbenjamin on 2009-10-30
> **unutbu said:**
> 

[PHP]#!/usr/bin/env python
import magic
import sys
filename=sys.argv[1]
ms = magic.open(magic.MAGIC_NONE)
ms.load()
ftype =  ms.file(filename)
print ftype
ms.close()
[/PHP]

Running it yields:
```
% test.py file.flv 
Macromedia Flash Video
```

Unutbu: could you please help me through your code?

Does sys.argv[1] pick up the argument you add while running the program in the shell? I am not familiar yet with that one.
Also i don't understand the magic.open(magic.MAGIC_NONE) part and where the .load comes from and what it does. .load does not seem to be in the list of functions of magic...
Well in short i don't understand how it works :P

---

### Post by unutbu on 2009-10-30
> Does sys.argv[1] pick up the argument you add while running the program in the shell? 

Yes. sys.argv is a list of the command and the arguments. For example, if your script says
```

print(sys.argv)
```

and you run
```

test.py file.mp3
```

Then you get 
```

['test.py','file.mp3']
```

So sys.argv[0] is 'test.py' and sys.argv[1] is the first argument after the name of the command, 'file.mp3'.

> 
Also i don't understand the magic.open(magic.MAGIC_NONE) part 

I don't know that much about it either, to tell you the truth. I do know though that python-magic provides python bindings for libmagic, which provides the core functionality of the file command. So doing a google search for "libmagic" led me to its man page: [http://linux.die.net/man/3/libmagic](http://linux.die.net/man/3/libmagic)

There I read:
```

The function magic_open() creates a magic cookie pointer and returns it.
```
MAGIC_NONE means no special handling. There are all sorts of other options listed on that man page. 
> 
and where the .load comes from and what it does. .load does not seem to be in the list of functions of magic...

How are you listing the functions? Note that magic.open() returns a "Magic cookie" object. load() is a "Magic cookie" method.

The man page says:

```
The magic_load() function must be used to load the the colon separated list of database files passed in as filename, or NULL for the default database file before any magic queries can performed. 
```

And from "man file" I see
```

     /usr/share/file/magic.mgc  Default compiled list of magic.

```
So I am guessing that magic_load() reads /usr/share/file/magic.mgc.

So I would treat these two lines as a preparation-idiom just to get ms ready. 
```

ms = magic.open(magic.MAGIC_NONE)
ms.load() 

```

> 
Well in short i don't understand how it works 

Maybe that is why they call it magic? :p

I hope this helps. My knowledge about this is limited. Part  of the beauty of using a high-level language like Python is that it comes with high-level modules. You just plug them in and go! Yes, if the details are important for your program, then by all means you'll have to dig deeper, but if you just need something that works and those capabilities are provided by the module, then I don't see anything wrong with using the module as a blackbox and leaving the details to the module developer.

---

### Post by jesuisbenjamin on 2009-10-30
Ha thanks! I also had found the man page online.

> **unutbu said:**
>  Note that magic.open() returns a "Magic cookie" object. load() is a "Magic cookie" method.

I hadn't realised .load() was method of a magic cookie (which i guess is a class of defined by magic ?)

> **unutbu said:**
> 
I hope this helps. [...] Part  of the beauty of using a high-level language like Python is that it comes with high-level modules. You just plug them in and go!

Yes it, does help quite a bit. And perhaps you are right too about using the modules as they are provided. It's just hard at my level to determine what is essential in the learning process and what is not.
Thanks.

---

### Post by jesuisbenjamin on 2009-11-04
OK i got around Magic and try to use it in a small project.

Now i would like to read some file types and when i read .docx file type, [FONT="Courier New"]magic.file[/FONT] returns:

```
Zip archive data, at least v2.0 to extract

```

Why is that? I am not very familiar with .docx documents but shouldn't it return something like [FONT="Courier New"]Office Open XML Document[/FONT]?

Thanks!

---

### Post by unutbu on 2009-11-04
Hi jesuisbenjamin. Does the "file" command return something different? I think "file" and python-magic use the same underlying libmagic library. Unfortunately, that also means the defects of one are also the defects of the other. Sometimes file/magic gets things wrong.

Also, what are you doing with the result from ms.file() ?
Are you using it to launch another program?
If so, perhaps you don't need python-magic. You could call "xdg-open file" instead. (In a terminal, try running
```

xdg-open filename.docx
```
Maybe that would work better.

---

### Post by jesuisbenjamin on 2009-11-04
Hi Unutbu,

Well i am not trying to open the file, i am making a program that would find all readable documents in a specific set of directories.
After that i want to create options to filter the documents i have found etc.

In stead of searching documents by their extensions (which are not always available) i prefered to look for file types and append the file to a list when the file type is wanted.

Using [FONT="Courier New"]file[/FONT] in terminal, the file type returned was the same as what [FONT="Courier New"]magic[/FONT] returned. I tried on 2 different .docx downloaded from 2 different sites, files were not zipped at download time and after.

---

### Post by jesuisbenjamin on 2009-11-11
Hello forum,

Although my project is going forward, i am stumbling on a new issue:

My program finds all pdf-, odt- and doc- documents, it converts them into text to search for a regular expression and return the names of the documents with a match.

With PDF documents i use [FONT="Courier New"]pyPdf[/FONT] to convert them to text -- it works fine. However there are two kinds of PDF: those with alphanumeric content and those which are an image. When an image-pdf is passed in [FONT="Courier New"]pyPdf[/FONT], it gets in trouble.

So i would like to filter image- from alphanumeric-PDFs, but [FONT="Courier New"]magic[/FONT] in IDLE or [FONT="Courier New"]file[/FONT] in the shell both return the same file type for each type of PDF.

How can i filter these?

Thanks

---

### Post by lavinog on 2009-11-13
what kind of trouble?

you might be able to use a try-except block

---

### Post by jesuisbenjamin on 2009-11-13
Yes i thought about the try-except, i have never used this before so i would need to dig in my python book.
But since i want my program to convert and search through many documents in a minimum time, i would prefer filtering off all image-PDF before doing that.

pyPdf itself is a bit too complex for me to find out what's going on:

[PHP]import pyPdf
fullpath = '/home/benjamin/Documents/Administration/SLS/fortis.pdf'
content = ''
# Load Pdf into pyPdf
pdf = pyPdf.PdfFileReader(file(fullpath, 'rb'))
# Iterate pages
for page in range(0, pdf.getNumPages()):
    # Append 'content' string with pdf-extracted text
    content += pdf.getPage(page).extractText() + '\n'

print content[/PHP]

[PHP]Traceback (most recent call last):
  File "/home/benjamin/python/test.py", line 9, in <module>
    content += pdf.getPage(page).extractText() + '\n'
  File "/var/lib/python-support/python2.6/pyPdf/pdf.py", line 1035, in extractText
    content = ContentStream(content, self.pdf)
  File "/var/lib/python-support/python2.6/pyPdf/pdf.py", line 1118, in __init__
    self.__parseContentStream(stream)
  File "/var/lib/python-support/python2.6/pyPdf/pdf.py", line 1157, in __parseContentStream
    operands.append(readObject(stream, None))
  File "/var/lib/python-support/python2.6/pyPdf/generic.py", line 87, in readObject
    return NumberObject.readFromStream(stream)
  File "/var/lib/python-support/python2.6/pyPdf/generic.py", line 232, in readFromStream
    return NumberObject(name)
ValueError: invalid literal for int() with base 10: ''
>>> 
[/PHP]

---

