---
title: "[SOLVED] Internal webcam not working"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by heddleston on 2008-07-05
i've already installed cheese, and it actually had been working previously, but not today. i ran lsusb & got this: Bus 007 Device 005: ID 05a9:7670 OmniVision Technologies, Inc. 


any ideas?

---

### Post by KIAaze on 2008-07-05
Your webcam should be supported out of the box apparently:
[http://www.wains.be/index.php/2008/01/21/ubuntu-on-dell-xps-m1330/](http://www.wains.be/index.php/2008/01/21/ubuntu-on-dell-xps-m1330/)
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

```
Dell XPS m1330 VGA Webcam
7.10 05a9:7670 uvcvideo
	
Skype 2.0.0.68 : Works out of the box, but Compiz must be turned off due to Intel X3100 video card 

```

It uses the uvcvideo driver.

You're saying it worked before. What did you change since then? Any system updates?
Do you have an Intel X3100 video card?

Before trying to install the uvcvideo yourself, try using the easycam tool as recommended in the Ubuntu wiki:
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

If this doesn't work, you can try installing the uvcvideo driver from source:
You will need the linux kernel headers:
```
sudo apt-get install linux-headers-$(uname -r)
```
Then it's just:
```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
make
make install

```

---

### Post by yeehi on 2010-05-08
I tried this, to get my webcam to go:

> svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
make
make install


I needed to install subversion first:

```
sudo apt-get install subversion

```

When I got as far as the first make command, I received the following error message:

make: *** No targets specified and no makefile found. Stop.

I tried proceeding anyway with make install and got:

make: *** No rule to make target `install'. Stop.



What should I do? 

Thank you!

---

### Post by KIAaze on 2010-05-09
This is pretty old. :rolleyes:
You could try to PM the original poster since he apparently solved the problem.

"make" will only work in a directory containing a file called "Makefile", "makefile" or "GNUmakefile".
So actually, you should have changed into the trunk directory first:
```
cd trunk
make

```

I just tried and it told me:
> -------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------


According to [http://www.ideasonboard.org/uvc/#download](http://www.ideasonboard.org/uvc/#download) :
> Linux 2.6.26 and newer includes the Linux UVC driver natively. You will not need to download the driver sources manually unless you want to test a newer version or help with development.


So you shouldn't need to compile from source anymore.
If it still doesn't work, try following the instructions [here]("http://www.ideasonboard.org/uvc/#download").

---

