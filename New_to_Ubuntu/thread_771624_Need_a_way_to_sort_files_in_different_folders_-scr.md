---
title: "Need a way to sort files in different folders -script maybe?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by snkiz on 2008-04-27
I had to use testdisk to recover a partition I formated by mistake. What I got was 100 folders each with 500 files, in random order and with random names. I'd like to sort those  files by type recursivly and put them in coresponding folders so I can do an eyes on sort. i'm guessing I need a bash script to do this, but I'm unsure how to proceed.

---

### Post by Bodsda on 2008-04-27
not a pro bash scripter myself but youllbe wanting something along the lines of 

```
#!/bin/bash
user=$(whoami)
sudo mkdir /home/$user/file_for_jpg/ ; sudo mkdir /home/$user/file_for_txt/

cd /path/to/files
sudo mv ./*.txt /home/$user/file_for_txt ; sudo mv ./*.jpg /home/$user/file_for_jpg

```

not brilliant but it gives you the idea

will have to add extras for other file types, you could also have a 

```
sudo mkdir /home/$user/leftovers/
sudo mv ./* /home/$user/leftovers

``` 

but that would need to be the last action you do

---

### Post by snkiz on 2008-04-27
Thats about what I was thinking, but didn't know the commands. will that go into each folder? Or would it need to be run on every one?

---

### Post by Bodsda on 2008-04-27
Ok, here goes im gonna try my best but it may not work completely -- this will only work if your files have file extensions

```
#!/bin/bash
user=$(whoami)
sudo mkdir /home/$user/file_for_txt/ ; sudo mkdir /home/$user/file_for_jpg

cd /plz/enter/the/path/to/the/parent/file/of/files/you/want/sorted

sudo mv ./*.txt /home/$user/file_for_txt ; sudo mv ./*.jpg /home/$user/file_for_jpg

#This is basically the same code as before and it will move any files with the extension .txt & .jpg  add other files and mv commands in the same manner for more file extensions-- after you've made the script-- chmod 777 it then double click and choose 'run in terminal' -- or cd to it through terminal and type ./'name_of_script_.sh'

it only needs to be run once

```

---

### Post by snkiz on 2008-04-27
Thats Perfect! (If it works) I'll try it out when I get home and let you know. btw love the Avatar, its a wallpaper right? where did you get it?

---

### Post by Bodsda on 2008-04-27
i made it 

[http://s258.photobucket.com/albums/hh275/Bodsda/?mediafilter=all]("http://s258.photobucket.com/albums/hh275/Bodsda/?mediafilter=all")

glad you like it and i hope the script works for ya

---

### Post by mr.lee on 2008-04-27
Even though my problems maybe a little bit different, but bassically the same idea. Coz i'm trying to collecting files from (maybe) a random folders... such as JPG. So my question is:

cd /plz/enter/the/path/to/the/parent/file/of/files/you/want/sorted

^^^^ Is that code only work for one folder so I need to repeated it as many folder that I want to be sorted... or can it be work on every folder that I have under /home/(myuser$) ???

Thx bro

---

### Post by sa-mejia on 2009-01-05
In Photorec's wiki page there is a python script (that I have copied at the end of this post) that is supposed to help one automatically sort files by extension.

I tried to use it, however, and this is the error with which I am stuck:  

Traceback (most recent call last):
  File "./photorecSorter.python", line 8, in <module>
    source = sys.argv[1]
IndexError: list index out of range

If anyone has a clue of how to run it, I'd be greatful.  I have no idea about python.

Santiago.


#!/usr/bin/env python
import os
import os.path
import shutil
import string
import sys

source = sys.argv[1]
destination = sys.argv[2]

while os.path.exists(source) != True:
    source = raw_input('Enter a valid source directory\n')
while os.path.exists(destination) != True:
    destination = raw_input('Enter a valid destination directory\n')

for root, dirs, files in os.walk(source, topdown=False):
    for file in files:
        extension = string.upper(os.path.splitext(file)[1][1:])
	destinationPath = os.path.join(destination,extension)
  	
	if os.path.exists(destinationPath) != True:
            os.mkdir(destinationPath)
	if os.path.exists(os.path.join(destinationPath,file)):
            print 'WARNING: this file was not copied :' + os.path.join(root,file)
	else:
	    shutil.copy2(os.path.join(root,file), destinationPath)


(I copied the script from: [http://www.cgsecurity.org/wiki/After_Using_PhotoRec#Sort_files_by_extension](http://www.cgsecurity.org/wiki/After_Using_PhotoRec#Sort_files_by_extension))

---

### Post by Guille Damke on 2009-01-05
Hi Santiago,

How are you running this program?

I have run it doing:
```

./program.py source_directory destination_directory

```
For doing that, I have the program in my current working directory and I have set permission to execute it:
```

chmod a+x program.py

```

- If you are going to use this program often, you can move it to the bin folder, and it will run as a command in your shell.

- Try to create the destination folder before you execute your program.

- Remember that python is an intended language (copy the lines as they are written, taking care of the indentation of each one).

If you have any other question, just ask again.

Saludos,
Guillermo.

---

