---
title: "Logon Screen Resolution"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Geekboy on 2008-11-14
How can I change the logon screen resolution size in Ibex?  The setting is probably for 1600x1200 and I want to change it to 1280x1024.  I took a look at Xorg.conf but there is nothing in there for resolution.

---

### Post by Crafty Kisses on 2008-11-14
Are you talking about the boot splash screen?

---

### Post by Kellemora on 2008-11-14
Hi Geek

Although the title don't fit your problem, the solution, starting at the bottom of the first page should help you fix your log-in screen to whatever you want it to be.

TTUL
Gary

Huge Log-in Screen?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
FWIW:  I did NOT have any luck using StartUpManager from Synaptic.  Editing /etc/usplash.conf xres and yres was unnecessary as they were already correct.  Neither dpkg-reconfigure -phigh xserver-xorg nor update-initramfs -u worked either to correct the HUGE Log-in screen problem.

This is from a total Noob, but took much research to find out exactly, what changed where, to figure it out.  It's also fairly long because it is geared toward big dummies like myself, hi hi.....

A Simple Test:
If you return your monitor to the original default settings, you should find that your log-in screen once again works right.  This was the CLUE to finding out which file controlled the log-in screen for me!

How to change screen resolution (not using Properties) is in another document titled “Screen Resolution Problems?  Easy fix!”  This too might cause log-in screen obesity!

Being a Noob, there may be an easier faster way to do this, but this is what consistently works for me.

The following changes are made using the “ROOT TERMINAL”.

The Terminal in Applications/Accessories does not work for me.  No Permission when you go to save!
If you do not have the Root Terminal under Applications/System Tools, then RIGHT CLICK on Applications, select Edit Menus (by left click) and a Main Menu will appear shortly.  In Main Menu (under Menus) select System Tools and the screen (titled Items) to your right will change.  Place a check mark in the box to the left of Root Terminal and select CLOSE.  The Root Terminal will now appear as a selection when  you select Applications/System Tools.

NOW, Select the Root Terminal.  Before the Root Terminal Opens you will have to Log-in as Administrator.  This is your NORMAL log-in!  Why it doesn't ask for Root Log-in I have no idea.
Even though it shows you are IN Root, you will notice that you are still in your /home/name/ directory.  If you try to open the required file from here, you will get a blank screen so DON'T save it, Close without Saving.

At the prompt type  cd ..  this will take you back to your /home directory.
Type  cd ..  again and you will be in the ROOT Directory and can perform the following command.

Note that the X is a capital letter, all others are lower case!  It's X Eleven not XII.

gksu gedit /etc/X11/xorg.conf  This will open your xorg.conf file for editing.

SAFETY OPTION:  Right Click on File, select SAVE AS (left click).  Add  .old  behind the filename xorg.conf so it reads xorg.conf.old, then Right Click on SAVE.  You will now be VIEWING the saved file so select Right Click on the OPEN Icon and select xorg.conf to reopen the working file for changes.  You can always revert back to the original file by saving it as xorg.conf without the word .old behind it.  End of Safety Option.

Scroll down (near the bottom) and you will find a line titled Section “Screen”, tabbed in twice you will find a line that reads Virtual followed by two sets of digits.  You should recognize these digits as being common screen resolutions.
Be very careful here!  It's better to be safe than sorry.
You may notice a High screen resolution listed here, one your monitor cannot recognize, like 1792 1344 (which defaults to 640 480), or it may be very low, like 640 480 already.  My desired screen resolution for the log-in screen is 1024 768 so those are the numbers I chose to replace the numbers.

DO NOT delete the existing numbers yet.  They appear to me to be in placeholders is why!

For safety reasons.  Place your cursor after the first digit of the first existing number and if different from the first number already listed, type the new single digit then move left one space and delete the first number, then move back right and enter your remaining numbers, then delete the old numbers from behind it.  If you are going from 1792 down to 1024, just place your cursor between the 1 and 7 and type 024 then delete the 792 ONLY.  I still use this method if I'm going from 640 up to 1024, placing the cursor between the 6 and 4 as my starting point, typing the whole number 1024.
OK, move to the second number, it may be 1344 and you want 768.  Use the same method here too!  Place your cursor between 1 and 3, type 768, delete the 344, move left and delete the leading 1.

This may be an unnecessary overkill way of doing it.  But why take chances when we're only Noob's?

Go to the top of the Screen and Select SAVE, then wait for a bit to make sure it saved before exiting the gedit program.

This has worked on all Ubuntu 8.04 Hardy Heron machines I have tried it on in my testing!

FWIW:  I did NOT have any luck using StartUpManager from Synaptic.  Editing /etc/usplash.conf xres and yres was unnecessary as they were already correct.  Neither dpkg-reconfigure -phigh xserver-xorg nor update-initramfs -u worked either to correct the HUGE Log-in screen problem.

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video card.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video card.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video card.
e-machine T6524, 2.30GHz Athlon 64-3500+, ATP Radion Express 300 video card.

TTUL
Gary/aka Kellemora
9/10/08 – rev 9/15/08

---

### Post by karlmp on 2008-11-14
check this: [http://ubuntuforums.org/showthread.php?t=972977](http://ubuntuforums.org/showthread.php?t=972977)

---

### Post by Mr_JMM on 2008-11-14
The solution in that thread worked for me, thanks.


Ps. You're a weird guy, Karl :lolflag:

---

### Post by Geekboy on 2008-11-16
Thanks Karlmp.   That worked for me!

---

### Post by alienexplorers on 2008-11-16
Have you tried startupmanager and editing /rtc/gdm/gdm.conf to fix your problem.
In gdm.conf edit the file and search for a line called server-stabdard and look for the line with sydit 0 in it and add -dpi 96.....  Save file and reboot,

---

### Post by bimasakti85 on 2008-11-16
What I've done usually is by adding :

SubSection "Display"
     Virtual       1280 800
EndSubSection

before the EndSection of the screen in the xorg.conf . In my case, I want the logon screen to be 1280 800.

---

