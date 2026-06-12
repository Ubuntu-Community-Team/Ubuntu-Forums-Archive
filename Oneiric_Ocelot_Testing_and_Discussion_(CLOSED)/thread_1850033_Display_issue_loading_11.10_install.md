---
title: "Display issue loading 11.10 install"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by leterman12 on 2011-09-25
I'm trying to install 11.10 on my home PC to dual boot with Win 7. You can see my issue from looking at the attached picture. That's what I see every time I i try to load the installer. Any suggestions as to what i can do?

---

### Post by grahammechanical on 2011-09-25
Wow! And welcome to the forums. At what point exactly do you see that? Do you see a message that says Selinux loading (or something like that). Do you get the option to Try Ubuntu or Install Ubuntu?

Regards.

---

### Post by MG&amp;TL on 2011-09-25
...the installer. You mean the live cd, or *wubi*?

And yes, wow. that's a pretty impressive monitor.

---

### Post by MG&amp;TL on 2011-09-25
You HAVE tried the stable ones before, right?

---

### Post by leterman12 on 2011-09-25
> **MG&TL said:**
> ...the installer. You mean the live cd, or *wubi*?

And yes, wow. that's a pretty impressive monitor.

It's the CD and no, I didn't get any options to do anything. I got to the purple screen with the "Ubuntu" logo and thats it.

Thank you about the monitor compliments btw ;)

---

### Post by MG&amp;TL on 2011-09-26
Errr..what monitor do you have, and try a USB, if you have one.

---

### Post by effenberg0x0 on 2011-09-26
Nice maze :) I wish my monitor ever did something so cool.

---

### Post by leterman12 on 2011-09-26
> **MG&TL said:**
> Errr..what monitor do you have, and try a USB, if you have one.

It's an Acer X223W monitor and I'm about to try a USB install. Could it be that Ubuntu can't even recognize my graphics card?

---

### Post by MG&amp;TL on 2011-09-26
What graphics card? It should still boot slightly less spectacularly than that...

Did you have to install a driver with your monitor?

---

### Post by MAFoElffen on 2011-09-26
> **leterman12 said:**
> It's an Acer X223W monitor and I'm about to try a USB install. [COLOR=Red]Could it be that Ubuntu can't even recognize my graphics card[/COLOR]?
What graphics card do you have?

Looking through all the posts so far... I've still missed a few answers on some of the previous questions...  From what you said, you try to "load the installer."  What exactly did that mean?  That you cannot run the LiveCD or the installer on it?

I do not recommend to people to install, until they can successfully "try" or run that version from the LiveCD. (Include LiveCD iso image on USB device)  The LiveCD can be used as a diagnostics tool to make that happen.

another question that was left unanswered asked if you have evr successfully ran any previous version of Ubuntu on your hardware combination before(?)  

There is many things it could be, but without some kind of info and organized feedback, the number of things it "might" be is whole lots and hard to narrow down.  We can help narrow that down...

---

### Post by leterman12 on 2011-09-26
> **MAFoElffen said:**
> What graphics card do you have?

Looking through all the posts so far... I've still missed a few answers on some of the previous questions...  From what you said, you try to "load the installer."  What exactly did that mean?  That you cannot run the LiveCD or the installer on it?

I do not recommend to people to install, until they can successfully "try" or run that version from the LiveCD. (Include LiveCD iso image on USB device)  The LiveCD can be used as a diagnostics tool to make that happen.

another question that was left unanswered asked if you have evr successfully ran any previous version of Ubuntu on your hardware combination before(?)  

There is many things it could be, but without some kind of info and organized feedback, the number of things it "might" be is whole lots and hard to narrow down.  We can help narrow that down...

Here's a run down on my full system, might make things easier:
mobo: nforce 680i SLT
GPU: nvidia geforce 240 GT
CPU: intel core 2 quad Q6600
RAM: 4g DDR3

Sorry to be less specific with my answers. I was trying to run the liveCD, not the installer. I didn't even get as far as choosing whether to install or run Ubuntu from the disc. I have tried 11.04 and ran into the same issue. I haven't tried the USB boot yet but i have prepared a bootable USB key. To answer another one of your questions, there was no driver to install for my monitor, it was just a plug in and play. I'll try switching my display ports from DVI to VGA tough and see if that makes any difference.

---

### Post by leterman12 on 2011-09-26
Just ran the USB with my monitor plugged into VGA instead of DVI and some issue.

---

### Post by MAFoElffen on 2011-09-26
> **leterman12 said:**
> Here's a run down on my full system, might make things easier:
mobo: nforce 680i SLT
[COLOR=Red]GPU: nvidia geforce 240 GT[/COLOR]
CPU: intel core 2 quad Q6600
RAM: 4g DDR3

Sorry to be less specific with my answers. I was trying to run the liveCD, not the installer. I didn't even get as far as choosing whether to install or run Ubuntu from the disc. I have tried 11.04 and ran into the same issue. I haven't tried the USB boot yet but i have prepared a bootable USB key. To answer another one of your questions, there was no driver to install for my monitor, it was just a plug in and play. I'll try switching my display ports from DVI to VGA tough and see if that makes any difference.
Use a "nomodeset" kernel boot switch using the LiveCD instructions from post 3 of my graphics sticky:
              #[**3**]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")

If it comes up with graphics (should with that switch) choose "TRY" and try to boot the OS.  If success and you install, you may have to use that switch one more time on reboot to install your graphics driver.  (Could also reboot into rescue mode to do that...) After that, you shouldn't need that switch again.

---

### Post by jonnyboysmithy on 2011-09-26
I tried to run a 64bit livecd on a 32bit system and it would come up with a scrambled screen similar to what you have.
Just my 2cents :)

---

### Post by leterman12 on 2011-09-26
> **MAFoElffen said:**
> Use a "nomodeset" kernel boot switch using the LiveCD instructions from post 3 of my graphics sticky:
              #[**3**]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")

If it comes up with graphics (should with that switch) choose "TRY" and try to boot the OS.  If success and you install, you may have to use that switch one more time on reboot to install your graphics driver.  (Could also reboot into rescue mode to do that...) After that, you shouldn't need that switch again.

When I'm in the live CD, do I enter all of those commands into the terminal? Or is there something else?

---

### Post by cariboo on 2011-09-26
> **leterman12 said:**
> When I'm in the live CD, do I enter all of those commands into the terminal? Or is there something else?

At the initial boot screen, the one with the little man and keyboard, press any key to get to the menu, then press F6 and select nomodeset from the menu that pops up, then press esc, and finally press enter.

---

### Post by MAFoElffen on 2011-09-27
@cariboo907 - Yes, those pictured instructions were in the post I refrerred him to.

New Problem he's having :
[QUOTE=leterman12]I ran into another problem. I don't know what  happened, but while I was installing the installer crashed. Now  everytime I boot my computer I get an error from grub saying "no such  file detected" and a thing that says "grub rescue" with a place to type.  I don't get an option to go into windows or Ubuntu. Is there anyway I  can get back into windows?[/QUOTE]
Right at this point, there is an incomplete install of the boot loader.

You could get windows started just by using an Ultimate Boot LiveCD (if you had one)... Boot Repair Disk, bootFix or testdisk (also if you had them) 

But with your skill level and where you are at, the correct thing to do is to restart the installer / reinstall again and see if you can successfully complete your install. Right?  Where in the intstall did it crash and do you suspect why?

*** Note on installer crashes- On daily dev builds, I do 4-6 fresh installs a day.  I get about one "normal" installer crash during the download/copy/install/config cycle a day, where "nothing" was really wrong... *maybe how I held my tongue and the placement of the moon or something.*  I don't try to read too much into it, unless it definitely consistently isn't working for me.  If it exits or hangs during the install before int completes, quickly look for anything obviously wrong.  If nothing found try again.

Please try again...

---

### Post by leterman12 on 2011-09-28
Now I know it'll be a bit of an under taking, but how would I repair or over right my MBR to ignore GRUB completely?

---

### Post by cariboo on 2011-09-28
What makes you think grub is the problem, or are you just giving up? 

If you are giving up on Oneiric, I'd suggest you install Lucid (10.04) so that you can learn how to use Ubuntu on a stable version.

---

### Post by MAFoElffen on 2011-09-28
> **cariboo907 said:**
> What makes you think grub is the problem, or are you just giving up? 

If you are giving up on Oneiric, I'd suggest you install Lucid (10.04) so that you can learn how to use Ubuntu on a stable version.
No, it's an easy fix...

@caraboo907

Sorry about changing pace... Look at my post 3 back (post #17).  He wrote me a private message about some changes and other problems he got to...  i messaged him back that we should really take care of those problems in his thread (here.)

Seems that leterman12 got the LiveCD going with our instructions... He then started an install and the installer crashed before it was completed.  Sounds like it crashed during the Grub install, as now upon reboot --> Grub says it can't find a file and drops down to a Grub Rescue prompt.  No access to his Windows instance... So it must have at least overote the MBR before crashing.

At this point, with a newer user = It's a fresh install that didn't complete.  Start over, meaning boot up on the LiveCD and Install again. Choose to overwrite the install as if it wasn't there in the partition process... It will install Grub as the boot loader and off he goes with a fresh install... Right?

As a fresh install, if it "completes" it's further than he got last night... and he's lost nothing.

EDIT-- I didn't recommend or give him instructions to "just" install grub from the LiveCD as his install process did not "complete."

---

### Post by leterman12 on 2011-09-28
All problems are solved! I used my good old win98 bootdisk and wiped the Linux partitions and repaired my MBR. Thanks for all help!

---

