---
title: "python: arrays of classes."
date: 2011-11-10
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-11-10
Hi-I'm writing a *shred* frontend, along with a mate, you can see it here: [http://code.google.com/p/shredder/]("http://code.google.com/p/shredder/")


However, I've run into a bit of a problem. Currently, files/directories are shredded on at a time in one program loop. I want an array/list so I can shred multiple files in one loop. So I have a class target, which contains a filename, and some options, and a boolean directory/file variable. This is Main.py:

```
#!/usr/bin/python

import array
from GetFile import GetFile
from target import target
from Shred import shred
from Recursive import rshred
import os

files = []
dirs = []
finished = False
#while user inputs:
while(finished != True):
	#target class
	file1 = target
	#get the filename of target	
	file1.filename = GetFile()
	#check directories
	file1.directory = False
	if((os.path.isdir(file1.filename)) == True):
		file1.directory = True
	else:
		 file1.directory = False
	file1.iterations = raw_input("Iterations:	")
	#overwrite file with zeros afterwards? <bool variable needed>
	file1.zero = raw_input("Zero after shredding? [y/n]")

	#check zero input is boolean and expected
	while ((file1.zero != "y") and (file1.zero != "n")):
		file1.zero = ""
		file1.zero = raw_input("Zero after shredding? [y/n]")

	#remove file after shredding?
	file1.remove = raw_input("Remove file after shredding[y/n]")

	#check input for accuracy
	while ((file1.remove != "y") and (file1.remove != "n")):
		file1.remove = ""
		file1.remove = raw_input("Zero after shredding? [y/n]")
	
	#place in appropiate array
	if(file1.directory == True):
		dirs.append(file1)
	else:
		files.append(file1)

	finished = False
	done = raw_input('Finished?[y/n]')
	while(done !="y" and done != "n"):
		done = raw_input('Finished?[y/n]')
	if(done=="y"):
		finished = True
	
        #zero filename to prevent contamination.
	file1.filename = ""

for x in files:
	print(x.filename)

for x in dirs:
	print(x.filename)
shred(files)
rshred(dirs)
	

	

```

where shred() is a standard function to shred things, and rshred() is a modification to recursively shred. (shred doesn't natively support directories) GetFile() returns a filename inputted by user, and sanitizes it en-route. file1 is just a name, 'file' is already used by python.

My problem is that a) when I call file1.filename again, it uses the previous value, a blank value, etc. And other variables get mixed, too. Am I doing something wrong with the arrays?

Any pointers appreciated, coding style as well as problem-based.

Thank you. :)

---

### Post by karlson on 2011-11-10
> **MG&TL said:**
> 
My problem is that a) when I call file1.filename again, it uses the previous value, a blank value, etc. And other variables get mixed, too. Am I doing something wrong with the arrays?

Any pointers appreciated, coding style as well as problem-based.

Thank you. :)

If memory serves there was something that had to do with saving a reference vs. saving value, you may be hitting that.  So you are saving a reference to a variable vs its value.

Conversely I just might be completely off my rocker.=P~#-o (we need a :crazy: smily)

---

### Post by MG&amp;TL on 2011-11-10
I think the 'confused' one usually does for me. :confused: :D

Thanks, karlson, I'll look into it. :)

---

### Post by crdlb on 2011-11-10
What exactly is 'target'? It should probably be a class (and named 'Target', by convention). In your loop, you would write:```
file1 = Target()
``` making an instance of that class for each loop.

As karlson implied, assignment does not make a copy.

---

### Post by MG&amp;TL on 2011-11-10
ah...okay, I come from C/C++, so python classes and lists are a bit hazy. Yeah, target is a class. I'll try that. :)

---

### Post by ofnuts on 2011-11-10
> **MG&TL said:**
> ah...okay, I come from C/C++, so python classes and lists are a bit hazy. Yeah, target is a class. I'll try that. :)
IMHO your code has a structure too complex for the job at hand.

I would use a Shreddable class which takes a filename and has a shred(times,zero,erase). Its shred() method determines if the Shreddable is a file or a directory. In the first case is actually shreds it using the parameters, otherwise it builds a list of Shreddable from the directory contents, and recursively calls shred((times,zero,erase) on each of them (no need to separate dirs from files...).

Your code also screams for a method that take a prompt message and returns a valid Y/N answer from the user (but I loathe scripts that ask questions).

Your "import array" serves no purpose. You are really using lists anyway.

As others have said, without knowing what "target" and "GetFile" do, it's hard to tell what you code does. 

Using modules is nice, but you are overdoing it for such a simple task. You may want to externalize all the UI in a class  (that would include GetFile and the various shred parameters), so that you can switch between a graphical UI and a console by using either of two derived classes, but I don't think it should go much further.

---

### Post by Bachstelze on 2011-11-10
Also what's wrong with just using the shred command?

---

### Post by d3v1150m471c on 2011-11-10
> **Bachstelze said:**
> Also what's wrong with just using the shred command?

 OP is probably testing python.

---

### Post by MG&amp;TL on 2011-11-11
> **Bachstelze said:**
> Also what's wrong with just using the shred command?

For you or me, nothing. For the office user who doesn't know what a command-line is...Also, shredder will have a GUI, and it *does* support directories. :) Neither of which shred does. And to be honest, by that argument, what's the point of nautilus/dolphin/thunar/pcmanfm? Although I agree, if you're using ubuntu, you probably know how to do that. Also I'm hoping for a panel applet or something, which will make it integrate quite nicely into an office routine, I feel.

Okay,so I'm using lists, I know, but if I don't ```
import array
``` it doesn't know what I'm doing. IDK.

Shreddable class...blink, blink. I'm just getting my head around that one....but it sounds good.

Thanks guys, coding is going ahead soon.

---

### Post by MG&amp;TL on 2011-11-11
> **d3v1150m471c said:**
> OP is probably testing python.

Kinda. My friend thotheolh-some of you may know him-wanted a shredding app, and tried to do it with quickly, but if I'm honest, that was doomed to failure.Personally, I'd have written it as a nautilus extension or panel applet, but a stand-alone window is good too.

Yes, I know, I hate scripts that do that too, but this is just the framework for the GUI that will be coming, I'd just rather get it right here first, in familiar territory.

---

### Post by d3v1150m471c on 2011-12-30
You could write some python code to fill the file several times over with random characters but it would probably make more sense to have your python gui os.system('shred') the data. That's the beauty of *nix, most core compenents are designed to work together.

Some python code you may want:
```

for i in range(0,256):
    print(chr(i))

FILE=open('file','rb').read()
#or
FILE=open('file','wb').write('string')

from random import randrange as Rr
print(chr(Rr(0,256)))

FILE_SIZE=len(open('file','rb').read())

```

---

