---
title: "Convert a string into a command in Python"
date: 2009-03-27
forum: Programming Talk
---

### Post by Mardok45 on 2009-03-27
```

import sys, glob

#Insert any additional distributions here

class Arch:
	def __init__(self):
		self.updateCommand = 'pacman -Qu'
		self.syncCommand = 'pacman -Sy'
	
	#Searches for the size of a specific package.
	def getPackageSize(self,pkg):
		#Use glob to search for the package in any one of the repository's since pacman doesn't say.
		desc_path = glob.glob('/var/lib/pacman/sync/*/'+pkg+'/desc')[0]
		#Open the desc file and seperate all the lines into a list
		desc = open(desc_path).readlines()
		#The size of the package is underr CSIZE, so search for CSIZE and use the index after it.
		size = desc[desc.index('%CSIZE%\n')+1]
		return size

OS = sys.argv[1]

```

I'm new to Python.  For one of my first projects, I'm trying to write a generic update notifier for Conky.

My problem is that I'm planning on adding a bunch of classes for this and I don't want to write a whole bunch of if/else's for each distribution.  What I mean is:

```

OS = ""
if sys.argv[1] == "Arch":
  OS = Arch()
elif sys.argv[1] == "Gentoo":
  OS = Gentoo()
elif sys.argv[1] == "Mandriva":
  OS = Mandriva()

```

Is there a way to turn a string into a Python command?  Like:

```

turn_string_into_command("OS = " + sys.argv[1] + "()")

```

---

### Post by ghostdog74 on 2009-03-27
if you don't want to use that many if/else, you can put your commands in a dictionary. Just an example.

```

def func_listdir(<args>):
  ....

def func_listfile(<args>):
  ...

execfunctions = { 'listdir' : ( func_listdir, ['**arg'] ) ,
                  'listfile' : (func_listfile , ['**arg'] ),

execfunctions[listdir][func_listdir](arg) #execute the function

```

---

### Post by Majorix on 2009-03-27
You might want to read [here]("http://docs.python.org/library/os.html"), especially the os.system part of it.

---

### Post by Flimm on 2009-03-27
I think you're looking for [eval](http://lybniz2.sourceforge.net/safeeval.html), which can be quite dangerous, so be careful.

---

### Post by Can+~ on 2009-03-27
The safest way would be to use a dictionary

[PHP]oslist = {"Arch":Arch(), "Gentoo":Gentoo(), ... }

thisOS = oslist[sys.argv[1]][/PHP]

Another way would be to have a class

[PHP]class CompatibilityLayer:
	def Gentoo(self):
		#Do stuff for gentoo

	def Arch(self):
		#Do stuff for Arch

complayer = CompatibilityLayer()
complayer.__dict__(sys.argv[1])
[/PHP]
(Which is pretty much the previous idea of using a dict, but using the implicit dictionary on a class). This is a rather crazy idea I had, it could make things tidier, but if user types __init__ or any private method of the class, it could be ugly. So I think the first method is better.

Also, avoid using "OS" as a variable, there's a library called os.

Btw, isn't there a library to get the specific linux distro?

***edit:** Yes, there is:

[platform.dist]("http://docs.python.org/library/platform.html#unix-platforms")()

---

### Post by nvteighen on 2009-03-27
> **ghostdog74 said:**
> if you don't want to use that many if/else, you can put your commands in a dictionary. Just an example.

```

def func_listdir(<args>):
  ....

def func_listfile(<args>):
  ...

execfunctions = { 'listdir' : ( func_listdir, ['**arg'] ) ,
                  'listfile' : (func_listfile , ['**arg'] ),

execfunctions[listdir][func_listdir](arg) #execute the function

```

Thanks for the tip! Quite simple, but never thought of it!

(You never know whom is your post going to help! :))

---

