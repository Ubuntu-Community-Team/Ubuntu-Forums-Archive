---
title: "Ubuntu on Another Non-Working Computer?"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by typomania on 2012-04-16
Hi! :) First just want to apologize now, because I'm kind of a noob at this and have no idea as to what I am doing but the matter's a bit urgent.

My computer has just been messed up all day. Long story short (and it is quite the story), I've been trying to access it through Ubuntu as someone suggested to someone else so I can get my files off the laptop and then reset to factory settings. The problem is, I THINK my issue is different but I could be wrong. If I am, then please redirect me to a thread that has the answer/has been solved!

Mostly, it's my being clueless as to how to mount Ubuntu onto a disk. This is because right now I'm typing on a Windows Vista desktop, and the computer that needs it is a Windows 7. How exactly would this work? When I tried to get it on disk, I couldn't exactly understand if it would work on the Windows 7 one, since the filing would be different and the mounting process is also different. So please explain!

---

### Post by mikewhatever on 2012-04-16
Hi, and welcome to the forums,

to copy data off an HDD, you'll need and an Ubuntu CD/DVD/USB. Multiplatform instructions on how to make a CD/DVD/USB can be found [-->here<--]("http://www.ubuntu.com/download/ubuntu/download").

Once made, it should work on any computer with supported hardware, regardless of what operating systems are installed on the HDD.

---

### Post by Curtis6767 on 2012-04-16
You might want to read through this: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Just some tips on how to download and then install Ubuntu

---

### Post by JC Cheloven on 2012-04-16
> **Curtis6767 said:**
> You might want to read through this: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Just some tips on how to download and then install Ubuntu

It's not like he/she wants to install ubuntu. Don't put pressure on him :D

@typomania: the advice given by mikewhatever is correct (of course). Only, as you didn't it before, you may need some clarification:

- You have first to make a bootable live cd of ubuntu (or a live usb...).
- You'll put the cd in the tray, turn on the computer, hit the key to access the bios (may be F12, F8, or something).
- In the bios, you'll tell the pc to boot from the cd.
- You'll be presented with a fully functional ubuntu desktop. You'll open the file browser, access your windows partition, and eventually copy your data to another external media (usb hard disk...)

Hope that  helps
JC

---

### Post by mikewhatever on 2012-04-16
> **Curtis6767 said:**
> You might want to read through this: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Just some tips on how to download and then install Ubuntu

It doesn't seem like the OP wants to install Ubuntu; just wants to rescue some data.

---

### Post by Curtis6767 on 2012-04-16
> **JC Cheloven said:**
> It's not like he/she wants to install ubuntu. Don't put pressure on him :DJC

Interesting response.

---

### Post by daslinkard on 2012-04-16
My first question would be what is going on with the Win 7 pc that you would be unable to access files?  Have you tried logging into safe mode to recover your files?  What efforts have you placed in recovering the files through the system?  I understand the user is wanting to utilize Ubuntu to get the data off, but if he/she is having issues running Ubuntu why not see if we can make this easy for them simply utilizing safe mode for Windows?

---

### Post by typomania on 2012-04-17
Thank you everyone for the quick response. It was quite important, so I do appreciate it.

daslinkard, I'm not exactly sure. It just began to spaz the other day; first it said my password to log in to Windows was wrong, and that's completely off because no one touches my laptop/knows the password to begin with It's been the same since the day I recieved my laptop and put it on there. I'm pretty sure it began after a Windows Update. Because it was perfectly fine before that, then overnight did the update (of course the updates happen when you aren't there to confirm it for yourself), and it was all messed up after that. It began this loop, rebooting and having it unable for me to acess the desktop or even log in screen then. Finally, I recieved advice to set it to where it doesn't refoot on error. I did that, but then it STILL rebooted. I was just completely confused until someone told me Ubuntu could get the files off, and then I could reset to factory settings.

And yes, I have attempted safe mode. All of them (the three options), but it did nothing. The first time I thought it worked until it still rebooted continuially with no stopping except for the black screen and the mouse there, that usually indicts the log in screen is about to open up. But in this case, it never does/did, and would reboot again. Aside from safe mode, I have tried a few other suggestions but I hadn't dare to take the harddrive out and put it in another computer to see if that would work. We only have two working computers in this household, so I'm pretty sure I'd be screwed if I began messing with the other working one, haha. Not to mention an angry family at my heels. But, yes. As for safe mode, I cannot get to it at all still.

---

### Post by Mark Phelps on 2012-04-17
typomania: Sorry you're having so much trouble, but if you're really interested in recovering the use of the Win7 box, you should go to a Win7 forum for advice -- recommend sevenforums.com.

They have help sections and tutorials -- and may be able to get it working for you again.

If they can't, you can always use an Ubuntu CD to rescue your data.

---

### Post by daslinkard on 2012-04-17
@typomania,

1st and most important....it sounds like you have a corrupted Windows in which it is continuously rebooting.  Personally you have a couple of options here.  The first would be to get the Live distro cd from the Ubuntu web site.

If you are having trouble actually downloading the CD, try this [site]("http://www.ubuntu.com/download/ubuntu/download"). Once you get Ubuntu on a Live CD, you will then set your PC to boot up via the CD Drive.  If you are unfamiliar with this you will probably be able to hit F12 to get into the boot menu.  You will select your CD drive (with CD in the drive).

At this point in time your computer is going to restart but be ready to press any key to boot from the CD.  This should get you into Ubuntu as you will select Try Ubuntu.

Once you are finally into the system you should be able to access your files.

If doing all of this is not possible, you will then need to get a Hard Drive enclosure for your computer.  Next you will need to take out your Hard Drive, placing it in the enclosure and connecting it up to another PC.  From there you will select the C: drive, go to User folder, and you will see your account with Documents, Pictures, Movies, Music, etc.

When it comes time to do a complete system restore on your computer (through windows) you should be able to tap F8 (like you were logging into safe mode) and select "Repair Your Computer".  This should walk you through doing a complete OS install of your PC.

Let me know what questions my ramblings brought forth for you.

---

