---
title: "HOW TO: Fix Logitech QuickCam and GnomeMeeting"
date: 2005-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Remix_88 on 2005-04-08
This fix is derived from a couple of posts in various topics and may work for more than just Logitech QuickCams, but I can't validate that as I don't have any other brand of web cam.

_The Problem_

After a fresh install of Hoary, GnomeMeeting produced the following error when I tried to use the web cam. 

**Error while opening video device /dev/video0**

_The Fix_

```
$ sudo apt-get install libpt-pluins-v4l
```


Start GnomeMeeting and change the video plugin to 'v4l' in the GnomeMeeting Preferences (instead of 'v4l2') and set the channel to 0.

Your webcam should now be working.

---

### Post by Jesus Franco on 2005-04-08
"libpt-plugins-v4l"

AND THANK YOU! Now I can use my sisters quickcam as a security can while I'm at school. I tried to get it to work before and it didnt. NOW IT DOES!!!!!!   :-D

---

### Post by simbloke on 2005-04-09
More thanks! 

I thought it was going to be something to do with the pwc module. I'm using a Philips camera by the way.

---

### Post by vrunt on 2005-04-09
If you're using a Labtec QuickCam, you need to do the same thing.
But first you'll have to get the drivers.
I used [http://qce-ga.sourceforge.net](http://qce-ga.sourceforge.net)

---

### Post by Fab_nasty on 2005-04-17
Motherboard : P4P800-e-deluxe
CPU : P4 2.8Ghz HT
RAM : 1024 MO
Graphic Card : ATI Radeon 9800Pro
Sound card : integred sound card (Realtek ALC 850)
TV Card : PCTV Rave (can Use V4l2 and V4l)
Webcam : Quickcam 4000 Pro
i have done this but i have, my webcam freeze.  i have v4l plugin but it doesn't work, if i use gqcam, gnomemeeting ou camstream, it's the same they freeze when my webcam start. Who can help me?
I hope you understand well because english is not my natural language

---

### Post by Jesus Franco on 2005-04-22
type the following in a terminal window

$ sudo gedit /etc/X11/xorg.conf

after u type your password a window should pop up with your X-Org configuration.

look for a section that says
```
Section "Module"
``` 
Make sure you have the following listed under it.
```
Load     "v4l"
``` 
If not add it. Mines looks like this
```
Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection
``` 

Note: I am using a ati video card. Dont know what you need to do to a config with a nvidia card. Maybe its the same. Dont know  :| 

Hope that helps you

---

### Post by Fab_nasty on 2005-04-25
I have always the same probleme, i don't think it's v4l problem, i think my pctv and my webcam make conflict, because my pctv card can use v4l2 and v4l, but i don't know how i can solve it.

---

### Post by st0ic on 2005-04-30
[QUOTE=vrunt]If you're using a Labtec QuickCam, you need to do the same thing.
But first you'll have to get the drivers.
I used [http://qce-ga.sourceforge.net](http://qce-ga.sourceforge.net)[/QUOTE]

I get the following error when I run the make all, any help?

awk: cannot open /lib/modules/2.6.10-5-686/build/include/linux/version.h (No such file or directory)
/bin/sh: line 0: [: -ge: unary operator expected
/bin/sh: line 0: [: -ge: unary operator expected
cc -I/lib/modules/2.6.10-5-686/build/include -nostdinc -iwithprefix include -DMODULE -D__KERNEL__ -DNOKERNEL -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -Wall -Wstrict-prototypes -Wno-trigraphs  -pipe -c qc-driver.c
make: cc: Command not found
make: *** [qc-driver.o] Error 127

---

### Post by Wallilabou on 2005-05-02
[QUOTE=st0ic]I get the following error when I run the make all, any help?

awk: cannot open /lib/modules/2.6.10-5-686/build/include/linux/version.h (No such file or directory)
/bin/sh: line 0: [: -ge: unary operator expected
/bin/sh: line 0: [: -ge: unary operator expected
cc -I/lib/modules/2.6.10-5-686/build/include -nostdinc -iwithprefix include -DMODULE -D__KERNEL__ -DNOKERNEL -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -Wall -Wstrict-prototypes -Wno-trigraphs  -pipe -c qc-driver.c
make: cc: Command not found
make: *** [qc-driver.o] Error 127[/QUOTE]

Just finished installing this same driver.

It needs the kernel headers to compile.  Search for linux-headers-686 in synaptic.  Also, instead of running make directly, I used ./quickcam.sh which guides you through the process.  (Check the updated instructions in the README file.)
Hope this helps.

---

### Post by Sabator on 2005-05-17
[QUOTE=Wallilabou]Just finished installing this same driver.

It needs the kernel headers to compile.  Search for linux-headers-686 in synaptic.  Also, instead of running make directly, I used ./quickcam.sh which guides you through the process.  (Check the updated instructions in the README file.)
Hope this helps.[/QUOTE]
 When compiling the driver at [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/) I get lots of errors. After typing "make all", I got deluged with crap such as

qc-driver.c:2418: error: `EFAULT' undeclared (first use in this function)
qc-driver.c:2421: error: dereferencing pointer to incomplete type
qc-driver.c:2421: error: `ERESTARTSYS' undeclared (first use in this function)
qc-driver.c:2422: error: dereferencing pointer to incomplete type
qc-driver.c:2423: error: `ENODEV' undeclared (first use in this function)
qc-driver.c:2427: error: `EAGAIN' undeclared (first use in this function)
qc-driver.c:2436: warning: implicit declaration of function `copy_to_user'
qc-driver.c:2443: error: dereferencing pointer to incomplete type
qc-driver.c:2449:41: missing binary operator before token "("
qc-driver.c:2459:41: missing binary operator before token "("
qc-driver.c: In function `qc_v4l_mmap':
qc-driver.c:2464: error: dereferencing pointer to incomplete type
qc-driver.c:2467:51: missing binary operator before token "("

I probably screwed up somewhere. Anyone have any ideas?

---

### Post by geokker on 2005-06-24
I get a:

E: Couldn't find package libpt-pluins-v4l

Which repository is it in? I thought I had all of the biggies installed.

** IGNORE ME!**

found it.

 :---)

---

### Post by rwabel on 2005-07-09
[QUOTE=Remix_88]This fix is derived from a couple of posts in various topics and may work for more than just Logitech QuickCams, but I can't validate that as I don't have any other brand of web cam.

_The Problem_

After a fresh install of Hoary, GnomeMeeting produced the following error when I tried to use the web cam. 

**Error while opening video device /dev/video0**

_The Fix_

```
$ sudo apt-get install libpt-pluins-v4l
```


Start GnomeMeeting and change the video plugin to 'v4l' in the GnomeMeeting Preferences (instead of 'v4l2') and set the channel to 0.

Your webcam should now be working.[/QUOTE]
 Gqcam gives me that error: /dev/video: No such file or directory

I need to make a symlink from /dev/video0

why that? It's the opposite!

---

### Post by gratefulfrog on 2005-09-10
[QUOTE=Remix_88]This fix is derived from a couple of posts in various topics and may work for more than just Logitech QuickCams, but I can't validate that as I don't have any other brand of web cam.

_The Problem_

After a fresh install of Hoary, GnomeMeeting produced the following error when I tried to use the web cam. 

**Error while opening video device /dev/video0**

_The Fix_

```
$ sudo apt-get install libpt-pluins-v4l
```


Start GnomeMeeting and change the video plugin to 'v4l' in the GnomeMeeting Preferences (instead of 'v4l2') and set the channel to 0.

Your webcam should now be working.[/QUOTE]
 This is really usefull.  Could someone send it to the official howtos, or to the unofficial ubutuntu guide?

---

### Post by Raj on 2005-09-30
Hi guys,

I have followed the instructions in the thread and it updated the v4l library/codec (?). The thing is that when I ask gnomemeeting to autodetect my cam, it isnt finding it - says that there is no input device found.

BUT - in device manager it sees it as a Quickcam Express ??

Ideas??

Cheers

Raj

********** EDIT ************

I followed this guide [http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+quickcam](http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+quickcam) and it worked staright up. Thanks again for everyones help...

---

### Post by meirm on 2005-11-23
for those trying to install 
sudo apt-get install libpt-pluins-v4l

There is a typo and you should type

sudo apt-get install libpt-plugins-v4l

If you are looking for a package you could type

apt-cache search <package-partial-name>

for instance

apt-cache search libpt

---

### Post by arnieboy on 2005-12-10
trythe following howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

