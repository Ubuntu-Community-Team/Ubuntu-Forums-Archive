---
title: "Ubuntu Live wont run"
date: 2019-06-12
forum: New to Ubuntu
---

### Post by mikeybinec on 2019-06-12
OK, so my PC machine, I think the hard drive died. I wanted to make sure the bsod's weren't from a bad vid card. So I have a couple of live CDs--an old Ubu and a Puppy- both about 8 years old

So I tried the Ubu first and then the Puppy 2nd and this is the image I get:  It's hung up on "disconnecting USB' and it increments up higher and higher

[IMG]https://i.postimg.cc/jqcp9frV/usb.jpg[/IMG]

So, I;m thinking this is because I had an old Ubu and Puppy, but aftter downloading the latest and greatest, I still get this
same image. Now, if I hit escape,  I can get to this image:

[IMG]https://i.postimg.cc/Y00bTh1k/ubuntu-ok.jpg[/IMG]


So after awhile, it returns to the "USB DISCONNECT" garbage that goes on and on and on.

So anybody have a comment on whats going on? 

thanks

---

### Post by oldfred on 2019-06-12
What brand/model system?
What video card/chip?
Do you have other USB cards plugged in? That may be causing issues.

It also says you have unclean Windows partition. That may be from hibernation flag is still set usually from fast start up if Windows 8 or 10, or it needs chkdsk using your Windows repair disk.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by mikeybinec on 2019-06-13
[QUOTE=oldfred;13865951]What brand/model system?  
What video card/chip?
Do you have other USB cards plugged in? That may be causing issues.

It also says you have unclean Windows partition. That may be from hibernation flag is still set usually from fast start up if Windows 8 or 10, or it needs chkdsk using your Windows repair disk.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates

Thanks for answering!!

 system is just a clone with an ASUS motherboard- Win 7 Pro 32 bit with 2 gig RAM. Vid card is a low end ZOLTAC.

Yes, there is a USB wireless NIC--it is my internet connection

Yeah, I did notice that windows partition message. But the HD is 9 years old, so it was expected. The reason I ran the live CD was to verify the vid card was still good-its
only 6 months old

Looking at the log output from Ubu, it correctly identified the manufacturer, but I would think it Ubu should be able to handle a wireless NIC

I appreciate your time

regards

---

### Post by oldfred on 2019-06-13
So is real issue your USB NIC?

I can move thread to Networking & Wireless sub-forum.
See Sticky on before you post and run the suggested script.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

---

