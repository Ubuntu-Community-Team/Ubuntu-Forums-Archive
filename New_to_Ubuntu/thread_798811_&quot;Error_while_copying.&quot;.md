---
title: "&quot;Error while copying.&quot;"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Rogue Yun on 2008-05-18
I'm as green as they come.

'The folder "Folder Name" cannot be handled because you do not have permissions to read it.'

Background:  Ubuntu Crashed (probably not its' fault but that of my ghetto computer) and I would like to copy the files from my old "/home" partition onto a separate external hard drive.  So I booted with the desktop CD and trying to copy files over, some files are not "starred" and some are.  What may I do to copy those files.  (I have the option of installing Ubuntu again on the "/" and try to leave the "/home" partition alone.  But being as I've never done that before I wanted to make sure the files we safe before I tried anything. Any suggestions?  Thanks in advance.

---

### Post by Rogue Yun on 2008-05-19
I'm not one to bump threads, but there are some new circumstances.  It seems reinstalling Ubuntu isn't working either.  So now I'm left to try to salvage the files from the drive I would do that, but....

I can't figure out how to change the permissions.  I'll be monitoring this thread for the next 30 minutes.  Please let me know if you have any suggestions.  Thank you in advance.

An interesting note.  I put in the warty warthog live cd (yes I still keep it around) and I was able to access all the files that I couldn't before because of permissions.  However, it seems as though I didn't have my  permissions on my Fat32 110.00 Gigabyte hard drive set right.  Though I can access it fine and create new folders while using the ubuntu 8.04 desktop cd.  Go figure (only if you want to though).

---

### Post by SIXAXIS on 2008-05-19
Do it in Terminal:

```
sudo cp <original file location> <new file location>
```

---

### Post by Rogue Yun on 2008-05-19
I apologize if I did it incorrectly.  I get this:
ubuntu@ubuntu:~$ sudo cp /media/disk-1/craig/Desktop /media/disk
cp: omitting directory `/media/disk-1/craig/Desktop'

---

### Post by shadow-of-sin on 2008-05-19
should be::
```
sudo cp -r <original file location> <new file location>
```

---

### Post by Rogue Yun on 2008-05-19
Yep that worked great.  Thank you very very much.

---

### Post by k28 on 2010-02-11
Hi,

first of all im a noob in ubuntu. i want to do the same as the Threadstarter.

I want to copy this folders(Black DOT):

[[IMG]http://img292.yukle.tc/thumbs/2121Screenshot.jpg[/IMG]]("http://img292.yukle.tc/image.php?id=2121Screenshot.jpg")

To this Harddisk:

_[IMG]http://img100.imageshack.us/img100/4082/screenshot2o.png[/IMG]_

I tryt this:

sudo cp -r home/k28/desktop/7 /82 GB Filesystem


but it wont work. Can somebodz help me please? :)

---

### Post by switch10 on 2010-02-11
> **k28 said:**
> Hi,

first of all im a noob in ubuntu. i want to do the same as the Threadstarter.

I want to copy this folders(Black DOT):

[[IMG]http://img292.yukle.tc/thumbs/2121Screenshot.jpg[/IMG]]("http://img292.yukle.tc/image.php?id=2121Screenshot.jpg")

To this Harddisk:

_[IMG]http://img100.imageshack.us/img100/4082/screenshot2o.png[/IMG]_

I tryt this:

sudo cp -r home/k28/desktop/7 /82 GB Filesystem


but it wont work. Can somebodz help me please? :)


First of all Linux is case sensitive, so desktop and Desktop are 2 different things.

Second, no spaces are allowed.

Third, that target destination does not exist.  It would be in /media something like sdb1 if it is an external hard drive or something.  I would look in /media and find out what the name is.

so do this 

```
 sudo cp -r home/k28/Desktop/7/ /media/sdxx 
```

where sdxx is the location of the disk you want to move the file to.

---

### Post by k28 on 2010-02-11
Thx for your help. It dident work :(

I get following error:

/home/k28.....
no such file or directory

Maybe you need this Informations:

The HDD where 7, neuer ordner etc. is, is the harddrive where the crached Ubuntu is installed.

The HDD where i want to copy these folders are a sata drive what i plugged in just for copying this files onto.

Im using Ubuntu 9.10 as live disc.

Sry for my english.

---

### Post by switch10 on 2010-02-11
ok if you are on a live cd you will be looking in the home directory of the live cd, not what you want.

why dont you do:

```
 nautilus /media/ 
```

and give me a screen shot.  look in these directories, they should look familiar to you.  Tell me which sdxx you want to copy from, and which sdxx you want to copy to.  

You could also just copy these directories using drag and drop with the GUI. it might be easier for you.

---

### Post by k28 on 2010-02-13
Hi,

now i get this error and the media folder pops up

[[IMG]http://img299.yukle.tc/thumbs/7540Bildschirmfoto2.jpg[/IMG]](http://img299.yukle.tc/image.php?id=7540Bildschirmfoto2.jpg)

---

