---
title: "Working with tar.bz2 tried commands"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by montana68 on 2013-03-06
Hello All
I tried the following command tar -xfj and got the following 

montana@montana-laptop:~$ tar -xfj file:///home/montana/Desktop/gimp-help-2.2.8.0.tar.bz2 
tar: j: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
montana@montana-laptop:~$ 

Maybe I didn't use the command correctly. So if someone could tell me what to do so I can get this tar opened and be able to use the manual.
Thank you for your help.
Montana     :confused:

---

### Post by drmrgd on 2013-03-07
Take out the hyphen from the options:

```
 tar xfj <file> 
```

Tar's one of those weird commands that don't require a hyphen for the options.

---

### Post by Paqman on 2013-03-07
> **montana68 said:**
> So if someone could tell me what to do so I can get this tar opened and be able to use the manual.


Right click > extract here.

Since you're looking at a Gimp manual I'm assuming you're running a graphical desktop. There's no need to use the terminal for little desktop jobs like this.

---

### Post by Impavidus on 2013-03-07
> **montana68 said:**
> Hello All
I tried the following command tar -xfj and got the following 

montana@montana-laptop:~$ tar -xfj file:///home/montana/Desktop/gimp-help-2.2.8.0.tar.bz2 
tar: j: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
montana@montana-laptop:~$ 

Maybe I didn't use the command correctly. So if someone could tell me what to do so I can get this tar opened and be able to use the manual.
Thank you for your help.
Montana     :confused:

Use```
tar -xjf /home/montana/Desktop/gimp-help-2.2.8.0.tar.bz
```
The f options must be the last one before you specify the archive file name. I'm also not sure tar accepts the file:// syntax.

---

### Post by montana68 on 2013-03-07
Hello Paqman
I extracted the files and put them into a folder called Gimp-help. I looked in the folder and there are files in there from gimp. The problem now is that I can't use them as they are like separate parts of you might say a puzzle. I didn't come out as a book, so I still can't use it. 
What is a graphical desktop as I using the desktop that comes with Ubuntu 12.04.
Thank you for your help in advance.
Montan

---

### Post by schragge on 2013-03-07
Both **drmrgd** and **Impavidius** are right. You could either use old-style tar options
```
tar xfj tarball.tar.bz2
``` or new-style options (in this case, the order is significant)
```
tar -xjf tarball.tar.bz2
``` But tar is smart enough to infer compression method from the file extension, so
```
tar xf tarball.tar.bz2
```would work, too.

As to your last question, gimp-help is packaged for Ubuntu.
```

sudo apt-get install gimp-help-en

```

---

### Post by montana68 on 2013-03-07
I used the following command
sudo apt-get install gimp-help-en
I thought that this one would be the easiest for me to use.
I got the following results, if it was installed I can't find where it was put. So could you tell me where I will find it. I have looked everywhere that I thought it would be. 

montana@montana-laptop:~$ sudo apt-get install gimp-help-en
[sudo] password for montana: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 tuxpaint-plugins-default gcompris-data
  gstreamer0.10-fluendo-mp3:i386 tuxpaint-data linux-headers-2.6.32-33
  linux-headers-2.6.32-33-generic liboil0.3:i386 tuxpaint-stamps-default
  python-pysqlite2 gcompris-sound-en
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gimp-help-en
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 26.1 MB of archives.
After this operation, 41.2 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gimp-help-en all 2.6.1-1 [26.1 MB]
Fetched 26.1 MB in 1min 59s (218 kB/s)                                         
Selecting previously unselected package gimp-help-en.
(Reading database ... 674451 files and directories currently installed.)
Unpacking gimp-help-en (from .../gimp-help-en_2.6.1-1_all.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Setting up gimp-help-en (2.6.1-1) ...
montana@montana-laptop:~$

---

### Post by schragge on 2013-03-08
Well, _physically_ it was installed into */usr/share/gimp/2.0/help/en*. You can change to that folder with file manager, or from terminal, e.g. using my script from [thread=2112000]this thread[/thread]. But as it was registered with* doc-base*, it should also be accessible from your GUI help system and probably from inside GIMP, too. What desktop environment are you using?

---

### Post by montana68 on 2013-03-08
I did look in the Gimp but only saw the one that is on line. I don't know what desktop environment I'm using. it is the one that comes with Ubuntu 12.04 when I installed Ubuntu. This one that has the launchers on the left side of the desktop.
Thank you.
Montana

---

### Post by montana68 on 2013-03-08
I did look in the Gimp but only saw the one that is on line. I don't know what desktop environment I'm using. it is the one that comes with Ubuntu 12.04 when I installed Ubuntu. This one that has the launchers on the left side of the desktop.
Thank you.
Montana

---

### Post by schragge on 2013-03-08
Ok, it's Unity then. Sorry, I have zero experience with it. Try to press **Alt**+**F2**, then enter *yelp*. That should open Ubuntu Desktop Guide. Hopefully, you can navigate from there to other help documentation installed on the system.

[highlight]Update.[/highlight]
Well, judging from LP#[lpbug]208147[/lpbug], yelp currently doesn't index documents registered with doc-base. That probably means that your either should point your web browser to the local folder */usr/share/gimp/2.0/help/en*, or install some doc-base client like [dwww]("http://manpages.ubuntu.com/manpages/precise/en/man1/dwww.1.html"), [dhelp]("http://manpages.ubuntu.com/manpages/precise/en/man1/dhelp.1.html") or [doc-central]("http://manpages.ubuntu.com/manpages/precise/man1/doccentral.1.html").

---

### Post by montana68 on 2013-03-08
sorry for the double post. What is the GUI help system? I looked at the script you posted but didn't know which one to use. 
Than you.
Montana

---

### Post by schragge on 2013-03-08
GUI help system is [Yelp]("http://linux.about.com/library/gnome/blgnome7n3c.htm") (GNOME Help Browser).

As to my script: it's *doc.bash*. Rename it to *doc*, and call from terminal like
```

./doc gimp

```
Alternatively, you can download and install the deb file
```
sudo dpkg -i doc_1_all.deb
```
Then
```
doc gimp
``` In this case, you will be able to complete package names with **Tab** key out of the box.

---

