---
title: "Python beginner problem"
date: 2007-08-23
forum: Programming Talk
---

### Post by viergeame on 2007-08-23
I've been working through a Python tutorial for the past few nights ([http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python)) and I've been running into a problem that I don't understand at all.  In one of the early exercises I defined a few numbers for variables, and now every time I mess up a variable in something new it throws in a bit of code from one of the early exercises.  It's always the same little bit that gets repeated and I can't figure out how it would happen.  I have an example, it might be a little long, but I'm not sure what all you would need to help.

This is what was in the guide for me to use:
```
a_var = 10
b_var = 15
e_var = 25

def a_func(a_var):
    print "in a_func a_var = ", a_var
    b_var = 100 + a_var
    d_var = 2 * a_var
    print "in a_func b_var = ", b_var
    print "in a_func d_var = ", d_var
    print "in a_func e_var = ", e_var
    return b_var + 10

c_var = a_func(b_var)

print "a_var = ", a_var
print "b_var = ", b_var
print "c_var = ", c_var
print "d_var = ", d_var
```

I know it's a bit broken, it was supposed to be.  Here is what the guide said was supposed to happen.
```
in a_func a_var =  15
in a_func b_var =  115
in a_func d_var =  30
in a_func e_var =  25
a_var =  10
b_var =  15
c_var =  125
d_var = 

Traceback (most recent call last):
  File "C:\Python24\def2", line 19, in -toplevel-
    print "d_var = ", d_var
NameError: name 'd_var' is not defined
```

Here is what I got:
```
in a_func a_var =  15
in a_func b_var =  115
in a_func d_var =  30
in a_func e_var =  25
a_var =  10
b_var =  15
c_var =  125
d_var =  74 + 785 = 859
4 ** 2 = 16
34 / 2 = 17
(5 * 4) - 6 = 14
45 / 20= 2 R 5
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/tempfile.py", line 33, in <module>
    from random import Random as _Random
  File "/usr/lib/python2.5/random.py", line 43, in <module>
    from math import log as _log, exp as _exp, pi as _pi, e as _e, ceil as _ceil
ImportError: cannot import name log

Original exception was:
Traceback (most recent call last):
  File "varfun.py", line 19, in <module>
    print "d_var = ", d_var
NameError: name 'd_var' is not defined
```

I even tried copy/pasting the code from the guide just to make sure I wasn't typing it wrong.  That little bit of math after d_var is something I used several chapters back.  I'm not sure if this makes a difference, but I've been writing out the code in gedit, saving it and running it in a terminal.

---

### Post by scooper on 2007-08-23
I get exactly the expected error when I try that code.  I'd start by assuming your python install is broken.  What Ubuntu and python do you have?  Did you use the Ubuntu Python package?  Is there also another Python that you installed from a different source?

Check for multiple pythons:
```
which -a python
```

Check the version.
```
python --version
```

If it's 2.4 you may have an odd problem, because it's using 2.5 libraries.

You could always try reinstalling the python packages.

One other dumb question.  Is the file in MSDOS format, i.e. CR/LF, rather than just LF for line endings?  That can cause lots of strange errors, although I wouldn't expect it to get as far as it got.

---

### Post by jfinkels on 2007-08-23
How are you executing the program?

Where are the files saved? What is the structure of the directory you are saving them in (i.e. what does ```
ls -al
``` show?)

---

### Post by viergeame on 2007-08-23
Sorry for the super long post....

> **scooper said:**
> I get exactly the expected error when I try that code.  I'd start by assuming your python install is broken.  What Ubuntu and python do you have?  Did you use the Ubuntu Python package?  Is there also another Python that you installed from a different source?

Check for multiple pythons:
```
which -a python
```

Check the version.
```
python --version
```

If it's 2.4 you may have an odd problem, because it's using 2.5 libraries.

You could always try reinstalling the python packages.

One other dumb question.  Is the file in MSDOS format, i.e. CR/LF, rather than just LF for line endings?  That can cause lots of strange errors, although I wouldn't expect it to get as far as it got.

I did the things you suggested.  There is only one python, and the version is 2.5.1.  I'm not sure what you mean about the MSDOS format.  Before Tuesday I had no programming knowledge whatsoever, so excuse my ignorance.

> How are you executing the program?

Where are the files saved? What is the structure of the directory you are saving them in (i.e. what does
Code:

ls -al

show?)

```
nikki@nikki:~$ ls -al
total 716624
drwxr-xr-x 61 nikki nikki     28672 2007-08-23 18:45 .
drwxr-xr-x  3 root  root       4096 2007-04-12 17:12 ..
-rw-r--r--  1 nikki nikki     39785 2007-08-12 18:21 1133028854115.jpg
-rw-r--r--  1 nikki nikki     56997 2007-08-19 01:02 1167925706224.jpg
-rw-r--r--  1 nikki nikki     33930 2007-08-19 01:12 1167925766837.jpg
-rw-r--r--  1 nikki nikki     81119 2007-08-15 18:41 495712267_fd398e89c7.jpg
-rw-r--r--  1 nikki nikki      3563 2007-01-04 01:50 4d11c54ef7c0d8cf09cc843763c361e026537923.jpg
-rw-r--r--  1 nikki nikki       131 2007-08-23 00:47 absolute.py
-rw-r--r--  1 nikki nikki       631 2007-04-28 14:56 .angryddrc
drwxr-xr-x  2 nikki nikki      4096 2004-04-30 14:02 archelder
-rw-r--r--  1 root  root       2393 2005-11-07 05:37 archive_key.asc
drwxr-xr-x 12 nikki nikki      4096 2007-08-18 18:38 avant-window-navigator
-rw-r--r--  1 nikki nikki      6373 2007-08-22 20:43 avatar244857_1.gif
-rw-r--r--  1 nikki nikki       445 2007-08-23 01:18 average2.py
-rw-r--r--  1 nikki nikki       375 2007-08-23 01:14 average.py
drwx------  5 nikki nikki      4096 2007-07-21 02:14 .ayttm
drwxr-xr-x  3 nikki nikki      4096 2007-04-23 23:30 .balazar_saved_games
-rw-------  1 nikki nikki      6737 2007-08-23 17:08 .bash_history
-rw-r--r--  1 nikki nikki       220 2007-04-12 17:12 .bash_logout
-rw-r--r--  1 nikki nikki      2298 2007-04-12 17:12 .bashrc
drwxr-xr-x  2 nikki nikki      4096 2007-08-23 02:07 .beryl
-rw-r--r--  1 nikki nikki       185 2007-08-23 02:07 .beryl-managerrc
-rw-r--r--  1 nikki nikki       319 2007-08-23 02:31 bignumber.py
-rw-r--r--  1 nikki nikki       319 2007-08-23 02:30 bignumber.py~
-rw-r--r--  1 nikki nikki     23203 2007-08-18 18:31 .bzr.log
drwx------  5 nikki nikki      4096 2007-08-22 19:48 .cache
-rw-r--r--  1 nikki nikki      3611 2007-08-16 22:33 calm1.jpg
-rw-r--r--  1 nikki nikki      6263 2007-08-16 22:14 calm.jpg
drwx------ 40 nikki nikki      4096 2007-08-14 23:44 .centericq
drwx------  2 nikki nikki      4096 2007-04-23 22:54 .clay
drwxr-xr-x 10 nikki nikki      4096 2007-08-18 21:04 .config
drwxr-xr-x  2 nikki nikki      4096 2007-06-19 22:22 .crack-attack
-rw-r--r--  1 nikki nikki         0 2007-08-16 20:19 .cvspass
-rw-r--r--  1 nikki nikki        52 2007-08-21 19:50 .DCOPserver_nikki__0
lrwxrwxrwx  1 nikki nikki        32 2007-08-19 19:38 .DCOPserver_nikki_:0 -> /home/nikki/.DCOPserver_nikki__0
drwxr-xr-x  2 nikki nikki      4096 2007-08-21 20:25 Desktop
drwx------  2 nikki nikki      4096 2007-05-05 01:36 .dillo
-rw-------  1 nikki nikki        24 2007-05-27 13:29 .dmrc
-rw-r--r--  1 nikki nikki      1046 2007-08-17 16:05 e17
drwxr-xr-x  2 nikki nikki      4096 2007-08-16 20:12 e17_cvs
-rw-r--r--  1 nikki nikki       162 2007-08-23 00:51 elif.py
-rw-r--r--  1 nikki nikki       161 2007-08-23 00:51 elif.py~
drwxr-xr-x  4 nikki nikki      4096 2007-08-21 16:27 .emerald
drwx------ 10 nikki nikki      4096 2007-07-01 22:24 .enlightenment
-rw-------  1 nikki nikki        16 2007-04-12 22:15 .esd_auth
-rw-r--r--  1 nikki nikki       230 2007-08-23 01:11 evenodd.py
drwxr-xr-x  8 nikki nikki      4096 2007-08-22 19:48 .evolution
lrwxrwxrwx  1 nikki nikki        26 2007-04-12 17:12 Examples -> /usr/share/example-content
-rw-r--r--  1 nikki nikki       292 2007-05-23 18:56 .fbhighlevelshistory
-rw-r--r--  1 nikki nikki       196 2007-05-23 18:57 .fbhighscores
-rw-r--r--  1 nikki nikki      1196 2007-05-23 18:41 .fbrc
-rw-r--r--  1 nikki nikki       336 2007-08-23 00:21 fibonacci.py
drwx------  2 nikki nikki      4096 2007-07-15 23:45 .filezilla
drwxr-xr-x  2 nikki nikki      4096 2007-07-17 17:58 .fontconfig
-rw-r--r--  1 nikki nikki       514 2007-05-10 00:02 .fonts.conf
drwx------  5 nikki nikki      4096 2007-08-23 20:08 .gaim
drwxr-xr-x  4 nikki nikki      4096 2007-08-23 20:11 .galeon
drwx------  5 nikki nikki      4096 2007-08-22 19:48 .gconf
drwx------  2 nikki nikki      4096 2007-08-23 20:09 .gconfd
drwx------  2 nikki nikki      4096 2007-07-15 23:45 .gftp
drwxr-xr-x 21 nikki nikki      4096 2007-08-21 20:26 .gimp-2.2
-rw-r-----  1 nikki nikki         0 2007-08-22 20:12 .gksu.lock
drwxr-xr-x  3 nikki nikki      4096 2007-04-12 22:15 .gnome
drwx------ 16 nikki nikki      4096 2007-08-21 22:29 .gnome2
drwx------  2 nikki nikki      4096 2007-04-12 22:15 .gnome2_private
drwx------  2 nikki nikki      4096 2007-08-08 22:12 .gpe
drwxr-xr-x  2 nikki nikki      4096 2007-08-04 00:48 .gstreamer-0.10
-rw-r--r--  1 nikki nikki        87 2007-05-12 22:53 .gtkrc-1.2-gnome2
-rw-r--r--  1 nikki nikki 729868288 2007-08-16 22:36 gutsy-desktop-i386.iso
-rw-r--r--  1 nikki nikki        12 2007-08-02 18:40 .gweled
-rw-r--r--  1 nikki nikki        20 2007-08-22 22:06 helloworld.py
-rw-r--r--  1 nikki nikki       367 2007-08-23 02:37 highlowcount.py
-rw-r--r--  1 nikki nikki       345 2007-08-23 02:35 highlowcount.py~
-rw-r--r--  1 nikki nikki       470 2007-08-23 01:08 highlow.py
-rw-------  1 nikki nikki      9621 2007-08-22 19:48 .ICEauthority
drwxr-xr-x  2 nikki nikki      4096 2007-04-12 22:29 .icons
drwxr-x---  2 nikki nikki      4096 2007-08-03 00:34 .inkscape
drwxr-xr-x  7 nikki nikki      4096 2007-08-13 00:16 junk
drwx------  4 nikki nikki      4096 2007-05-05 01:34 .kde
drwxr-xr-x  2 nikki nikki      4096 2007-07-27 00:30 kde colors
-rw-------  1 nikki nikki       464 2007-06-09 14:30 .kderc
drwxr-xr-x  2 nikki nikki      4096 2007-06-20 00:29 .kq
-rw-------  1 nikki nikki        35 2007-08-20 23:28 .lesshst
drwxr-xr-x  3 nikki nikki      4096 2007-04-12 22:58 .local
-rw-r--r--  1 nikki nikki       126 2007-08-23 00:28 login.py
-rw-r--r--  1 nikki nikki       124 2007-08-23 00:28 login.py~
-rw-r--r--  1 nikki nikki        53 2007-08-23 00:17 loop.py
drwx------  3 nikki nikki      4096 2007-04-16 22:52 .macromedia
-rw-r--r--  1 nikki nikki       154 2007-08-22 22:30 math.py
-rw-r--r--  1 nikki nikki       323 2007-08-22 23:13 math.pyc
drwxr-xr-x  3 nikki nikki      4096 2007-04-14 17:57 .mcop
-rw-------  1 nikki nikki        31 2007-08-21 20:18 .mcoprc
-rw-r--r--  1 nikki nikki        37 2007-08-22 22:32 mee.py
-rw-r--r--  1 nikki nikki        42 2007-08-22 22:25 me.py
drwx------  3 nikki nikki      4096 2007-04-12 22:15 .metacity
drwx------  4 nikki nikki      4096 2007-05-19 12:42 .mozilla
drwx------  3 nikki nikki      4096 2007-08-15 01:05 .naimlog
-rw-r--r--  1 nikki nikki       156 2007-08-23 02:25 name.py
-rw-r--r--  1 nikki nikki       152 2007-08-23 02:23 name.py~
drwxr-xr-x  3 nikki nikki      4096 2007-08-21 22:29 .nautilus
drwxr-xr-x  2 nikki nikki      4096 2007-05-19 00:44 .nicotine
-rw-r--r--  1 nikki nikki       219 2007-08-22 22:46 numstr.py
drwx------  3 nikki nikki      4096 2007-05-09 20:43 .openoffice.org2
drwxr-xr-x  2 nikki nikki      4096 2007-08-13 00:29 packages
-rw-r--r--  1 nikki nikki       267 2007-08-23 00:25 password.py
drwxr-xr-x  5 nikki nikki     20480 2007-08-15 22:12 pics
drwxr-x--- 10 nikki nikki      4096 2007-04-23 22:13 .pingus
-rw-r--r--  1 nikki nikki       566 2007-04-12 17:12 .profile
-rw-------  1 nikki nikki   1383853 2007-08-23 18:45 programming from the ground
-rw-r--r--  1 nikki nikki       183 2007-08-23 00:15 program.py
-rw-r--r--  1 nikki nikki       135 2007-08-22 23:22 pythagoras.py
-rw-r--r--  1 nikki nikki       138 2007-08-22 23:13 pythagoras.py~
-rw-------  1 nikki nikki    206711 2007-08-23 17:29 python tutorial
drwxr-xr-x  2 nikki nikki      4096 2007-08-19 19:38 .qt
-rw-r--r--  1 nikki nikki       173 2007-08-22 22:53 ratedistance.py
-rw-------  1 nikki nikki    125169 2007-08-23 01:55 .recently-used
-rw-r--r--  1 nikki nikki    161948 2007-08-23 18:42 .recently-used.xbel
-rw-r--r--  1 nikki nikki       236 2007-08-22 22:56 rectangle.py
-rw-r--r--  1 nikki nikki       160 2007-08-22 22:39 spam.py
-rw-r--r--  1 nikki nikki       692 2007-08-14 22:37 stencils
-rw-r--r--  1 nikki nikki       166 2007-08-23 00:09 stringint.py
-rw-r--r--  1 nikki nikki         0 2007-04-12 22:31 .sudo_as_admin_successful
drwx------  2 nikki nikki      4096 2007-05-26 23:55 .synaptic
-rw-r--r--  1 nikki nikki       104 2007-08-22 22:58 temperature.py
drwxr-xr-x  5 nikki nikki      4096 2007-08-03 00:03 .themes
drwx------  5 nikki nikki      4096 2007-05-09 21:17 .thumbnails
drwxr-xr-x  4 nikki nikki      4096 2007-08-22 20:39 .tomboy
-rw-r--r--  1 nikki nikki      1679 2007-08-22 20:39 .tomboy.log
drwx------  7 nikki nikki     28672 2007-08-21 20:08 .Trash
-rw-r--r--  1 nikki nikki       400 2007-08-23 00:43 unlock.py
-rw-r--r--  1 nikki nikki       399 2007-08-23 00:42 unlock.py~
-rw-r--r--  1 nikki nikki       821 2007-08-21 23:06 Unsaved Document 1
drwxr-xr-x  2 nikki nikki      4096 2007-04-13 14:11 .update-manager-core
drwx------  2 nikki nikki      4096 2007-04-12 22:15 .update-notifier
-rw-r--r--  1 nikki nikki        49 2007-08-22 22:42 vara.py
-rw-r--r--  1 nikki nikki       393 2007-08-23 17:07 varfun.py
drwxr-xr-x  2 nikki nikki     69632 2007-08-19 00:56 wallpapers
drwxr-xr-x  2 nikki nikki      4096 2007-08-22 20:37 .wapi
-rw-r--r--  1 nikki nikki        44 2007-08-23 00:12 while.py
-rw-r--r--  1 nikki nikki        72 2007-08-22 22:35 whogoes.py
drwxr-xr-x  4 nikki nikki      4096 2007-08-14 17:17 .wine
-rw-r--r--  1 nikki nikki    186183 2007-08-23 01:55 workstation.jpg
-rw-------  1 nikki nikki       116 2007-08-22 19:48 .Xauthority
-rw-------  1 nikki nikki       192 2007-05-17 20:46 .xcompmgrrc
drwxr-xr-x  2 nikki nikki      4096 2007-04-13 16:25 .xine
-rw-r--r--  1 nikki nikki    200067 2007-08-22 20:04 .xsession-errors

```

---

### Post by pmasiar on 2007-08-23
Code you provided does not let you print this part of your output:

```

4 ** 2 = 16
34 / 2 = 17
(5 * 4) - 6 = 14
45 / 20= 2 R 5

```

Is it possible you are running some different program, and not the one you posted? 

Example is rigged to fail at printing d_var - to show you that although d_var is defined inside function, it is localized in it's body and unknown outside. Because your code does not fail (no error message), d_var is defined somewhere, but not in code snipped you shown us. Some confusion perhaps?

---

### Post by jfinkels on 2007-08-23
> **viergeame said:**
> Sorry for the super long post....



I did the things you suggested.  There is only one python, and the version is 2.5.1.  I'm not sure what you mean about the MSDOS format.  Before Tuesday I had no programming knowledge whatsoever, so excuse my ignorance.



When you save a plaintext file on Windows operating system, at the end of each line, the operating system stores two non-printing characters, the symbols for Carriage Return and Line Feed, also known as Cr and Lf, also known as \r and \n.

When you save a plaintext file on a Mac OS computer, the end of line character is just a Carriage Return, a \r.

When you save a plaintext file on a Linux computer, the end of line character is just a Line Feed, a \n. You can use this in writing strings in python to print a new line (produces the same effect for text output as pressing the "Enter" button does for input):```
print 'Line 1\nLine 2\nLine 3'
```

May I suggest putting all your python files in their own directory? It may be easier for you to manage your files that way. Again, that's only a suggestion. To create a new directory, enter:```
mkdir ~/*mynewdirectory*
``` where *mynewdirectory* is the name of your new directory. To change the current working directory to that directory, Enter the following:```
cd ~/*mynewdirectory*
```

Finally, you can execute your program in two ways. One way is to just write the code to a file, then execute it using the python interpreter this way:```
python *filename*
``` The second way is to prepend this line:```
#!/usr/bin/env python
``` to the top of your code file, then make the file executable:```
chmod +x *filename*
``` and execute it:```
./*filename*
``` Prepending the line starting with the 'shebang' ( #! ) tells the shell (in our case, bash, the Bourne Again SHell, the program with which you interact when you are working in the terminal emulator) which program to use to execute the contents of the file. '/usr/bin/env python' uses the program 'env' to determine the location of the 'python' interpreter.

Which way are you doing it? It seems that your interpreter is getting confused between files, though it isn't immediately obvious to me why...Have you tried putting the file you want to run here in a folder separate from your previous files?

---

### Post by viergeame on 2007-08-23
>  Code you provided does not let you print this part of your output: 

The code in my original post is all that was in the program.  After the first time I had problems with it I copy/pasted it directly from the tutorial into a new page in gedit.  [http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Defining_Functions](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Defining_Functions) There is a link to the tutorial page it is on.

> When you save a plaintext file on a Linux computer, the end of line character is just a Line Feed, a \n. You can use this in writing strings in python to print a new line (produces the same effect for text output as pressing the "Enter" button does for input):
I am using Ubuntu so I would assume it is saving them like this.

> May I suggest putting all your python files in their own directory? It may be easier for you to manage your files that way. Again, that's only a suggestion. To create a new directory, enter: 
I planned on making a new directory for all the python files, I just hadn't done it yet.  I have not been using shebang lines.  The tutorial I'm using hasn't mentioned them yet.  I did she them mentioned in another I started reading, but I just glanced over it so I didn't remember how to do it when I started this tutorial.  Does it make a difference which way I do it?

---

### Post by viergeame on 2007-08-23
When I was moving all the python files into the new directory I made for them I saw a file with a .pyc extension and when I ran it, it came up with 
```
74 + 785 = 859
4 ** 2 = 16
34 / 2 = 17
(5 * 4) - 6 = 14
45 / 20= 2 R 5
```
That is the weird output I've been getting on other things.... I'm not sure what .pyc is or how it got that extension.  Could this somehow be the problem?

<<EDIT:  When I moved the files I kept the .pyc one in a different folder.  But I still got the weird output from the other program, even when they were in seperate folders.>>

---

### Post by jfinkels on 2007-08-23
> **viergeame said:**
> When I was moving all the python files into the new directory I made for them I saw a file with a .pyc extension and when I ran it, it came up with 
```
74 + 785 = 859
4 ** 2 = 16
34 / 2 = 17
(5 * 4) - 6 = 14
45 / 20= 2 R 5
```
That is the weird output I've been getting on other things.... I'm not sure what .pyc is or how it got that extension.  Could this somehow be the problem?

.pyc files are 'byte-compiled' files which essentially represent the machine-code interpretation of your file. If a .pyc file exists where a .py file might have been interpreted, python chooses to just run the .pyc compiled file because this way, it doesn't have to load the .py file into the interpreter and take the time to translate it into machine language. You need not worry about these files; they are a consequence of running files with only a little bit of code. Here's more info on that: [http://www.network-theory.co.uk/docs/pytut/CompiledPythonfiles.html](http://www.network-theory.co.uk/docs/pytut/CompiledPythonfiles.html)

As for your original problem, it seems that python is getting confused when it gets the "d_var undefined in this scope" error and is executing your previous file.

Again, have you tried moving this file to a different location entirely?

I ask about the command you are using to execute the program to make sure you are not accidentally doing:```
python myfile.py someotherfile.py
``` or something silly like that.

This really should not be a concern for you, you should be able to continue your tutorial with no problem, as long as you understand why d_var is undefined in this scope :D

---

### Post by viergeame on 2007-08-23
I went through the folder I moved the python files into again and realised that I accidentally did copy the offending file into the new folder.  I moved it away and now everything is fine again.  Thank you for your help.  :D

---

### Post by jfinkels on 2007-08-23
> **viergeame said:**
> I went through the folder I moved the python files into again and realised that I accidentally did copy the offending file into the new folder.  I moved it away and now everything is fine again.  Thank you for your help.  :D

No problem! Let us know if you need anything else!

---

