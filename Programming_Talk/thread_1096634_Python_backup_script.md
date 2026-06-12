---
title: "Python backup script"
date: 2009-03-15
forum: Programming Talk
---

### Post by matmatmat on 2009-03-15
I'm trying to make a script that does time based backups:
[PHP]
import os
from os.path import dirname
import shutil
from time import time

def CheckDirectory(directory, backupdir):
   exist = False
   dirlist = os.listdir(directory)
   for f in dirlist:
      newf = directory + '/' + f
      if os.path.isdir(f) == True:  
	CheckDirectory(newf, backupdir)
      else:	
	copy_file = backupdir + newf
	dt = os.path.getmtime(newf)
	copy_parent = dirname(copy_file)
	if os.path.exists(copy_parent):
	  contents = os.listdir(copy_parent)
	  if len(contents) > 0:
	    print "exist"
	    exist = True	    
	else:
	  os.makedirs(copy_parent)
	if dt > lastrun:
	   print "Backing up " + newf
	   shutil.copyfile(newf, copy_file + '.' + str(dt))
	
	elif exist == False:
	   print "Backing up " + newf
	   shutil.copyfile(newf, copy_file + '.' + str(dt))


lastrun = os.path.getmtime('/home/matio/.backup')
backupdir = '/home/matio/backup'
CheckDirectory('/home/matio/Documents', backupdir)
f = open('/home/matio/.backup', 'w')
f.write(str(time()))
f.close()
[/PHP]
When I run it I get this error:
[PHP]
matio@ubuntu:~/Documents$ python backup.py 
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
exist
Backing up /home/matio/Documents/mikeos-2.0.0/libmikeos-0.1.1/include
Traceback (most recent call last):
  File "backup.py", line 36, in <module>
    CheckDirectory('/home/matio/Documents', backupdir)
  File "backup.py", line 13, in CheckDirectory
    CheckDirectory(newf, backupdir)
  File "backup.py", line 13, in CheckDirectory
    CheckDirectory(newf, backupdir)
  File "backup.py", line 31, in CheckDirectory
    shutil.copyfile(newf, copy_file + '.' + str(dt))
  File "/usr/lib/python2.5/shutil.py", line 51, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 21] Is a directory
[/PHP]
Whats wrong?

---

### Post by Habbit on 2009-03-15
What is wrong is that you are trying to "copy" a directory, which is an operation with no meaning (try using `cp' on it). You need to either traverse the directory yourself, replicating the tree and copying each file, or use an external program that does it for you like `tar'. Actually, why don't you just use tar for backups? AFAIK it supports all the functionality you seem to require, though it's certainly not the king of speed.

---

### Post by matmatmat on 2009-03-16
Why is it copying a  directory?  I thought this:
[PHP]
if os.path.isdir(f) == True:  
  CheckDirectory(newf, backupdir)
[/PHP]
would handle that?

---

### Post by imdano on 2009-03-16
> **matmatmat said:**
> Why is it copying a  directory?  I thought this:
[PHP]
if os.path.isdir(f) == True:  
  CheckDirectory(newf, backupdir)
[/PHP]
would handle that?Could you repost your code, but double-check to make sure the indentation is still correct after you paste it here?  It's hard to tell exactly what's going on because some of your code ended up looking like this: ```
      if os.path.isdir(f) == True:  
    CheckDirectory(newf, backupdir)
      else:    
    copy_file = backupdir + newf
    dt = os.path.getmtime(newf)
    copy_parent = dirname(copy_file)
    if os.path.exists(copy_parent): 
```Which definitely isn't right, and it might be messed up in other places but in a more subtle way.

---

### Post by matmatmat on 2009-03-16
Here it is:
```

# -*- coding: utf-8 -*-
import os
from os.path import dirname
import shutil
from time import time

def CheckDirectory(directory, backupdir):
   exist = False
   dirlist = os.listdir(directory)
   for f in dirlist:
      newf = directory + '/' + f
      if os.path.isdir(f) == True:  
	CheckDirectory(newf, backupdir)
      else:	
	copy_file = backupdir + newf
	dt = os.path.getmtime(newf)
	copy_parent = dirname(copy_file)
	if os.path.exists(copy_parent):
	  contents = os.listdir(copy_parent)
	  if len(contents) > 0:
	    print "exist"
	    exist = True	    
	else:
	  os.makedirs(copy_parent)
	if dt > lastrun:
	   print "Backing up " + newf
	   shutil.copyfile(newf, copy_file + '.' + str(dt))
	
	elif exist == False:
	   print "Backing up " + newf
	   shutil.copyfile(newf, copy_file + '.' + str(dt))


lastrun = os.path.getmtime('/home/matio/.backup')
backupdir = '/home/matio/backup'
CheckDirectory('/home/matio/Documents', backupdir)
f = open('/home/matio/.backup', 'w')
f.write(str(time()))
f.close()

```

---

### Post by imdano on 2009-03-16
I think this is your problem:
[php]   for f in dirlist:
      newf = directory + '/' + f
      if os.path.isdir(f) == True:  
[/php]f is only a relative path, which means that if you have a directory structure like this:
/home/
-| matio/
---| test/
-----| otherdir/

And you run the script from the matio directory, you're going to be running:
```
os.path.isdir("test")
os.path.isdir("otherdir")
```

matio/test exists and is a directory, so it will return True, but matio/otherdir does not exist, so it will return False.  You need to pass newf to os.path.isdir(), so you get ```
os.path.isdir("/home/matio/test")
os.path.sidir("/home/matio/test/otherdir")
```

edit: Also, you might want to look into os.walk(), I think it's basically designed for exactly what you're trying to do.

---

### Post by matmatmat on 2009-03-16
Thanks, it worked!

---

### Post by matmatmat on 2009-03-17
I've now moved on to the listing part of the script that lists the avaliable backups, so far I have this:
```

def Listbackups(filename):
   fil = backupdir + filename
   copy_parent = dirname(fil)
   
   dirlist = os.listdir(copy_parent)

```
and I want to do this (c#)
```

static void ListBackups(string filename) {
        string file = Path.GetFullPath(filename);
        string copy_parent = Path.GetDirectoryName(BackupLocation + file);
        string search_filter = Path.GetFileName(file) + ".*";
        
        string[] backups = Directory.GetFiles(copy_parent, search_filter);
        
        // this is the new loop, replacing foreach
        for (int i = 0; i < backups.Length; i++) {
                string ext = Path.GetExtension(backups[i]).Substring(1);
                long backup_date = long.Parse(ext);
                string write_time = DateTime.FromFileTime(backup_date).ToString();

                // this next line is totally new, so don't worry about it for now
                Console.WriteLine(string.Format("{0}: {1}", i + 1, write_time));
        }                       
}

```
this in python.
I'm trying to make [this]("http://www.tuxradar.com/content/hudzilla-coding-academy-project-three") only in python.
I'm stuck on checking if anything in dirlist is the same as the filename + (eg) .123456789.
Would it use something like:
```

list = ["name6013456789"]
a = "hello"
b = len(a)
############
c = list[::b]
# or #####
for i in range(b)
   # ?
############

```

---

### Post by Sprut1 on 2009-03-17
> **imdano said:**
> edit: Also, you might want to look into os.walk(), I think it's basically designed for exactly what you're trying to do.

Yes os.walk is brilliant

```

for root, dirs, files in os.walk(path):
     Do()

```

---

### Post by imdano on 2009-03-17
> **matmatmat said:**
> I'm stuck on checking if anything in dirlist is the same as the filename + (eg) .123456789.
Would it use something like:
```

list = ["name6013456789"]
a = "hello"
b = len(a)
############
c = list[::b]
# or #####
for i in range(b)
   # ?
############

```What do you mean exactly?  I think you could just do ```
for f in dirlist:
    if f.startswith(filename + "."):
        # Do something...
```But the code example you posted doesn't quite make sense to me, so I'm not sure if that's what you're trying to do.

---

### Post by matmatmat on 2009-03-17
Thanks, that worked! How would I write the rest of the function?

---

### Post by matmatmat on 2009-03-17
I'm trying to get the extension of the file unfortunately the file have multiple "."'s in:
```

backup.py.1237229218.0

```
I've tried os.path.splitext but it returns:
```

('backup.py.1237229218', '.0')

```
What should I do?
Also is there a way to convert, for example the date/time string 1237229218.0 to a human redable date/time string?

---

### Post by keithweddell on 2009-03-17
Tell you what, why not just ask them to write it for you?  Or you could make it a learning experience by checking the [python documentation]("http://docs.python.org/library/") which is pretty comprehensive.

Keith

---

### Post by matmatmat on 2009-03-17
I've done it:
```

# -*- coding: utf-8 -*-
import os
from os.path import *
import shutil
import sys
import time

def Restorebackup(filename, version):
   fil = backupdir + abspath(filename)
   copy_parent = dirname(fil)
   backup = []
   dirlist = os.listdir(copy_parent)
   for f in dirlist:
     if os.path.isdir(f) == False:
       if f.startswith(filename):
	backup.append(f)
   version = int(version)
   version -= 1
   bfile = backupdir + abspath(backup[version])
   print bfile
   print filename
   shutil.copyfile(bfile, filename)

def Listbackups(filename):
   fil = backupdir + abspath(filename)
   copy_parent = dirname(fil)
   backup = []
   dirlist = os.listdir(copy_parent)
   for f in dirlist:
     
     if os.path.isdir(f) == False:
       if f.startswith(filename):
	backup.append(f)
   i = 1
   for f in backup:
      a = splitext(f)
      last = a[1]
      a = a[0]
      first = splitext(str(a))
      fi = first[1]    
      full = float(fi.lstrip('.') + last)
      t = time.gmtime(full)
      print str(i) + ' ' + first[0] + ' ' + str(t[3]) + ':' + str(t[4]) + ' ' + str(t[2]) + '/' + str(t[1]) + '/' + str(t[0])
      i += 1              
   
def CheckDirectory(directory, backupdir):
   exist = False
   dirlist = os.listdir(directory)
   for f in dirlist:
      newf = directory + '/' + f
      if os.path.isdir(newf) == True:  
	CheckDirectory(newf, backupdir)
      else:	
	copy_file = backupdir + newf
	dt = os.path.getmtime(newf)
	copy_parent = dirname(copy_file)
	if os.path.exists(copy_parent):
	  contents = os.listdir(copy_parent)
	  if len(contents) > 0:
	    print "exist"
	    exist = True	    
	else:
	  os.makedirs(copy_parent)
	if dt > lastrun:
	   print "Backing up " + newf
	   shutil.copyfile(newf, copy_file + '.' + str(dt))
	
	elif exist == False:
	   print "Backing up " + newf
	   shutil.copyfile(newf, copy_file + '.' + str(dt))

lastrun = os.path.getmtime('/home/matio/.backup')
backupdir = '/home/matio/backup'

if sys.argv[1] == "list":
    Listbackups(sys.argv[2])
elif sys.argv[1] == "restore":
    Restorebackup(sys.argv[2], sys.argv[3])
else:
    CheckDirectory(sys.argv[1], backupdir)
    f = open('/home/matio/.backup', 'w')
    f.write(str(time.time()))
    f.close()


```
Sorry if I were asking you too many questions, it's just I couldn't find any answers until I looked through the docs.

---

### Post by Can+~ on 2009-03-17
You can get a tuple of day and hour with:

[PHP]datetime.datetime.now()[/PHP]

[http://docs.python.org/library/datetime.html#datetime.datetime.now](http://docs.python.org/library/datetime.html#datetime.datetime.now)

Best thing, is that it has it's own __str__ definition, so you can easily do:

[PHP]str(datetime.datetime.now())[/PHP]

Which returns
```
'2009-03-17 13:50:48.275885'
```

---

### Post by matmatmat on 2009-03-19
Thanks for the reply but I don't need the current date/time.

---

### Post by matmatmat on 2009-03-19
Is there anything I should add that would make it better/feature packed/more app like

---

### Post by matmatmat on 2009-03-20
bump

---

### Post by matmatmat on 2009-03-21
Last bump

---

### Post by matmatmat on 2009-03-21
As you can see from my signature, it is now on launchpad.

---

