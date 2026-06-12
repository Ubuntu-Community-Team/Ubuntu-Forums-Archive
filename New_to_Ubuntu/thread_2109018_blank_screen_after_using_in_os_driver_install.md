---
title: "blank screen after using in os driver install"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by Mantinziza on 2013-01-26
I have an nvidia gtx 570, this is my first time using ubuntu, I manages to get everything right up to this point. After I used the in system update to install my graphics card update. When i select ubuntu from the os selector. The screen just goes blank. Ive searched through plenty of google forums and every thing seems to have a different answer. So much help would be appreciated.

---

### Post by grahammechanical on 2013-01-26
It would help if you told us the version of Ubuntu that you were using. They other day I assumed someone was using 12.04 or 12.10 and I gave an explanation for both versions and the person was using 10.04 (3 years old and forgotten by me). One of the reasons for so many different suggestions is the fact that we get so little information about what is going wrong.

I cannot tell you how to fix this because I do not know what is wrong.

At the OS selector (called the Grub menu) select one of the earlier kernels and see if that helps. If you are using 12.04 it will be on the screen. If you are using 12.10 you will find earlier kernels in the Advance Options for Ubuntu sub-menu.

Or, at the Grub menu select Recovery Mode. At the Recovery Mode menu select Resume. That sometimes helps. In 12.10 Recovery Mode is found in the Advanced Options sub-menu. That will load Ubuntu without activating a video driver.

If you can get to working desktop, then try another video driver. In 12.04 we look for the Additional Drivers Utility. In 12.10 we go to System Settings>Software Sources and look in the Additional drivers tab.

We can choose from an open source driver called Nouveau and four or more proprietary video drivers. What video card do you have, by the way? You do not tell us. Try changing the video driver.

Ubuntu developers cannot modify proprietary video drivers. If one is buggy then all the developers can do is pass the bug report to the proprietary developers and then we wait for them to put things right.

I have had experience of an updated (newer) proprietary video driver breaking the OS at some point in the loading process.

At what point do you get a black screen? Before you get to the log in screen? Or after you log in to Ubuntu? Sorry, but this is all I can give you.

Regards.

---

### Post by Mantinziza on 2013-01-26
I yhave an nvidia gtx 570, with ubuntu 12.04. It gets to the grub menu I then when i pick the standard ubuntu it starts to load then goes blank. Before i installed the driver it worked fine, now it just goes blank

---

### Post by Bashing-om on 2013-01-26
Mantinziza; Hi !

Follow grahammechanical's advise and get to the desktop and install different drivers.
Often the "open source" nouveau driver is the better choice.
12.04: Launcher -> System Settings -> Additional Drivers.

[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by squakie on 2013-01-26
Well, this should help:


[LIST]
[*]at the grub boot menu highlight Ubuntu but don't press enter.  Follow the on screen prompt at the bottom to edit that line.  Change "splash" to "nomodeset splash".  Since you have the nVidia card you'll need to do that.  This will only work for the current boot.
[*]if that works for you post back and we can tell you how to make it permanent.
[/LIST]

---

### Post by Mantinziza on 2013-01-26
well I tried all of the above tricks and none of them worked, I even tried changing the "splash" text. like said above and it got stuck at some execution type 1 failed. text over nad over again. I would love to switch over to this but I can't get it to work. I'm just gonna remove it all.

It's ubuntu 12.04. Agian it worked just fine till i tried installing the driver again for a gtx 570 nvidia card, right in the os itself. After that whenever i try to run ubuntu through the grub menu I just get a flashing underscore for a few seconds then blank screens.

Again some help would be nice.

---

### Post by Sef on 2013-01-26
> It's ubuntu 12.04. Agian it worked just fine till i tried installing the driver again for a gtx 570 nvidia card, right in the os itself. 

Is it the restricted driver that you are installing? If it is, use nouveau as was previously suggested by Bashing-Om.

---

### Post by squakie on 2013-01-27
You may need to try ACPI=NO and/or NOAPIC in the boot line - try as you did with the nomodeset option/

---

### Post by Mantinziza on 2013-01-29
Ok I ahve tried all of these options minus the one above. First off, this is my first time ever trying linux. Before hand i had windows, I have gotten tired with how greedy microsoft has gotten. I do like this software quite a bit. Ive played with it not installing the driver. I want it but I need to update my driver in order for it to install properly so here it is.

Im new I have no clue where, these commands are supposed to be typed in. I do have computer experience but no linux, this looks all greek to me. 

Again I have an nvidia gtx 570, after I install any of the driver updates supported from linux itself. (no im not using a cd), when I get to the grub menu and select it to boot after the install. The screen flashes purple for a second, like it normally does when I start it. Straight to a black screen, the monitor stays on but it just goes black. 

There are no nouvea files in the updater, I have tried that nomodeset trick. And i have no clue where to put the files told to me above. 

Please I know I'm new to this, but I would really like some help figuring this out.

---

### Post by Bashing-om on 2013-01-29
Mantinziza; 

We were all new to this operating system at one time, do not feel bad that you just do not know. This indeed is NOT windows.

Back up and regroup: 
Booting into you system; hold the shift key as soon as the bios screen clears -> grub boot menu;
Insure the first line remains highlighted at this time and press the "e" key for edit mode;
Arrow down to the line containing the term "quiet splash" arrow across to that term and insert also the term "nomodeset" -with out the quotes- ;
ctl+x to continue the boot process.

Do you now boot into the GUI login (degraded state) ?

Further advise is pending this result. 

[INDENT][INDENT][INDENT]try'n to help

[/INDENT][/INDENT][/INDENT]

---

### Post by squakie on 2013-01-30
Sorry - didn't know they didn't know how to do this when I posted nomodeset earlier.  Perhaps I should have been more descriptive.

---

### Post by Mantinziza on 2013-01-30
Thankyou, I tried the above. And All I got was the same blank screen. Same as before. Am i just adding nomodeset or deleting quiet splash and typing it in.

No I do not know what degraded state is. And once I do get to this point what should I do?

---

### Post by Bashing-om on 2013-01-30
Mantinziza;

Following my lead, the graphics will be in lower resolution - the vesa graphics driver.
Removing "quiet splash" can be a good thing as the text boot messages may then be seen.

If you can get to a gui and able to log in to ubuntu; Then:
Launcher (left side of screen) -> System settings -> Additional Drivers.
Install the recommended driver (likely, nouveau).

Reboot.

[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

