---
title: "[SOLVED] Trying-out Ubuntu 8.04.1 Desktop from CD"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by GrenadierExercise on 2008-10-23
I am having some difficuly in trying-out Ubuntu from CD in advance of committing to a full install from the same CD.
The CD version is ubuntu-8.04.1-desktop-amd64.iso and has been checked OK by md5sum and by the check facility on the CD.
On trying to run from the CD ubuntu boots as far as the log-in screen but refuses to recognise any username or password as valid.  I understand that the username has to be in lower case format and the password any case alphanumeric format.
I have tried repeatedly to get the program to run from the CD without success.  I have even tried an alternative ubuntu version (i386) CD but with identical results.
I think I must be missing something very obvious and would welcome advice on how to run ubuntu from CD.
My desktop is a HP Compaq Presario model SR1519UK AMD64Athlon currently running MSoft XP Home.

---

### Post by Peter09 on 2008-10-23
I cannot remember off hand but I thought the username and password were displayed on the screen during the LiveCD start.

---

### Post by OldGrey on 2008-10-23
I have recently installed Ubuntu 64 bit from a live CD and when running from the CD it did not request a username and password, neither have other Ubuntu live CDs I have used. Which option did you select at the first screen?

---

### Post by Gausian on 2008-10-23
Yeah, ive never been asked for a password from any live cd before.  Where did you download the iso from?

---

### Post by C.S.Cameron on 2008-10-23
I think I've seen this before, just hitting enter at user name seemed to work, don't type anything.

---

### Post by GrenadierExercise on 2008-10-25
> **Peter09 said:**
> I cannot remember off hand but I thought the username and password were displayed on the screen during the LiveCD start.

I don't know why but my live CD is demanding username and password to try-out Ubuntu. I do not know how the "entry method" to "try-out" is structured in the start system so do not know what to expect.

---

### Post by philinux on 2008-10-25
Every livecd I've tried boots straight to the desktop. This behaviour is not normal.

Try ubuntu for the username and password.

---

### Post by GrenadierExercise on 2008-10-25
> **OldGrey said:**
> I have recently installed Ubuntu 64 bit from a live CD and when running from the CD it did not request a username and password, neither have other Ubuntu live CDs I have used. Which option did you select at the first screen?

I selected "Demo" when running CD in XP, then after reboot "English" language and "Trying Ubuntu without any change to your computer". After kernel loaded I end up being asked for username and password, none of which is accepted.  It implies to me that maybe default entries exist, but what??  I have tried all the obvious possibilities with no luck.

---

### Post by mikewhatever on 2008-10-25
> **GrenadierExercise said:**
> I selected "Demo" when running CD in XP, then after reboot "English" language and "Trying Ubuntu without any change to your computer". After kernel loaded I end up being asked for username and password, none of which is accepted.  It implies to me that maybe default entries exist, but what??  I have tried all the obvious possibilities with no luck.

Where did you get the iso from?

---

### Post by GrenadierExercise on 2008-10-25
> **Gausian said:**
> Yeah, ive never been asked for a password from any live cd before.  Where did you download the iso from?

I downloaded the CD from the Ubuntu mirror list. The mirror site used is the closest to me geographically - "Great Britain (UK) University of Kent UK Mirror Service".  The downloaded Cd was checked as recommended by Ubuntu and found OK.

---

### Post by GrenadierExercise on 2008-10-25
> **C.S.Cameron said:**
> I think I've seen this before, just hitting enter at user name seemed to work, don't type anything.

I have tried that with no result.

---

### Post by GrenadierExercise on 2008-10-25
> **philinux said:**
> Every livecd I've tried boots straight to the desktop. This behaviour is not normal.

Try ubuntu for the username and password.

I have tried "ubuntu" as username and password and get the response in red "Incorrect username or password.  Letters must be typed in the correct case".

---

### Post by GrenadierExercise on 2008-10-25
> **mikewhatever said:**
> Where did you get the iso from?

I downloaded the CD from the Ubuntu mirror list. The mirror site used is the closest to me geographically - "Great Britain (UK) University of Kent UK Mirror Service". The downloaded Cd was checked as recommended by Ubuntu and found OK.

---

### Post by mikewhatever on 2008-10-25
> **GrenadierExercise said:**
> I downloaded the CD from the Ubuntu mirror list. The mirror site used is the closest to me geographically - "Great Britain (UK) University of Kent UK Mirror Service". The downloaded Cd was checked as recommended by Ubuntu and found OK.

That password problem is extremely odd. As the previous posters, I can also confirm that Ubuntu live CDs shouldn't require neither usernames nor passwords.

---

### Post by GrenadierExercise on 2008-10-26
> **mikewhatever said:**
> That password problem is extremely odd. As the previous posters, I can also confirm that Ubuntu live CDs shouldn't require neither usernames nor passwords.
Thanks for your reply.  The consensus of replies seems to be that what I am experiencing regarding demand for username and password when running the live CD to try out Ubuntu should not happen.  The suspicion is that my desktop will not run Linux, ie hardware or bios problems.
How on earth do I track down the (hardware?) problem?

---

### Post by CatKiller on 2008-10-26
The usual method to try the Ubuntu live cd doesn't involve a Windows step at all. You can go into your BIOS (you generally have to press a key as your computer boots, which varies by motherboard manufacturer - Del is quite common, but it might be one of the F-keys) to set the boot order. Set your CD drive to boot before your hard drive, and if your Ubuntu cd is in the drive your computer will boot from that in preference to the hard drive.

You should then be able to select the first entry from the Ubuntu menu, and boot to the desktop without being asked for a password at all.

---

### Post by mikewhatever on 2008-10-26
> **GrenadierExercise said:**
> Thanks for your reply.  The consensus of replies seems to be that what I am experiencing regarding demand for username and password when running the live CD to try out Ubuntu should not happen.  The suspicion is that my desktop will not run Linux, ie hardware or bios problems.
How on earth do I track down the (hardware?) problem?

I don't see any sign of a hardware problem. If it boots and you get the login screen, it means the OS is nearly loaded, but why the login is beyond me.

---

### Post by Slug71 on 2008-10-26
I wouldn't install 8.04.1. 8.10 comes out in 4 days and the new Kernel it has is way better in terms of Hardware support than the Kernel in 8.04.1.

---

### Post by SunnyRabbiera on 2008-10-26
> **Slug71 said:**
> I wouldn't install 8.04.1. 8.10 comes out in 4 days and the new Kernel it has is way better in terms of Hardware support than the Kernel in 8.04.1.

for me the jump to ibex is not worth it.
I would just try it all again

---

### Post by JC Cheloven on 2008-10-26
> **GrenadierExercise said:**
> I selected "Demo" when running CD in XP, then after reboot "English" ...

The "xp" bit in your post is unclear, and seems to be odd one. Anyway, an Ubuntu live cd never asks for usr&pswd, to my knowledge.  Please, do as CatKiller said :
> 
CatKiller said: The usual method to try the Ubuntu live cd doesn't involve a Windows step at all. You can go into your BIOS (you generally have to press a key as your computer boots, which varies by motherboard manufacturer - Del is quite common, but it might be one of the F-keys) to set the boot order. Set your CD drive to boot before your hard drive, and if your Ubuntu cd is in the drive your computer will boot from that in preference to the hard drive.

You should then be able to select the first entry from the Ubuntu menu, and boot to the desktop without being asked for a password at all.

and tell us how it was. I'm pretty sure it will be alright ;-)

---

### Post by GrenadierExercise on 2008-10-27
> **CatKiller said:**
> The usual method to try the Ubuntu live cd doesn't involve a Windows step at all. You can go into your BIOS (you generally have to press a key as your computer boots, which varies by motherboard manufacturer - Del is quite common, but it might be one of the F-keys) to set the boot order. Set your CD drive to boot before your hard drive, and if your Ubuntu cd is in the drive your computer will boot from that in preference to the hard drive.

You should then be able to select the first entry from the Ubuntu menu, and boot to the desktop without being asked for a password at all.
I have checked BIOS boot settings and am indeed booting from CD first and not HD.  I keep getting login screen for username followed by password entry screen followed by refusal to accept inputed username or password.
I am becoming convinced that the problem lies in the PC as no one seems to have dificulty in trying out Ubuntu from CD.

---

### Post by lhr111 on 2008-10-27
I'm planning to do a dual boot XP/Ubuntu, but I've tried both the i386 iso as a cd (checked both image and burn)and an extracted form on a cd to check viability. neither work, when i restart to do the demo, I end up in a grub line that doesn't respond to suggested commands. I followed the directions listed here and at [http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236).

---

### Post by CatKiller on 2008-10-27
FWIW, I believe that the username is **ubuntu** and the password is blank - although I've not had to boot from the Live CD for quite some time. I can't imagine what's causing you to be asked, though.

---

### Post by GrenadierExercise on 2008-10-28
> **CatKiller said:**
> FWIW, I believe that the username is **ubuntu** and the password is blank - although I've not had to boot from the Live CD for quite some time. I can't imagine what's causing you to be asked, though.
I have tried ubuntu as username with blank password but with same result - refusal and cycled back to login screen again and again.  I am wondering if anyone with a similar desktop has had success at trying out Ubuntu from the downloaded CD and has successfully mounted Ubuntu 8.04.1.  (My desktop is a HP Compaq Presario AMD 64 Athlon 3200 with Phoenix Award BIOS v3.18)

---

### Post by CatKiller on 2008-10-29
> **GrenadierExercise said:**
> I have tried ubuntu as username with blank password but with same result - refusal and cycled back to login screen again and again.

I just checked my 8.04 cd (I don't have a later one) and the username/password is as I stated earlier. Are you using the 64-bit version? It might be significant information to someone.

To recap; you are definitely just booting from the cd - you aren't launching anything in Windows? You haven't used Wubi (the Windows application that lets you install Ubuntu within Windows)? You've not already set up a username and password - perhaps as part of that "Demo" step that you mentioned? It's definitely an Ubuntu login screen, rather than anything else (there will be a distinctly brown & orange theme - I've not used the default login screen for about two years, so I can't remember exactly what it looks like)?

... something I've just thought of: when you're at the login window, pressing Ctrl-Alt-F1 should take you to a black screen with white writing. At the bottom of this text, does it say ```
ubuntu@ubuntu
``` or does it say ```
ubuntu login:
```

---

### Post by jespdj on 2008-10-29
The screen where you are asked to enter a username and password, is that a text screen (black with light letters, nothing graphical) or do you see the graphical login screen?

You *should* go straight to the graphical desktop. If you're asked to enter a username and password on a text screen, then maybe Ubuntu has no drivers for your graphics card.

What hardware do you have in your computer (what processor, how much memory, what brand and model graphics card, etc.)?

You can also check if the CD doesn't contain defects. Boot from the CD, and select "Check CD for defects" (or something similar) from the CD boot menu.

---

### Post by ugm6hr on 2008-10-29
> **GrenadierExercise said:**
> I am becoming convinced that the problem lies in the PC as no one seems to have dificulty in trying out Ubuntu from CD.

Provided you are genuinely booting from the LiveCD (a previous post mentions Windows and a reboot - which is not required for LiveCD use) - then the problem is with the CD.

Use a torrent engine to check (and possibly re-download) the iso file, and then reburn.

Although I suspect that you may have actually installed Ubuntu with Wubi, based on your dexription here:
> **GrenadierExercise said:**
> I selected "Demo" when running CD in XP, then after reboot "English" language and "Trying Ubuntu without any change to your computer". After kernel loaded I end up being asked for username and password, none of which is accepted.  It implies to me that maybe default entries exist, but what??  I have tried all the obvious possibilities with no luck.

---

### Post by GrenadierExercise on 2008-10-30
> **ugm6hr said:**
> Provided you are genuinely booting from the LiveCD (a previous post mentions Windows and a reboot - which is not required for LiveCD use) - then the problem is with the CD.

Use a torrent engine to check (and possibly re-download) the iso file, and then reburn.

Although I suspect that you may have actually installed Ubuntu with Wubi, based on your dexription here:
I am cold booting from the downloaded CD.  The downloaded iso file was md5sum checked and after burning the CD self checked after booting.  I have tried alternative downlod versions. i386 and 64bit as well as trying an alternative mirror site with identical results each time.  (The mentioned reboot from windows was my first effort at running the Ubuntu CD.  All subsequent tries have been from cold boots.)

---

### Post by GrenadierExercise on 2008-10-30
> **jespdj said:**
> The screen where you are asked to enter a username and password, is that a text screen (black with light letters, nothing graphical) or do you see the graphical login screen?

You *should* go straight to the graphical desktop. If you're asked to enter a username and password on a text screen, then maybe Ubuntu has no drivers for your graphics card.

What hardware do you have in your computer (what processor, how much memory, what brand and model graphics card, etc.)?

You can also check if the CD doesn't contain defects. Boot from the CD, and select "Check CD for defects" (or something similar) from the CD boot menu.
It is a graphical login screen.  The Cd was self checked at the CD boot menu.
My desktop is a (HP) Compaq Presario 061, AMD64Athlon, model EC520AA-ABU SR1519UK GB530, main board MSI Amethyst-M version 1, processor AMD Athlon 64 3200 clock speed 1989 Mhz, graphics ATI RADEON XPRESS 200 Series, memory installed 3584 MBs.

---

### Post by GrenadierExercise on 2008-10-30
> **CatKiller said:**
> I just checked my 8.04 cd (I don't have a later one) and the username/password is as I stated earlier. Are you using the 64-bit version? It might be significant information to someone.

To recap; you are definitely just booting from the cd - you aren't launching anything in Windows? You haven't used Wubi (the Windows application that lets you install Ubuntu within Windows)? You've not already set up a username and password - perhaps as part of that "Demo" step that you mentioned? It's definitely an Ubuntu login screen, rather than anything else (there will be a distinctly brown & orange theme - I've not used the default login screen for about two years, so I can't remember exactly what it looks like)?

... something I've just thought of: when you're at the login window, pressing Ctrl-Alt-F1 should take you to a black screen with white writing. At the bottom of this text, does it say ```
ubuntu@ubuntu
``` or does it say ```
ubuntu login:
```
I am doing everything as you comment.
I have tried your suggested use of ctrl-alt-F1 at the login screen appearance but unfortunately the programme locked solidly and required the big red switch treatment to shut down and reboot.

---

### Post by CatKiller on 2008-10-30
When you attempt to log in, does it actually say you're using the wrong username/password, or does it try to do something and then kick you back to the login window?

I'm starting to think that there might be some kind of graphical problem that's stopping GDM from successfully getting to the desktop even though you're using the correct credentials (as the automatic login does).

When you're at the initial Ubuntu menu there is an option, which I believe is selected with F4, that lets you select different options for the graphics than the default auto-detect. You may be able to test out the Ubuntu environment in a lower resolution, and then if you ultimately decide to install Ubuntu for real then we can try to get your graphics working as they should.

EDIT: If you already know that you want to install Ubuntu, then there are other install methods that don't need a working Ubuntu desktop, like the text-based Alternate disc, or Wubi.

Also, you say that when you went to the first virtual console (Ctrl-Alt-F1) the program locked up. There are situations where this might show a black screen with a blinking (or occasionally fixed) cursor in the top-left corner. Ctrl-Alt-F2 to -F6 will take you to the other virtual consoles, -F7 will take you back to X (or the GDM login screen), and -F8 will display some messages from the startup process. So it might not have locked up, but appeared that way. Sorry, I should have given you more information on how to get back before I asked you to try it. I just had the idea that the consoles might still have automatically logged in, which would have definitely pointed to a GDM or X problem. Not that I actually know how the automatic login on the live cd works.

The only time I've seen the virtual consoles in this state is when there's been a problem with the framebuffer (which is related to the graphics system), which is why I'm still leaning towards a graphics problem as the root cause of your problem.

---

### Post by GrenadierExercise on 2008-10-31
> **CatKiller said:**
> When you attempt to log in, does it actually say you're using the wrong username/password, or does it try to do something and then kick you back to the login window?

I'm starting to think that there might be some kind of graphical problem that's stopping GDM from successfully getting to the desktop even though you're using the correct credentials (as the automatic login does).

When you're at the initial Ubuntu menu there is an option, which I believe is selected with F4, that lets you select different options for the graphics than the default auto-detect. You may be able to test out the Ubuntu environment in a lower resolution, and then if you ultimately decide to install Ubuntu for real then we can try to get your graphics working as they should.

EDIT: If you already know that you want to install Ubuntu, then there are other install methods that don't need a working Ubuntu desktop, like the text-based Alternate disc, or Wubi.

Also, you say that when you went to the first virtual console (Ctrl-Alt-F1) the program locked up. There are situations where this might show a black screen with a blinking (or occasionally fixed) cursor in the top-left corner. Ctrl-Alt-F2 to -F6 will take you to the other virtual consoles, -F7 will take you back to X (or the GDM login screen), and -F8 will display some messages from the startup process. So it might not have locked up, but appeared that way. Sorry, I should have given you more information on how to get back before I asked you to try it. I just had the idea that the consoles might still have automatically logged in, which would have definitely pointed to a GDM or X problem. Not that I actually know how the automatic login on the live cd works.

The only time I've seen the virtual consoles in this state is when there's been a problem with the framebuffer (which is related to the graphics system), which is why I'm still leaning towards a graphics problem as the root cause of your problem.
Many thanks for your detailed reply - your help much appreciated.
I have today tried the try-out exercise with Ubuntu 8.10 desktop i386 version and IT WORKS!!!   I have been able to take a good look at this latest issue of Ubuntu and will proceed to install.  I cannot explain why the previos versions would not mount on my machine but think that your pointer towards a possible graphics problem is most likely correct.  Some time back my attempt to update the graphics driver from the HP/Compaq support site failed due to the necessity to update the system BIOS first, which I was reluctant to do.
Thanks again for your help.

---

### Post by CatKiller on 2008-10-31
> **GrenadierExercise said:**
> I have today tried the try-out exercise with Ubuntu 8.10 desktop i386 version and IT WORKS!!!

Good stuff. I hope you enjoy it, now you're started.

---

