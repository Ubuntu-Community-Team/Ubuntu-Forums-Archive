---
title: "Need help about Python"
date: 2008-12-22
forum: Programming Talk
---

### Post by vietwow on 2008-12-22
Hi all,

I am very new in Python Programming, I have written a bash script for creating bittorent files automatically :

```

#!/bin/bash

for file in `ls $1`; do /home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce $1/$file ;done


```

It works fine !

Now I want to port this script to Python, I have tried with this :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.popen("ls -1").readlines():
    cmd = "/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + path + "/" + line
    output = os.popen(cmd).read()

```


when I execute script, I got an error :

```
[root@server]# ./bit.py
Traceback (most recent call last):
  File "./bit.py", line 5, in ?
    path = sys.argv[1]
IndexError: list index out of range
```

Please help me to correct this

Thanks !

---

### Post by mentallaxative on 2008-12-22
Try sys.argv[0] -- Python counts lists starting from zero.

---

### Post by ghostdog74 on 2008-12-22
> **vietwow said:**
> Hi all,

I am very new in Python Programming, I have written a bash script for creating bittorent files automatically :

```

#!/bin/bash

for file in `ls $1`; do /home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce $1/$file ;done


```

It works fine !

Now I want to port this script to Python, I have tried with this :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.popen("ls -1").readlines():
    cmd = "/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + path + "/" + line
    output = os.popen(cmd).read()

```


when I execute script, I got an error :

```
[root@server]# ./bit.py
Traceback (most recent call last):
  File "./bit.py", line 5, in ?
    path = sys.argv[1]
IndexError: list index out of range
```

Please help me to correct this

Thanks !

use the listdir() method of os module to do file listing.  
```

for files in os.listdir(sys.argv[1]):
    #do something


```
since you want to pass in arguments, then make sure you supply it when you call your script
```

# ./myscript.py <mypath>

```

---

### Post by vietwow on 2008-12-22
> **mentallaxative said:**
> Try sys.argv[0] -- Python counts lists starting from zero.

Dear entallaxative,

After I change, now script is :

```
#!/usr/bin/python

import sys

path = sys.argv[0]

import os
for line in os.popen("ls -1").readlines():
    cmd = "/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + path + "/" + line
    output = os.popen(cmd).read()
```

I run script and there is no error but I checked & saw that the script is not run properly, there is no any torrent file, so means the command "maketorrent-console.py" is not run :confused:

---

### Post by SeanHodges on 2008-12-22
> **vietwow said:**
> I run script and there is no error but I checked & saw that the script is not run properly, there is no any torrent file, so means the command "maketorrent-console.py" is not run :confused:

What happens when you run maketorrent-console.py directly? Do you get a torrent file appear? Type it exactly as it would be run by your Python script, e.g.

```
/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/[type path here]/[type line here]
```

Without knowing what maketorrent-console.py does, I'm not sure what it is you are expecting your script to do.

---

### Post by vietwow on 2008-12-22
> **SeanHodges said:**
> What happens when you run maketorrent-console.py directly? Do you get a torrent file appear? Type it exactly as it would be run by your Python script, e.g.

```
/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/[type path here]/[type line here]
```

Without knowing what maketorrent-console.py does, I'm not sure what it is you are expecting your script to do.

Dear SeanHodges,

The maketorrent-console.py is a part of [http://download.bittorrent.com/dl/BitTorrent-5.2.0.tar.gz](http://download.bittorrent.com/dl/BitTorrent-5.2.0.tar.gz) , a command line bittorent client, I use this tool to create a torrent file, its command look likes : /path/to/maketorrent-console.py [URL of Tracker] file_name

and after run this command, it will generate a torrent file (in the same directory) associate with file that you indicated file_name in above command

This script only works with a single file, so I have to write a script to generate torrent files from all files in a specified folder automatically


I tested with bash script (in fist post of this topic), It works well, but with above python script , but it don't generate any torrent file

---

### Post by Tony Flury on 2008-12-22
Have you put print statements inside your loop - to make sure that you are actually getting the correct results from your ls -l command.

As ghostdog74 pointed out - there is a far better way for get a file list from a directory - using the listdir method in the os module.

---

### Post by vietwow on 2008-12-22
Dear Tony Fulry,

Can you tell me the way to print statements inside your loop for getting result of command ?

Thanks

---

### Post by Tony Flury on 2008-12-22
Adding print statements into code is a very basic debugging tool - they key things are adding them to the right places and making sure that you know what they mean

```

#!/usr/bin/python

import sys

path = sys.argv[0]

import os
for line in os.popen("ls -1").readlines():
    print "file found :", line
    cmd = "/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + path + "/" + line
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

Try that - it might help you understand what is going on in the loop - try it in a folder with only a few files first.

---

### Post by vietwow on 2008-12-22
> **Tony Flury said:**
> Adding print statements into code is a very basic debugging tool - they key things are adding them to the right places and making sure that you know what they mean

```

#!/usr/bin/python

import sys

path = sys.argv[0]

import os
for line in os.popen("ls -1").readlines():
    print "file found :", line
    cmd = "/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + path + "/" + line
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

Try that - it might help you understand what is going on in the loop - try it in a folder with only a few files first.

Oh, Thanx Tony Flury, now I know the problem, here it is :

```

file found : htop-0.8.1

About to run : /home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/home/xyz/bit.py/htop-0.8.1

file found : htop-0.8.1.tar.gz

About to run : /home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/home/xyz/bit.py/htop-0.8.1.tar.gz

file found : htop-0.8.1.tar.gz.torrent

About to run : /home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/home/xyz/bit.py/htop-0.8.1.tar.gz.torrent

file found : httpd-2.2.10.tar.gz

About to run : /home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/home/xyz/bit.py/httpd-2.2.10.tar.gz

```

Example with "httpd-2.2.10.tar.gz" file
It should be : 

```
/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/home/xyz/bit.py httpd-2.2.10.tar.gz
```

Instead of :

```
/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce/home/xyz/bit.py/httpd-2.2.10.tar.gz
```

Means now I need to change the slash (/) charater into a space ( ) charate between URL of Tracker and filename.

Now I change code to : 

```
#!/usr/bin/python

import sys

path = sys.argv[0]

import os
for line in os.popen("ls -1").readlines():
    print "file found :", line
    cmd = "/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + " " + path + "/" + line
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

But new problem occurs :

```
[root@server ~]# /home/xyz/bit.py /root/test

file found : wxGTK-2.8.7-2.el5.i386.rpm

About to run : /home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce /home/xyz/bit.py/wxGTK-2.8.7-2.el5.i386.rpm

Traceback (most recent call last):
  File "/home/xyz/bittorrent/maketorrent-console.py", line 61, in ?
    data_dir=config['data_dir'])
  File "/root/BitTorrent-5.2.0/BitTorrent/makemetafile.py", line 84, in make_meta_files
  File "/root/BitTorrent-5.2.0/BitTorrent/makemetafile.py", line 201, in calcsize
  File "/usr/lib64/python2.4/posixpath.py", line 139, in getsize
    return os.stat(filename).st_size

```

It changes my file's path to : 

```
/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce /home/xyz/bit.py/wxGTK-2.8.7-2.el5.i386.rpm
```

It's wrong, path variable must is /root/test/ which take from first argument that user input (means full path is /root/test/wxGTK-2.8.7-2.el5.i386.rpm), but script understand path is path of this script (/home/xyz/bit.py)

Can you help me this problem ?

Thanks in advance

---

### Post by Tony Flury on 2008-12-23
You are using : 

```

path = sys.argv[0]

```

which will give you the filename of the script that you are running.

- what I think  you want is 

```

path = sys.argv[1]

```

Which will be the first argument you pass it - you should try to read the documentation : [http://docs.python.org/](http://docs.python.org/)
specifically : [http://docs.python.org/library/sys.html](http://docs.python.org/library/sys.html)

(I know someone told you early in the thread to use sys.argv[0], but that is probably due to the fact they did not fully understand what your code did or how you used it - and the example you gave in your first post you did not past an argument to your script - which means that sys.argv[1] would not work)

---

### Post by vietwow on 2008-12-23
> **Tony Flury said:**
> You are using : 

```

path = sys.argv[0]

```

which will give you the filename of the script that you are running.

- what I think  you want is 

```

path = sys.argv[1]

```

Which will be the first argument you pass it - you should try to read the documentation : [http://docs.python.org/](http://docs.python.org/)
specifically : [http://docs.python.org/library/sys.html](http://docs.python.org/library/sys.html)

(I know someone told you early in the thread to use sys.argv[0], but that is probably due to the fact they did not fully understand what your code did or how you used it - and the example you gave in your first post you did not past an argument to your script - which means that sys.argv[1] would not work)

Dear Tony Flury,

First I am much obliged to you for your help !

I have made changes code to :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.popen("ls -1").readlines():
    print "file found :", line
    cmd = "/home/dunglt/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + " " + path + "/" + line
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

It's works but now I want to give a path variable to command ls -1, because what my code do is : take argument (directory path) from user input, ls -1 this path, get all file name in this directory and take they as argument in command /home/xyz/bittorrent/maketorrent-console.py

I have tried :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.popen("ls -1 path").readlines():
    print "file found :", line
    cmd = "/home/dunglt/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + " " + path + "/" + line
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

but may be it's wrong, it will "ls" directory named path, not directory in "path" variable. Hope you can help me this final problem :)

Again thanks,

---

### Post by WW on 2008-12-23
You can replace your first use of os.popen() with os.listdir(). That is, change the "for" statement to
```

for line in os.listdir(path):

```
Just be aware that the list of files will include the "hidden" files that begin with ".".

---

### Post by vietwow on 2008-12-23
> **WW said:**
> You can replace your first use of os.popen() with os.listdir(). That is, change the "for" statement to
```

for line in os.listdir(path):

```
Just be aware that the list of files will include the "hidden" files that begin with ".".

Dear WW,

Tried to change :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.listdir(path).readlines():
    print "file found :", line
    cmd = "/home/xyz/bittorrent/maketorrent-console.py http://10.30.12.36:2710/announce" + " " + path + "/" + line
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

but :

```
[root@server ~]# /home/xyz/bit.py /root/test
Traceback (most recent call last):
  File "/home/xyz/bit.py", line 8, in ?
    for line in os.listdir(path).readlines():
AttributeError: 'list' object has no attribute 'readlines'

```

---

### Post by WW on 2008-12-23
Don't use readlines().  listdir() returns a list of file names, so use it like I showed in my previous post.

---

### Post by vietwow on 2008-12-23
> **WW said:**
> Don't use readlines().  listdir() returns a list of file names, so use it like I showed in my previous post.

Dear WW,

The code works great in Linux, but now I run it on Windows (with a little change , such as path ...), now the code is :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.listdir(path) :
    print "file found :", line
    cmd = "C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + path + "\" + line
    print "About to run :", cmd
    output = os.popen(cmd).read()
```

I have installed & test run python on Windows, everything is ok :

```
C:\>C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\asm\Chuong01.ppt
C:\asm\Chuong01.ppt
87.5% complete
C:\>
```.

Now I run script and got and error :

```
C:\Documents and Settings\VietWOW.VIETWOW-27F0049>cd C:\

C:\>bit.py C:\asm
  File "C:\bit.py", line 10
    cmd = "C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce"
 + " " + path + "\" + line

                         ^
SyntaxError: EOL while scanning single-quoted string

```

Can you help to correct my code ?

Thanks

---

### Post by WW on 2008-12-23
The problem is "\". The backslash is the 'escape' character, and it prevents the following double-quote from terminating the string. Instead, it tells python to include the double-quote as part of the string.  To fix this, just change "\" to "\\".

A better way to deal with this is to replace
```

path + "\" + line

```
with
```

os.path.join(path,line)

```
This will automatically use the correct delimiter on both windows and linux.

---

### Post by vietwow on 2008-12-23
> **WW said:**
> The problem is "\". The backslash is the 'escape' character, and it prevents the following double-quote from terminating the string. Instead, it tells python to include the double-quote as part of the string.  To fix this, just change "\" to "\\".

A better way to deal with this is to replace
```

path + "\" + line

```
with
```

os.path.join(path,line)

```
This will automatically use the correct delimiter on both windows and linux.

Dear WW,

This problem is solved but still have another problem, sorry if this bother you

I run the script :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.listdir(path) :
    print "file found :", line
    cmd = "C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)
    print "About to run :", cmd
    output = os.popen(cmd).read()
```

and got output :

```
About to run : Cittorent\maketorrent-console.py http://10.30.12.36:2710/announce
 C:\asm\Chuong09.ppt
file found : Chuong10.ppt
About to run : Cittorent\maketorrent-console.py http://10.30.12.36:2710/announce
 C:\asm\Chuong10.ppt
file found : Chuong11.ppt
About to run : Cittorent\maketorrent-console.py http://10.30.12.36:2710/announce
 C:\asm\Chuong11.ppt
file found : Chuong12.ppt
About to run : Cittorent\maketorrent-console.py http://10.30.12.36:2710/announce
 C:\asm\Chuong12.ppt
file found : Chuong13.ppt
About to run : Cittorent\maketorrent-console.py http://10.30.12.36:2710/announce
 C:\asm\Chuong13.ppt
```

The path of file name is right but the cmd is wrong, It is should "C\bittorent\maketorrent-console.py ..." instead of "Cittorent\maketorrent-console.py ...". I don't know what made this problem ?

---

### Post by WW on 2008-12-23
It's the same problem as with "\".  Change each single backslash to two backslashes.  That is, change
```

    cmd = "C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)

```
to
```

    cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)

```

---

### Post by vietwow on 2008-12-23
Finally, I have succeed with this script, I am really much obliged to Tony Flury, WW and all who helped me

Thanks all :)

---

### Post by WW on 2008-12-23
> **vietwow said:**
> Finally, I have succeed with this script,
Congratulations!

Keep having fun with python...

---

### Post by vietwow on 2008-12-24
Hi all, 

Fisr, Merry Christmast to all :D

During testing this script, the new problem has occur, this script will not work with a folder name include a space

example : I have a folder named "book t" in C:\, and I run :

```
C:\>bit.py C:\book t
Traceback (most recent call last):
  File "C:\bit.py", line 9, in <module>
    for line in os.listdir(path) :
WindowsError: [Error 3] The system cannot find the path specified: 'C:\\book/*.*
'

```

How can I correct my code ?

Now my code is :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
for line in os.listdir(path) :
    print "file found :", line
    cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

Thanks

---

### Post by vietwow on 2008-12-25
Anybody help me ?

---

### Post by Tony Flury on 2008-12-25
I have never used python in windows - in fact i rarely even boot windows on this PC - so i can't help you directly - but - you can start to try to work it out yourself :

The easiest way is to do what you did last time - add in prints so you can see what your code is doing. The error seems to be in the results from os.path.join(path,line) - why not put that in a variable (before you add it to cmd) and print out the result - it might give you a clue or two - you could also print out path and line - so you know what arguments you are passing in.

Also look at the python documents for the libraries you are using - in this case : [http://docs.python.org/library/os.path.html](http://docs.python.org/library/os.path.html)

I am sure someone could come along and completely correct your code for you - but what would you learn then ?

If you really want to learn python, you should bookmark : [http://docs.python.org/](http://docs.python.org/) and keep referring back to it, also work through the tutorial on that site.

---

### Post by vietwow on 2008-12-25
> **Tony Flury said:**
> I have never used python in windows - in fact i rarely even boot windows on this PC - so i can't help you directly - but - you can start to try to work it out yourself :

The easiest way is to do what you did last time - add in prints so you can see what your code is doing. The error seems to be in the results from os.path.join(path,line) - why not put that in a variable (before you add it to cmd) and print out the result - it might give you a clue or two - you could also print out path and line - so you know what arguments you are passing in.

Also look at the python documents for the libraries you are using - in this case : [http://docs.python.org/library/os.path.html](http://docs.python.org/library/os.path.html)

I am sure someone could come along and completely correct your code for you - but what would you learn then ?

If you really want to learn python, you should bookmark : [http://docs.python.org/](http://docs.python.org/) and keep referring back to it, also work through the tutorial on that site.

Dear Tony Flury,

Sure I know that I have to read many books for mastering python, I never think that I will master python from step by step guide helping but my script is serving for my company so I must do this as soon as posible


I really want to thank Tony Flury for learing python guides. Anyway, Hope anyone can correct my code
Thanks

---

### Post by vietwow on 2008-12-25
The problem is solved, not need to change code, just add path in double quote, example "C:\book t"

Thanks all

---

### Post by Tony Flury on 2008-12-25
Can you insert the prints into your code - and show me what path and line actually are in your progam ? In your example you call 
```

C:\>bit.py C:\book t

```
but based on the traceback you got it almost looks like it is being called as : 
```

C:\>bit.py C:\\book/*.*

```
so it might suggest that windows is doing something odd with the path that you pass it.

It would appear at first glance that os.listdir is not as cross platform as we might like but i would need to see the output of prints in your code to be sure.

Can you run this code on your Windows PC and post the full output

```

#!/usr/bin/python

import sys

path = sys.argv[1]
print path

import os

for line in os.listdir(path) :
    print "file found :", line
    joined = os.path.join(path,line)
    print "joined full path :", joined
    cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + joined
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

---

### Post by vietwow on 2008-12-25
> **Tony Flury said:**
> Can you insert the prints into your code - and show me what path and line actually are in your progam ? In your example you call 
```

C:\>bit.py C:\book t

```
but based on the traceback you got it almost looks like it is being called as : 
```

C:\>bit.py C:\\book/*.*

```
so it might suggest that windows is doing something odd with the path that you pass it.

It would appear at first glance that os.listdir is not as cross platform as we might like but i would need to see the output of prints in your code to be sure.

Can you run this code on your Windows PC and post the full output

```

#!/usr/bin/python

import sys

path = sys.argv[1]
print path

import os

for line in os.listdir(path) :
    print "file found :", line
    joined = os.path.join(path,line)
    print "joined full path :", joined
    cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + joined
    print "About to run :", cmd
    output = os.popen(cmd).read()

```

Dear Tony Flury,

Your code works the same with my code 

```
C:\>test.py C:\asm
C:\asm
file found : Chuong01.ppt
joined full path : C:\asm\Chuong01.ppt
About to run : C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\asm\Chuong01.ppt
file found : Chuong02.ppt
joined full path : C:\asm\Chuong02.ppt
About to run : C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\asm\Chuong02.ppt
file found : Chuong03.ppt
joined full path : C:\asm\Chuong03.ppt
About to run : C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\asm\Chuong03.ppt
```

I have another problem, After run this script it will create torrent files with name *.torrent. I need to rename all these files to files with name *.zing

I have tried :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
if os.path.isdir (path):

	for line in os.listdir(path) :
		print "file found :", line
		cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)
		print "About to run :", cmd
		output = os.popen(cmd).read()
	fname = "\*\.torrent"
	newname = "\*\.zing"
	output1 = os.rename(os.path.join(path, fname), os.path.join(path, newname))

else: print 'This is not a directory'
```

But It only creates new torrent files, not rename. I need your help

Thanks

---

### Post by Tony Flury on 2008-12-25
you seems to be trying to rename the file called ".torrent" to ".zing" - whereas i think you want "*.torrent" to "*.zing".

You might find that wont work though - and it might be better to rename the file in the loop immediately after it is created, if you can predict the name of the "torrent" file created

---

### Post by vietwow on 2008-12-25
> **Tony Flury said:**
> you seems to be trying to rename the file called ".torrent" to ".zing" - whereas i think you want "*.torrent" to "*.zing".

You might find that wont work though - and it might be better to rename the file in the loop immediately after it is created, if you can predict the name of the "torrent" file created

Dear Tony Flury,

I have tried to change code as you described above :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
if os.path.isdir (path):

	for line in os.listdir(path) :
		print "file found :", line
		cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)
		print "About to run :", cmd
		output = os.popen(cmd).read()
	
	for line in os.listdir(path) :
	fullpath = os.path.join(path, line)
	output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))
	print "Renaming files ..."

else: print 'This is not a directory'
```

But output is :

```
C:\>bit.py C:\asm
  File "C:\bit.py", line 18
    fullpath = os.path.join(path, line)
           ^
IndentationError: expected an indented block
```

Can you correct me ?

Thanks

---

### Post by Ahadiel on 2008-12-26
> 	for line in os.listdir(path) :
	fullpath = os.path.join(path, line)
	output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))
	print "Renaming files ..."

You need to indent whatever is inside the for loop.
```
	for line in os.listdir(path) :
		fullpath = os.path.join(path, line)
		output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))
		print "Renaming files ..."

```

---

### Post by vietwow on 2008-12-26
> **Ahadiel said:**
> You need to indent whatever is inside the for loop.
```
	for line in os.listdir(path) :
		fullpath = os.path.join(path, line)
		output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))
		print "Renaming files ..."

```

Dear Ahadiel,

I have tried to change code :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os
if os.path.isdir (path):

	for line in os.listdir(path) :
		print "file found :", line
		cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)
		print "About to run :", cmd
		output = os.popen(cmd).read()
	
	for line in os.listdir(path) :
		fullpath = os.path.join(path, line)
		output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))
		print "Renaming files ..."

else: print 'This is not a directory'
```

Now another error :

```

...#code run maketorrent-console.py script well#
...
About to run : C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\asm\Chuong12.ppt
file found : Chuong13.ppt
About to run : C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\asm\Chuong13.ppt
Traceback (most recent call last):
  File "C:\bit.py", line 19, in <module>
    output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))
WindowsError: [Error 3] The system cannot find the path specified
```

What does it mean ?

---

### Post by Ahadiel on 2008-12-26
Why are you renaming the .torrent files to .zing? Your script doesn't even check what the file extensions are.

Also quite possibly maketorrent-console.py is creating the .torrent files in the directory the script is run from. If this is the case, that would explain your "WindowsError: [Error 3] The system cannot find the path specified".

---

### Post by vietwow on 2008-12-26
> **Ahadiel said:**
> Why are you renaming the .torrent files to .zing? Your script doesn't even check what the file extensions are.

Also quite possibly maketorrent-console.py is creating the .torrent files in the directory the script is run from. If this is the case, that would explain your "WindowsError: [Error 3] The system cannot find the path specified".

My manager require a script which can create torrent files and the rename all these torrent file with name *.zing so I have to rename these

---

### Post by Ahadiel on 2008-12-26
> **vietwow said:**
> My manager require a script which can create torrent files and the rename all these torrent file with name *.zing so I have to rename these

Then see the second part of my previous post.

---

### Post by vietwow on 2008-12-26
> **Ahadiel said:**
> Then see the second part of my previous post.

Sorry by I can't understand your second mean, can you explain more ?

---

### Post by Ahadiel on 2008-12-26
> **vietwow said:**
> Sorry by I can't understand your second mean, can you explain more ?

Okay, take a look at this example:

Say you have a file called foo.py located in C:\
If you were to run C:\foo.py, foo.py's current working directory would be C:\
Now, what if foo.py took a folder as an argument?
```
C:\foo.py C:\path\to\folder
```
foo.py's current directory is STILL C:\

How this relates to your code?

maketorrent-console.py most likely creates torrent files in whatever directory it was called from (the script's current working directory). The .torrent files created would therefore not be in "path", but rather in the script's current working directory.

edit: Forgot to include possible solution.
Instead of
```
fullpath = os.path.join(path, line)
```
try
```
fullpath = os.path.join(path, "..\%s" % (line))
```
This solution does however assume that the script was run from the parent directory of "path".

---

### Post by vietwow on 2008-12-26
> **Ahadiel said:**
> Okay, take a look at this example:

Say you have a file called foo.py located in C:\
If you were to run C:\foo.py, foo.py's current working directory would be C:\
Now, what if foo.py took a folder as an argument?
```
C:\foo.py C:\path\to\folder
```
foo.py's current directory is STILL C:\

How this relates to your code?

maketorrent-console.py most likely creates torrent files in whatever directory it was called from (the script's current working directory). The .torrent files created would therefore not be in "path", but rather in the script's current working directory.

edit: Forgot to include possible solution.
Instead of
```
fullpath = os.path.join(path, line)
```
try
```
fullpath = os.path.join(path, "..\%s" % (line))
```
This solution does however assume that the script was run from the parent directory of "path".

Thanks for your help but your solution is not work, still the same error :(

Anyway, thanx

---

### Post by Ahadiel on 2008-12-26
At the very top of your script, add this
```
import os; print os.getcwd()
```
Paste the output here, and also tell me the fullpath to the folder you specified.

---

### Post by vietwow on 2008-12-27
> **Ahadiel said:**
> At the very top of your script, add this
```
import os; print os.getcwd()
```
Paste the output here, and also tell me the fullpath to the folder you specified.

Dear Ahadiel, 

Now my code is :

```
#!/usr/bin/python

import sys

path = sys.argv[1]

import os; print os.getcwd()
if os.path.isdir (path):

	for line in os.listdir(path) :
		print "file found :", line
		cmd = "C:\\bittorent\\maketorrent-console.py http://10.30.12.36:2710/announce" + " " + os.path.join(path,line)
		print "About to run :", cmd
		output = os.popen(cmd).read()
	
	for line in os.listdir(path) :
		fullpath = os.path.join(path, "..\%s" % (line))
		output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))
		print "Renaming files ..."

else: print 'This is not a directory'
```

And this is my output :

```
C:\>bit.py C:\test
C:\
file found : loginpage.html
About to run : C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\test\loginpage.html
Traceback (most recent call last):
  File "C:\bit.py", line 19, in <module>
    output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpat
h, '.zing'))
WindowsError: [Error 3] The system cannot find the path specified


```

"fullpath" that I want is files's name in directory
why I need fullpath ?

My idea is, example I have a file in C:\test\abc.exe
My script will get first argument and put it into "path" variable => so when I run script "C:\bit.py C:\test" then now the value of path variable is "C:\test"

The for loop (for line in os.listdir(path)) will get every files'name in directory and put into "file" variable => so because C:\test only have 1 file "abc.exe" thereforce now value of "file" variable is "abc.exe"

Next, I create new variable named "fullpath" which combines path (now is "C:\test") and file (now is "abc.exe") => generate fullpath is C:\test\abc.exe

Final, I made :

output1 = os.rename(os.path.join(fullpath, '.torrent'), os.path.join(fullpath, '.zing'))

Means combine fullpath (now is C:\test\abc.exe) and .torrent => I have name of torrent file (is C:\test\abc.exe.torrent) and rename to fullpath + .zing (is C:\test\abc.exe.zing)

That's all

Waiting for your help

Thanks

---

### Post by Ahadiel on 2008-12-27
I still think this has something to do with maketorrent-console.py. Check if any torrents exist in C:\

---

### Post by vietwow on 2008-12-27
> **Ahadiel said:**
> I still think this has something to do with maketorrent-console.py. Check if any torrents exist in C:\

No, when I run above command, torrent file only exist on path that I have given to argument, means now torrent file is in C:\test

You can test this, first download [http://download.bittorrent.com/dl/BitTorrent-5.2.0.tar.gz](http://download.bittorrent.com/dl/BitTorrent-5.2.0.tar.gz) unzip & rename it into C:\bittorent, after that, save my script to C:\bit.py, make a folder for testing (I use C:\test as mentioned) and run the script

---

### Post by chrisjmyers1204 on 2008-12-27
I don't know if it matters or not,or if it would help out any at all but in this:
```
About to run : C:\bittorent\maketorrent-console.py http://10.30.12.36:2710/announce C:\test\loginpage.html

```
bittorrent is spelled with double r's, so it would look like this:
```
About to run : C:\bittorrent\maketorrent-console.py http://10.30.12.36:2710/announce C:\test\loginpage.html

```
spelling doesn't seem that important to me, but it may help something.:)

---

### Post by Ahadiel on 2008-12-27
You can get rid of the "..\" in your second for loop, as it seems your torrents aren't in C:\, but in C:\test.

---

