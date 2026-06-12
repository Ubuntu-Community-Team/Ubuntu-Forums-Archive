---
title: "Official Ubuntu HCL?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Tomist on 2008-11-27
Hello.

I am trying to make the switch from Windows to Ubuntu, but after hours of working to install Ubuntu, I finally came to a conclusion that all of my laptops hate Ubuntu. Go figure. Anyway, sooner or later I would like to buy a working laptop that can run Ubuntu and I was wondering if there was an "official" Ubuntu HCL. If so, awesome. If not, are there any "unofficial" Ubuntu HCLs that are any good?

Thanks! :)

---

### Post by Olivier2371 on 2008-11-27
Hello there,

Try this link.

[http://ubuntuforums.org/showthread.php?t=361236]("http://ubuntuforums.org/showthread.php?t=361236")

Hope this helps.

What's your system specs.

---

### Post by ByteJuggler on 2008-11-27
What exact models of laptops do you have (+specs) and what do they all do when you try to install Ubuntu on them?  (Crashing behaviour is always something I'm keen to get reported so it can hopefully be fixed somewhere along the line...)

---

### Post by Tomist on 2008-11-27
Thanks.


It's a Compaq Presairo R3000. It has Windows on it but I have never been successful at getting it to go very far. The last people that owned it  (it was given to me) really ruined that XP install. Because of that, I was never able to get all the specs. All I know is that it has an Athlon 64 processor and a nVidia graphics thing. I'd give your more if I knew more.

When I try to install Ubuntu (8.04 btw) by going to the "Install" option, it gets to the pretty bird screan (I think it's the default desktop) and does nothing. When I try to "Run it without any change to your desktop" or whatever it says, it gets to the desktop, and freezes up, or I'll be able to do stuff, but when I click on the "Install" icon, it freezes.

---

### Post by slmouradian on 2008-11-27
this may be obvious, but did you

'Check for defects on cd'?

---

### Post by Tomist on 2008-11-27
Yep, I did. It sayed that it was ok. I also checked the MD5sum on my computer and it was ok too.

---

### Post by Olivier2371 on 2008-11-27
Hello there,

You can find the specs of your system there, just download the manual.

[http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=&cc=us&lang=&product=442915]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=&cc=us&lang=&product=442915")

Hope this is helpful.

---

### Post by ByteJuggler on 2008-11-27
> **Tomist said:**
> Thanks.
It's a Compaq Presairo R3000. It has Windows on it but I have never been successful at getting it to go very far. The last people that owned it  (it was given to me) really ruined that XP install. Because of that, I was never able to get all the specs. All I know is that it has an Athlon 64 processor and a nVidia graphics thing. I'd give your more if I knew more.

When I try to install Ubuntu (8.04 btw) by going to the "Install" option, it gets to the pretty bird screan (I think it's the default desktop) and does nothing. When I try to "Run it without any change to your desktop" or whatever it says, it gets to the desktop, and freezes up, or I'll be able to do stuff, but when I click on the "Install" icon, it freezes.

How much memory?   Hangs and freezes on the LiveCD might be RAM related on low memory systems (booting the LiveCD uses more RAM than normal due to booting the OS from CD into RAM.)  But I don't think the R3000 is that old or has that little memory.

Please do the following for me.  
0.) Boot the LiveCD, wait for it to get to the desktop.
1.) Press alt-f2.  A comman run box should open up.
2.) Enter (or better yet, copy and paste) the following command into space provided and press enter (or click Run):
```
gksudo lspci >/tmp/hw.txt; gedit /tmp/hw.txt
```
3.) Post the output which should've opened in a text editor back here.
4.) Next, press alt-f2 again, and enter/copy the following command:
```
free >/tmp/mem.txt; gedit /tmp/mem.txt
```
5.) Please post the output of that back here also.

You might want to try downloading the Alternate install CD which uses a text mode installer and is significantly lighter on resource usage.

---

### Post by Tomist on 2008-11-27
Thanks for the link.

The computer is:

Compaq Presairo R3000
ATI Radeon 9000 graphics
Broadcom 54G wireless
JBL Pro speakers
DVD and CDR/W combo drive
100 GB Hard drive
512 MB Memory (I think, no less that 512)

I'll post those once the desktop comes up. Thanks for all your help so far.

EDIT: Good lord. I got to it, started typing, and it crashed. :\

---

### Post by Olivier2371 on 2008-11-27
Tomist,

Are sure?

[http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/]("http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/")

The one I found could be an older model.

---

### Post by Tomist on 2008-11-27
I'm almost positive. The guy that gave it to me said 100 GB and 512 Memory. But then again, he could have been wrong.

I think that the laptop is just old and won't work with Ubuntu because of that.

EDIT: Ran the live cd again. I got this while booting. "Segmentation fault
run-parts: /etc/dbus-1/event.d/70system-tools-backend exited with return code 139"

I'm going to download the text installer.

---

### Post by ByteJuggler on 2008-11-27
> **Tomist said:**
> 
EDIT: Ran the live cd again. I got this while booting. "Segmentation fault
run-parts: /etc/dbus-1/event.d/70system-tools-backend exited with return code 139"


Hmmm... a segmentation fault is the equivalent of an "access violation" on Windows.  Usually that happens when there's a serious bug in a software program, and such a bug related crash is usually (although not always) repeatable in the same place.  But it's fairly unlikely that *that *piece of software would crash *there* with such a problem.  (If there was a problem there in the code, it would've been found long ago as everyone would've been getting it, and that's not the case, which implies there's likely another reason behind that seg-fault crash.)

The only other reason for segmentation faults are sometimes hardware issues of some sort.  E.g. dodgy memory or rarely CPU overheat.  In such a case often the seg-fault will not be exactly repeatable, so you'll find an app crashes one time, and not the next.  

So: Have you tried the memory test on the boot menu for a while at least to check your RAM?  (I somehow doubt it'll be CPU overheat, but you might want to consider whether that's plausible.)

---

### Post by jimreynold2nd on 2008-11-27
I have been working with several laptops and what I observed is that the ThinkPads are very linux-friendly. My installation of Ubuntu on a T22, a T42, a T60 and a T61 went very smoothly with everything automatically recognized. I have some minor problems with the T61: back-forward keys not working (but they work in openSuSE). Everything else is perfect, including bluetooth, media keys, Fn keys, hibernate-suspend, etc.

---

