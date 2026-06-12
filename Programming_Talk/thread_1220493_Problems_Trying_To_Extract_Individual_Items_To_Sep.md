---
title: "Problems Trying To Extract Individual Items To Separate Paths From a Tar File(Python)"
date: 2009-07-22
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-07-22
Ey guys, I am trying to make a script that will extract all items from a tar file into individual paths. Here is my code:

```

#!/usr/bin/env python
#script that restores directory to specified state

import sys, os, tarfile

class G:
	settingsFile = '.restoreSettings.txt'
	settingsFilePresent = 0
	arbitraryIndexValue = 100000
	saveOption = 0
	tarFile = 'restore.tar'
	cwd = ''
	items = []

def checkForFlag(flag):
	return list(flag[1:])

def contains(l,c):#list, character
	for i in range(len(l)):
		if l[i] == c:
			return True
	return False

def checkForHypen(arg):
	if arg[0] == '-':
		return True
	return False

def initOptions(argv):
	if checkForHypen(argv[1]) and contains(checkForFlag(argv[1]),'s'):
		G.saveOption = 1

def saveSettings():
	w = open(G.settingsFile, 'w')
	tar = tarfile.open(G.tarFile, 'w')
	w.write("Restore Settings File")
	for r,d,f in os.walk(os.getcwd()):
		w.write("\n")
		w.write(r)
		for i in range(len(f)):
			w.write(" ")	
			w.write(f[i])
			#os.chdir(r)
			tar.add(r + "/" + f[i])
			
			
	#w.write()
	tar.close()
	w.close()
	
def printTar(members):
	for tarinfo in members:
		yield tarinfo
		
def splitAtFSlash(item):
	c = len(item)-1
	for i in range(len(item)):
		if item[c] == "/":
			return (item[:c+1],item[c+1:])
		c -= 1
	return ('','')

def main(argv):
	if len(argv) > 1:
		initOptions(argv)
	G.cwd = os.getcwd()
	if G.saveOption == 1:
		saveSettings()
		tar = tarfile.open(G.tarFile)
		#tar.extractall(members = printTar(tar))
		G.item = tar.getnames()
		for i in range(len(G.item)):
			(path,fname) = splitAtFSlash(G.item[i]) #BEGIN AREA OF CONCERN
			os.chdir("/")
			os.chdir(path)
			tar.extract(G.item[i],os.getcwd()) #END AREA OF CONCERN
		tar.close()
	else:
		for r,d,f in os.walk(os.getcwd()):
			for i in range(len(f)):
				if f[i] == G.settingsFile:
					G.settingsFilePresent = 1
		if G.settingsFilePresent == 1:
			w = open(G.settingsFile, 'r')
			G.settings = w.readlines()
			w.close()
		else:
			print "No settings file exists!"
			exit()
			

if __name__ == '__main__':
	main(sys.argv)

```

And here are the contents of the tar file:
```

$ tar -tvf restore.tar 
-rw-r--r-- .../...       0 2009-06-12 21:03 home/.../Documents/Programming/Projects/Restore/testarea/test.mp3
-rw-r--r-- .../...    2085 2009-07-22 17:44 home/.../Documents/Programming/Projects/Restore/testarea/restore.py
-rw-r--r-- .../...       0 2009-07-22 17:45 home/.../Documents/Programming/Projects/Restore/testarea/.restoreSettings.txt
-rw-r--r-- .../...       0 2009-06-12 21:03 home/.../Documents/Programming/Projects/Restore/testarea/txt.doc
-rw-r--r-- .../...   11863 2009-07-21 14:50 home/.../Documents/Programming/Projects/Restore/testarea/freezefile.py
-rw-r--r-- .../...       0 2009-06-12 21:03 home/.../Documents/Programming/Projects/Restore/testarea/home/.../Documents/Programming/Projects/Restore/testarea/test.mp3
-rw-r--r-- .../...    2085 2009-07-22 17:44 home/.../Documents/Programming/Projects/Restore/testarea/home/.../Documents/Programming/Projects/Restore/testarea/restore.py
-rw-r--r-- .../...       0 2009-07-22 17:44 home/.../Documents/Programming/Projects/Restore/testarea/home/.../Documents/Programming/Projects/Restore/testarea/.restoreSettings.txt
-rw-r--r-- .../...       0 2009-06-12 21:03 home/.../Documents/Programming/Projects/Restore/testarea/home/.../Documents/Programming/Projects/Restore/testarea/txt.doc
-rw-r--r-- .../...   11863 2009-07-21 14:50 home/.../Documents/Programming/Projects/Restore/testarea/home/.../Documents/Programming/Projects/Restore/testarea/freezefile.py
-rw-r--r-- .../...       0 2009-06-30 14:53 home/.../Documents/Programming/Projects/Restore/testarea/abe/yolo
-rw-r--r-- .../...       0 2009-07-01 00:42 home/.../Documents/Programming/Projects/Restore/testarea/abe/txt.doc
-rw-r--r-- .../...       0 2009-06-30 14:53 home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/yolo
-rw-r--r-- .../...       0 2009-07-01 00:42 home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/txt.doc
-rw-r--r-- .../...       0 2009-06-30 14:53 home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/yolo
-rw-r--r-- .../...       0 2009-07-01 00:42 home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/home/.../Documents/Programming/Projects/Restore/testarea/abe/txt.doc


```
The problem I am having is that it keeps on making a directory named "Home" and places the contents from the tar file in there. I am trying to place each item in the designated path by parsing the path and changing the current directory, which you can see in the code. Any suggestions or things I am overlooking?

Thanks in advance!

Edit: I actually realized why it is making a "Home" directory... its because that is what is saved in the tar file... But I am unsure why the tar file is saving a "Home" directory. Any ideas?

---

### Post by StunnerAlpha on 2009-07-27
I have figured out why tar is putting home directories in my new directory.. its because the entire path is in the tar file and when I extract it, it extracts the entire path, not just the file. Is there any way I can go about just extracting the file itself instead of the entire path? I would like to keep the tar file the way it is, with the path names in there as well. Thanks in advance!

---

### Post by StunnerAlpha on 2009-07-27
Ok so I did a work-around for my last problem and changed my directory to root then extracted the tar file rather than parsing the paths within the text file... Anyways I have a new problem. I am trying to make a backup of everything in a tar file before it removes everything but the backup doesnt seem to be putting all the files into an archive, only the saved amount.

Here is the directory state I have saved with my script:
```

$ ls -aR
.:
.  ..  abe  alpha  freezefile.py  kuntakente  restore.py  test.mp3  txt.doc

./abe:
.  ..  txt.doc  yolo

./alpha:
.  ..  beta

./alpha/beta:
.  ..

./kuntakente:
.  ..

```
And this is what my directory looks like after adding a few files and directories:
```

$ ls -aR
.:
.   abe    bebop.txt      kuntakente    new folder 2       restore.py  txt.doc
..  alpha  freezefile.py  new folder 1  restore (copy).py  test.mp3

./abe:
.  ..  txt.doc  yolo

./alpha:
.  ..  beta

./alpha/beta:
.  ..

./kuntakente:
.  ..

./new folder 1:
.  ..

./new folder 2:
.  ..  another dir  another.doc

./new folder 2/another dir:
.  ..
$

```
Here is the output from my script:
```

$ python restore.py
backup removed
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/test.mp3 to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/bebop.txt to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/restore.py to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/restore (copy).py to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/txt.doc to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/freezefile.py to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/new folder 2/another.doc to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/abe/yolo to new backup file
adding /home/aaron/Documents/Programming/Projects/Restore/testarea/abe/txt.doc to new backup file

```
Contents of the backup archive:
```

$ tar -tvf ../BACKUP.tar 
-rw-r--r-- aaron/aaron       0 2009-06-12 21:03 home/aaron/Documents/Programming/Projects/Restore/testarea/test.mp3
-rw-r--r-- aaron/aaron    4845 2009-07-27 19:02 home/aaron/Documents/Programming/Projects/Restore/testarea/restore.py
-rwxr-xr-x aaron/aaron       0 2009-06-12 21:03 home/aaron/Documents/Programming/Projects/Restore/testarea/txt.doc
-rwxr-xr-x aaron/aaron   11863 2009-07-21 14:50 home/aaron/Documents/Programming/Projects/Restore/testarea/freezefile.py
-rw-r--r-- aaron/aaron       0 2009-06-30 14:53 home/aaron/Documents/Programming/Projects/Restore/testarea/abe/yolo
-rwxr-xr-x aaron/aaron       0 2009-06-12 21:03 home/aaron/Documents/Programming/Projects/Restore/testarea/abe/txt.doc

```
And here is the relevant code in my script:
```

if G.settingsFilePresent == 1 and G.tarFilePresent == 1:
			os.chdir(G.cwd)
			os.chdir("..")
			if os.path.exists(os.getcwd() + "/" + G.backupTarFile):
				os.remove(G.backupTarFile)
				print "backup removed"
			tar = tarfile.open(G.backupTarFile, 'w')
			for r,d,f in os.walk(G.cwd):
				for i in range(len(f)):
					print "adding", r + "/" + f[i], "to new backup file"
					tar.add(r + "/" + f[i])
			tar.close()
			
			removeall(G.cwd)
			
			if not os.path.exists(G.cwd):
				os.mkdir(G.cwd)
			os.chdir(G.cwd)

```
Is there something I am doing wrong or something that I should know before tackling this task? Any help whatsoever appriciated, thanks.

---

### Post by StunnerAlpha on 2009-07-29
Bump... anyone?

---

### Post by benj1 on 2009-07-29
i cant see anything wrong.
first just to discount the obvious you are putting a leading slash on your path 
ie  /home/user/Desktop/foo
not home/user/Desktop/foo

just to be clear its just the tar file being put in a new home directory.
where is this home directory being put?

can you post your full script and a settings file

---

### Post by StunnerAlpha on 2009-07-30
Thanks for the reply. For some reason it works if I try it in anotehr directory... I'll let you know if I come across problems again. Thanks.

---

