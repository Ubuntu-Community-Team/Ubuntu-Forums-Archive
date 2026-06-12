---
title: "Trouble installing ubuntu on a real old computer"
date: 2017-11-30
forum: New to Ubuntu
---

### Post by jay-hey on 2017-11-30
Hi there, 

I've recently decided to install Ubuntu on a really old computer I had lying around. I'm talking 80GB, 2GB RAM, 128MB graphics card and so on.

I've stumbled on an error upon booting from DVD called:
```
This kernel requires an x86-64 CPU, but only detected an i686 CPU. 
Unable to boot - please use a kernel appropriate for your CPU.
```

I've looked around and [found this thread on askubuntu]("https://askubuntu.com/questions/128657/kernel-requires-an-x86-64-cpu-but-only-detected-an-i686-cpu-how-can-i-install"), however, it seems that my CPU doesn't support virtualization.

Is there any way I can install Ubuntu onto this computer and bypass this error?

Additional information: I have it running Lubuntu right now and it seems to work well. I wanted Ubuntu LTS because Lubuntu doesn't seem to have the VMWare View Client that I need for work.

My thanks for your attention.

---

### Post by jaweewo on 2017-11-30
it says that you're cpu its 32 bits and you are trying to install 64 bits kernel on it.
Try this iso --> [http://releases.ubuntu.com/16.04/ubuntu-16.04.3-desktop-i386.iso.torrent](http://releases.ubuntu.com/16.04/ubuntu-16.04.3-desktop-i386.iso.torrent)

---

### Post by leunam12 on 2017-11-30
You need a 32bit iso as jaweewo stated; also if you see any PAE related errors with the 32bit version refer to the link below:

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by jay-hey on 2017-11-30
It's installing now. My thanks to both of you.

---

### Post by spronkc on 2017-12-10
Worked for me also.  Thanks to both.

---

### Post by spronkc on 2017-12-15
I installed 32 bit ubuntu 16.04.  Not happy, as I could not do Skype which is now only works with 64 bit.

I did some more research and found a way to install Ubuntu 17.10, 64-bit.  I unfortunately cannot find the details on how I did it. 

I went to computer BIOS to choose the USB to be the boot device. I only remember that when I tried to install the USB drive, the screen with a black background requested an input after a line that said something like Boot_:  I entered the four letters

live

This seemed to be accepted.

I had to do this twice.  There was considerable waiting for some periods where nothing seemed to happen, but eventually I got a screen that give me an icon to start the install process.

Be patient and good luck.

I am very happy now, as Ubuntu 17 works perfectly now and I love its new features.  Not missing Unity.

---

