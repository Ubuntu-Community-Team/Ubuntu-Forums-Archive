---
title: "script (using ffmpeg) to convert audio"
date: 2010-07-05
forum: Programming Talk
---

### Post by M4rotku on 2010-07-05
hey guys,

I'm trying to write a small script to move through the directories in my music folder recursively and convert each non-mp3 file to mp3.  I keep getting an error telling me that I'm exceeding the max recursion limit, but my directories only go 3 deep.  Could anyone point out to me what I am doing wrong in my recursion?  (side note:  Test is a test directory containing wma files and other directories (with more wma files))

Much thanks,
M4rotku

File attached

---

### Post by DaithiF on 2010-07-06
Hi, every time you call Recurse, you start from the same location (self.location, as set in the __init__ method).  So it runs and runs until it hits the recursion limit.  Presumably what you want instead is to pass a parameter to Recurse giving it a location to start from.

---

### Post by M4rotku on 2010-07-06
Ow, I think I accidentally took that reassignment part out when I was erasing another part of the program.  I will put it back in and have another go at running it.  I can't believe I forgot to put it back in.

Much thanks,
M4rotku

---

### Post by M4rotku on 2010-07-06
Ok, after fixing the error mentioned before, it ran without any errors, but it didn't actually convert anything.  So, something must still be messed up.  Here is the new code:

[PHP]#! /usr/bin/env python
### Music Converter

import os

class Converter():
	def __init__(self):
		self.location = '/home/joey/Programs/Test'  # sets the location in which the recursive conversions are going to be performed
	
	def Recurse(self):
		""" Recurse() recurses through the given <location> and performs the given <operation> (usually a function call)
		Must have os imported to use Recurse()
		The <operation> in this case will be running the converter """
	
		dirlist = os.listdir(self.location)
		for item in dirlist:
			fullname = os.path.join(self.location,item)
			if os.path.isdir(fullname):
				self.location = fullname
				self.Recurse()
		#for item in dirlist:		# commented out to see if we can handle folders and files at the same time
		#	fullname = os.path.join(location,item)
			if os.path.isfile(fullname):
				(self.longname, extension) = os.path.splitext(fullname)
				if extension != '.mp3':
					self.name = fullname
				

	def Convert(self):
		""" Converts any file which is not .mp3 into an mp3 """
		new_name = self.longname + '.mp3'
		command = 'ffmpeg -i %s -f mp3 -ab 192k %s' % (self.name,new_name)
		os.system(command)
		
		
if __name__ == '__main__':
	mp3Convert = Converter()
	mp3Convert.Recurse()
[/PHP]

---

### Post by DaithiF on 2010-07-06
Hi,
when does the Convert method get called?

[ thats a rhetorical question, as from the code you posted it never gets called. :) ]

thats one problem.  the other is that your recursion won't work ... by manipulating self.location at various levels in the recursion you are preventing later invocations from carrying on where they left off.

Imagine a simple structure like:
topdir -> subdir1
         -> subdir2

you start off with self.location = topdir.
you populate dirlist with the entries subdir1, subdir2.
you examine the first item, subdir1, decide it is a directory, set self.location to be topdir->subdir1, then call Recurse again.  what happens when that call to Recurse has exited, and you are now back processing subdir2?  you join item to self.location, which gives you topdir->subdir1->subdir2, which doesn't exist
and so subdir2 won't get processed.

you should use a local variable to hold the location, not a class variable.

---

### Post by M4rotku on 2010-07-06
Ugg.  Wow.  Sorry.  I think that might have been another thing I took out while making adjustments and forgot to put back in.  Ok, so I'm putting it back in and changing the variable to a local one and I'll see how it goes.

---

### Post by M4rotku on 2010-07-06
Ok, I'm getting confused as to how to change the class variable to a local variable.  I can just use a local variable within the function, but then how can I set it to the original directory (the starting directory) from outside of the function.  I can't do it from within the function, because then it would just keep getting reset.  I think that's the reason I was trying to use a class variable in the first place.

---

### Post by M4rotku on 2010-07-06
Ok, nvm, I figured that out by just sending it the location as a parameter.  So that is solved and the converter works to some extent.  The problem is that it can't seem to read directories or files that have spaces in them.  It sees the directory 'Test 2' as 'Test' and then cuts off the 2.  It does the same thing with files.  Otherwise it worked fine and all of the files that didn't have spaces and weren't in a directory with spaces in the name were converted.

---

### Post by DaithiF on 2010-07-07
good. in the ffmpeg command enclose the %s in "" marks to handle spaces in file/dir names.

---

### Post by M4rotku on 2010-07-07
Ok.  A lot of progress has been made with that last change, but for some reason it's still only converting some of the files and the rest it leaves untouched.  In my 'Test' folder, there is a wma file and an m4a file and another folder 'Test 2' containing more files of the same sorts.  The program correctly descends first into the 'Test 2' subfolder and converts those files correctly.  But it fails to come out of that folder as it should and convert the files in the original directory.  I thought I had it written so that it would come back up, but it doesn't want to do so for some reason.

The current text of the file is now:

[PHP]#! /usr/bin/env python
### Music Converter

import os

class Converter():
	def __init__(self):
		# nothing to init right now
		pass
	
	def Recurse(self, current_location):
		""" Recurse() recurses through the given <location> and performs the given <operation> (usually a function call)
		Must have os imported to use Recurse()
		The <operation> in this case will be running the converter """
			
		dirlist = os.listdir(current_location)
		for item in dirlist:
			fullname = os.path.join(current_location,item)
			if os.path.isdir(fullname):
				current_location = fullname
				self.Recurse(current_location)
		#for item in dirlist:		# commented out to see if we can handle folders and files at the same time
			#fullname = os.path.join(current_location,item)
			if os.path.isfile(fullname):
				(self.longname, extension) = os.path.splitext(fullname)
				if extension != '.mp3':
					self.name = fullname
					self.Convert()
				

	def Convert(self):
		""" Converts any file which is not .mp3 into an mp3 """
		new_name = self.longname + '.mp3'
		command = 'ffmpeg -i "%s" -f mp3 -ab 192k "%s"' % (self.name,new_name)
		os.system(command)
		
if __name__ == '__main__':
	mp3Convert = Converter()
	current_location = '/home/joey/Programs/Test'
	mp3Convert.Recurse(current_location)
[/PHP]

---

### Post by DaithiF on 2010-07-07
you're still changing the value of a variable that you need to leave unchanged within the method.

instead of this:
```

current_location = fullname 
self.Recurse(current_location) 

```   
[COLOR=#000000][COLOR=#007700]try this:
[/COLOR][/COLOR]```
self.Recurse(fullname)

```[COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]

---

### Post by M4rotku on 2010-07-07
Ok, that seems to have worked.  Thank you very much for your help.  Now I can finally put all of my music on my mp3 player.

Much thanks,
M4rotku

---

