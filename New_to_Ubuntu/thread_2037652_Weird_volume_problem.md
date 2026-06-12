---
title: "Weird volume problem"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by cjennn on 2012-08-05
Hi! This is a computer numpty speaking here.... (but one who loves the idea of linux and has been running it for several years). 

From today I have a weird 'volume bar' flashing on and off on the top right of my screen. When I manually turn down the volume, it automatically turns the volume back up again! Clicking on it with left or right buttons does nothing. It also interferes with the running speed of my computer. Seems like a virus or something to me....  

The version of linux was uploaded a couple of months ago, I forgot what version it's called! 

Any ideas?

I have been working on a word file on a windows computer and my computer alternatively via usb. I'm in Indonesia, some sort of weird Indonesian windows virus playing around in my linux?? Hmmmm. 

Thanks!

---

### Post by Gone fishing on 2012-08-05
Is this a laptop? is the volume controlled by keys or buttons on the laptop? are they stuck down?

Just thought I’d start with the obvious.

---

### Post by cjennn on 2012-08-06
Thanks! Yes it is a laptop. 

Normally, the volume is controlled by a little speaker icon I click on with the mouse in the top right. 

No I don't think keys are stuck down. 

This problem is involves an entirely new volume bar that has appeared in the last day or two, flickers about on my screen, turns the volume up all by itself, slows down the running speed of my computer when it is there, and when I click on it (left or right mouse button), nothing happens! 

It's not there all the time, just randomly! 

Thanks for help! 

Jen

---

### Post by audiomick on 2012-08-06
Three things:

Firstly, a windows virus is not going to affect your Linux install. In the same way that a windows program won't run on Linux, a virus can't either.

Secondly, one way of checking to see what version of Ubuntu you have is to open the system monitor and look on the first tab. If the version you have is only a couple of months old and a standard Ubuntu, you probably have the Unity desktop. Type "system monitor" in the search box in the dash to find the program.

Thirdly what I would do is to find out what the applet is that controls the volume and remove it and re-install it. If there is no mechanical fault like a stuck down button or something, then it seems likely to me that the applet has a problem. The symptoms you describe sound like the applet thinks it is getting instructions to turn up the volume. That bar appears when every thing is working right when you change the volume using keys on the keyboard.

Bear in mind that even if a key is not physically stuck down, it may be sending false signals due to a fault. Do you have a second OS installed on that computer  to see if the problem, or one that might be related, appears there? Are you able to boot into the Ubuntu live  CD and see if the problem shows up there?

---

### Post by cjennn on 2012-08-08
Thanks for your answer Michael, 

the problem seems to have gone away itself for today... 

If it comes back I will try some of those things. 
Hmmm, so I have version 11.1. 
I'll try un and reinstalling the volume ap ( i guess by typing 
volume' into the 'software centre' to see what turns up.)
OS means operating system right? I used to have windows vista, but that crashed and no longer works. 
Not sure what the Ubuntu live CD is. 
Hopefully the problem has gone away though, 
thanks again!!!

---

### Post by audiomick on 2012-08-08
> **cjennn said:**
> 
the problem seems to have gone away itself for today... 

I'll try un and reinstalling the volume ap ( i guess by typing 
volume' into the 'software centre' to see what turns up.)


If the problem has gone away, maybe it will stay away. Watch it for a while and see.

I just had a look at my 11.10 install (incidentally, it is 11.10 because it came out in October, the tenth month, in 2011, so it needs the last zero in the name. ). I think the suggestion to uninstall and reinstall may be was not so brilliant. I couldn't find the volume thing in the software centre. The function used to be done by a thing that was called something like "gnome panel notifier". That was something that could be removed and re-installed (and needed to be occasionally when it was playing up).

I have the impression that the volume control thing has become and integral part of the unity panel. I don't know for sure, but maybe it can't be re-installed alone anymore.

> OS means operating system right? I used to have windows vista, but that crashed and no longer works. 
Not sure what the Ubuntu live CD is. 

Yes, OS is operating system. The live CD is the CD (or usb stick) that you installed from. The Live environment is when you use the "try without installing" option from the menu on the CD. It is a good way to check if you have a hardware or a software problem. If the problem is still there when you are booted into the live environment or another OS, then it is likely to be hardware (or maybe BIOS) related. If you are only getting the problem in one install and not in the live environment or when booted into another OS on the same machine, then that install has probably got a problem.

Anyway, watch it for a while and see if it behaves. I might have just been having a bad day. I have to say, on thinking about it after having posted, I tend to think that there was some strangeness happening with your keyboard or something, i.e. more of a hardware problem that a software one. But that is just a guess.

---

### Post by cjennn on 2012-08-08
Thanks again for all your suggestions - this supportive community really renews my faith in ubuntu, even though I am not very good at computers! 

Yep, the problem is back today. And quite annoying because I stops the computer doing anything whilst it is flashing on and off. 

I'm looking for the volume control on the keyboard just to make sure it's not a hardware problem. It seems to change the volume you need to press Fn at the same time as F11 or F12, so I don't think both keys are being stuck down at the same time. (They are not even sticky keys). 

I'm pretty sure I downloaded Ubuntu from the net, not off a CD (a friend did it for me). 

Hmm, a weird one. I could try upgrading ubuntu when it is available and see if it goes away?

---

### Post by audiomick on 2012-08-09
> **cjennn said:**
> I'm pretty sure I downloaded Ubuntu from the net, not off a CD (a friend did it for me).

Yes, it would have been downloaded from the net, but it would then have been put on a CD or a USB stick. That is the only way to install Ubuntu.

If you can't find the medium you used to install, you might want to make a new one. I always keep at least one USB installer around in case my computer decides not to boot and I need to get at something that is on there. 

Here is how to make a USB installer
[https://help.ubuntu.com/community/Installation/FromUSBStick/]("https://help.ubuntu.com/community/Installation/FromUSBStick/")


and you can download from the Ubuntu home page.
[http://www.ubuntu.com/]("http://www.ubuntu.com/")

If you did this, you would actually kill two birds with one stone, sort of. You said you are using 11.10, didn't you? If you want to be really thorough, you could find and iso for 11.10, make an installer of that and boot into that to see if your install is corrupted somehow, but that is a lot of effort. If you use the current 12.04 version, then you will see at the same time if your problem is related to your install (software problem) or not (a problem, probably hardware, maybe bios, with the machine itself). You would also see if your machine runs happily on the newer version of Ubuntu, which will tell you if you can upgrade without any worries.

---

