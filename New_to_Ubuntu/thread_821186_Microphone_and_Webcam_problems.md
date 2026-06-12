---
title: "Microphone and Webcam problems"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-06-06
I have a Sony PS2 eyetoy and also a Logitech USB microphone. I installed some stuff and my Sony PS2 eyetoy is recognized and shows video with some installed applications like XAWTV. I plugged in my USB mic and went to sound recorder and there was no sound. I went to System, Preferences, and then Sound and was kind of lost to as what to select. I went to [http://stickam.com/](http://stickam.com/) which is a webcam site and Adobe flash player seems to not recognize my webcam or microphone. I was curious what I should do for it to recognize them and to get my microphone working, thanks.

---

### Post by ImThatNerd on 2008-06-07
I just installed Adobe for Linux x86, although I didn't think I had x86 machine. Anyways I am still having the same problem.

---

### Post by steve101101 on 2008-06-07
> **ImThatNerd said:**
> I just installed Adobe for Linux x86, although I didn't think I had x86 machine. Anyways I am still having the same problem.

I am not sure exactly how to fix your problem, but you don't just want to install any old software, especially if it is for a different architecture. 

If you havent already type 

```

lsusb

```

---

### Post by ImThatNerd on 2008-06-07
This is what it says

```
ryan@ryan-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 046d:0a01 Logitech, Inc. Logitech USB Headset
Bus 003 Device 003: ID 054c:0155 Sony Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 003: ID 1668:6010 Actiontec Electronics, Inc. [hex] 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ryan@ryan-desktop:~$ 





```

Now what?

---

### Post by ImThatNerd on 2008-06-07
Anyone?

---

### Post by ImThatNerd on 2008-06-13
5 day bump. :)

---

### Post by cariboo on 2008-06-13
Did you right click on the speaker icon and click Open Volume Control and make sure your microphone volume is not muted? X86 is just shorthand for 286,386,486,586 or Pentium 1, Pentium 2 etc.

Jim

---

### Post by ImThatNerd on 2008-06-13
> **cariboo907 said:**
> Did you right click on the speaker icon and click Open Volume Control and make sure your microphone volume is not muted? X86 is just shorthand for 286,386,486,586 or Pentium 1, Pentium 2 etc.

Jim

The volume for the microphone was up 3/4 of the way. I just really want to get the webcam to be recognized by flash since it has a microphone built in to it.

---

### Post by ImThatNerd on 2008-06-17
Anyone? This really is weird that no one knows the problem. I have no clue how to get it working.

---

### Post by loell on 2008-06-18
<whisper>



plug the webcam, and type ```
lsmod | grep  ov51x 
```


do tell the output..


</whisper>

---

### Post by ImThatNerd on 2008-06-23
> **loell said:**
> <whisper>



plug the webcam, and type ```
lsmod | grep  ov51x 
```


do tell the output..


</whisper>

Sorry for the late response, I was on vacation. I put that in and nothing happened:

```
ryan@ryan-desktop:~$ lsmod | grep  ov51x
ryan@ryan-desktop:~$ 

```

---

### Post by loell on 2008-06-23
i see, so no output, i guess you'll have to compile th driver :(

[http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz]("http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz")

---

### Post by ImThatNerd on 2008-06-24
> **loell said:**
> i see, so no output, i guess you'll have to compile th driver :(

[http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz]("http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz")

I downloaded that file, but I was wondering if you can give me a walk through so I do not mess up. I really want this to work and for flash to recognize my mic and web cam.

Edit: I followed that sites installation instructions on their wiki page. I didn't do the '  Force a parameter at load ' should I? I didn't know how I could edit and save since I don't have the permissions and know I have to access it in root. 

So after I did everything, still no luck.

---

### Post by loell on 2008-06-24
ok ;)

so i built a package to save you the trouble of compiling to just test if this even works or not :)

so here it is (download and install)

[ATTACH]75243[/ATTACH]

---

### Post by ImThatNerd on 2008-06-25
> **loell said:**
> ok ;)

so i built a package to save you the trouble of compiling to just test if this even works or not :)

so here it is (download and install)

[ATTACH]75243[/ATTACH]

Still doesn't work. Ubuntu recognizes it, but on websites like stickam.com and other websites that use flash for their webcams it doesn't work on when I right click and hit settings it has my camera selected but just a black image.

---

### Post by loell on 2008-06-25
what do you mean by **ubuntu recognizes it?** do you mean that it works with some webcam applications can you see images?

if indeed ubuntu recognizes it and the flash based webcam applications doesn't, its probably a v4l2 based webcam. you'll need **flashcam** to use it :(

---

### Post by ImThatNerd on 2008-06-25
Yeah Ubuntu applications recognize it. What is flashcam, I cannot find much about it.

---

### Post by loell on 2008-06-25
> **ImThatNerd said:**
> Yeah Ubuntu applications recognize it. What is flashcam, I cannot find much about it.

so the driver that you just installed is working now? and that you can actually use it? 

download this
[ATTACH]75254[/ATTACH]

and then extract it, in the terminal navigate it to where you extracted it

then type

```
sudo make install
```

---

### Post by ImThatNerd on 2008-06-25
> **loell said:**
> so the driver that you just installed is working now? and that you can actually use it? 

download this
[ATTACH]75254[/ATTACH]

and then extract it, in the terminal navigate it to where you extracted it

then type

```
sudo make install
```

Hmm:

```
ryan@ryan-desktop:~$ cd /home/ryan/flashcam-1.1
ryan@ryan-desktop:~/flashcam-1.1$ make install
install -d /usr/local/flashcam
install: cannot change permissions of `/usr/local/flashcam': No such file or directory
make: *** [install] Error 1
ryan@ryan-desktop:~/flashcam-1.1$ 

```

---

### Post by cariboo on 2008-06-25
You have forgot sudo.

Jim

---

### Post by ImThatNerd on 2008-06-25
I swear I could not see that earlier. XD

```
ryan@ryan-desktop:~$ cd /home/ryan/flashcam-1.1
ryan@ryan-desktop:~/flashcam-1.1$ sudo make install
[sudo] password for ryan: 
install -d /usr/local/flashcam
install -d /usr/local/flashcam/bin
ln -s /usr/local/bin/flashcamwrap /usr/local/flashcam/bin/firefox
ln -s /usr/local/bin/flashcamwrap /usr/local/flashcam/bin/flashplayer
install -m 755 flashcamhook.so /usr/local/flashcam
install -m 755 flashcam flashcamwrap /usr/local/bin
install -m 755 fcinit /etc/init.d
(cd vloopback-1.1.2; make install);
make[1]: Entering directory `/home/ryan/flashcam-1.1/vloopback-1.1.2'
install -d /lib/modules/2.6.24-19-generic/kernel/drivers/misc
install -m 644 -c vloopback.ko /lib/modules/2.6.24-19-generic/kernel/drivers/misc
/sbin/depmod -a
make[1]: Leaving directory `/home/ryan/flashcam-1.1/vloopback-1.1.2'
if [ -x /sbin/chkconfig ]; then chkconfig --add fcinit; fi
if [ -x /usr/sbin/update-rc.d ]; then update-rc.d fcinit start 98 3 4 5 . stop 10 0 1 2 6 .; fi
 Adding system startup for /etc/init.d/fcinit ...
   /etc/rc0.d/K10fcinit -> ../init.d/fcinit
   /etc/rc1.d/K10fcinit -> ../init.d/fcinit
   /etc/rc2.d/K10fcinit -> ../init.d/fcinit
   /etc/rc6.d/K10fcinit -> ../init.d/fcinit
   /etc/rc3.d/S98fcinit -> ../init.d/fcinit
   /etc/rc4.d/S98fcinit -> ../init.d/fcinit
   /etc/rc5.d/S98fcinit -> ../init.d/fcinit
ryan@ryan-desktop:~/flashcam-1.1$ 
ryan@ryan-desktop:~/flashcam-1.1$ 

```

It looks like it went well in terminal, but still no luck on it displaying on websites.

---

### Post by loell on 2008-06-25
sorry i did intended not to give the whole instruction, so as not to overload you with information, but anyway..

from [http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")


the next step is 

in the terminal
```
sudo flashcam -L 
```

what's the output?

---

### Post by ImThatNerd on 2008-06-25
```
ryan@ryan-desktop:~$ sudo flashcam -L
[sudo] password for ryan: 
Scanning devices
------
------
No V4L2 capture devices found.
ryan@ryan-desktop:~$ sudo flashcam -L
Scanning devices
------
------
No V4L2 capture devices found.
ryan@ryan-desktop:~$ 

```

This sucks. :(

---

### Post by loell on 2008-06-25
can you

```
lsmod | grep ov
```

again?



if you're already giving up then I can understand, these things are usually not for beginners.

---

### Post by ImThatNerd on 2008-06-26
I am not giving up I am just getting really frustrated. I got my mic working on Skype, but haven't tried other programs so that is fine. My webcam I see some people have gotten working but no instructions. I just really want it to get working.

This is the output:

```
ryan@ryan-desktop:~$ lsmod | grep ov
ov51x_jpeg            156120  0 
videodev               29440  1 ov51x_jpeg
usbcore               146028  12 usb_storage,libusual,ov51x_jpeg,snd_usb_audio,snd_usb_lib,rndis_host,cdc_ether,usbnet,usbhid,ehci_hcd,uhci_hcd
ryan@ryan-desktop:~$ 


```

---

### Post by loell on 2008-06-26
looking at the output , your system is now using the driver you installed!

ahah!!

found it. :D

while your webcam is supposed working now looking at the output, it won't specifically work with skype you need

a specific patch to make it to work with skype

[http://ubuntuforums.org/showthread.php?t=690666]("http://ubuntuforums.org/showthread.php?t=690666")


____ EDIT___

oh bad news, :( with the last post of the thread indicates :(

---

### Post by ImThatNerd on 2008-06-26
Well I did it anyways since there is nothing else for me to do. Before skype recognized my camera by the name, now it doesn't, so I am just going to stop with this since Ubuntu obviously has some trouble with it.

---

### Post by loell on 2008-06-26
yeah, but try not to ditch this webcam, it may  work the next ubuntu release. :)

---

