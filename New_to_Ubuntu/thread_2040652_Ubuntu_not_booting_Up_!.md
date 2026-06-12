---
title: "Ubuntu not booting Up !"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by abc260191 on 2012-08-11
I tried to install Ubuntu in my Sony Vaio laptop with 52GB left space(Ubuntu took up 29Gb), 3Gb DDR3 RAM .I chose the option of installing alongside Windows with no dedicated partition.. The installation went fine and on rebooting, I saw an option of choosing between Win7 and Ubuntu.. Choosing Ubuntu leads me to a blank black screen with nothing happening at all.. Btw, Win7 is working perfectly fine.

Should I delete and re-install?? What could be the possible reason for this failure of booting?? Please Help !

---

### Post by abc260191 on 2012-08-11
Please Reply !!!

---

### Post by Kalanac on 2012-08-11
By blank screen do you mean completely black and unlit or do you see a cursor or similar?  Also, I presume you're installing the latest version of Ubuntu?  (12.04: Perfect Pangolin)

---

### Post by ajgreeny on 2012-08-11
> **abc260191 said:**
> I tried to install Ubuntu in my Sony Vaio laptop with 52GB left space(Ubuntu took up 29Gb), 3Gb DDR3 RAM [COLOR=Red].I chose the option of installing alongside Windows with no dedicated partition.[/COLOR]. The installation went fine and on rebooting, I saw an option of choosing between Win7 and Ubuntu.. Choosing Ubuntu leads me to a blank black screen with nothing happening at all.. Btw, Win7 is working perfectly fine.

Should I delete and re-install?? What could be the possible reason for this failure of booting?? Please Help !
Do you mean that you installed ubuntu inside windows using wubi?  Did you boot from the ubuntu CD, or did you run the CD from within windows?

---

### Post by Bashing-om on 2012-08-11
ABC,,, 
  We are awaiting your response...
maybe a display graphical problem (?).... if so there are measures to be taken to get you up and running!

---

### Post by abc260191 on 2012-08-11
sorry for late reply.. Yes completely blank screen during boot process after it says that it will complete installation and asks to press Esc key for taking a different mode and counts down for a couple of seconds..Then the screen goes all blank.. I waited for about 20 min also but no gain !!!

Yes I used wubi installer.. Not the latest version..basically I downloaded 695 Mb iso image(to fit in 700Mb CD)..mounted it on daemon tool..pasted the inner files in a blank CD and burned the data on that CD..then I used that CD to install the ubuntu..

Thanks for your kind consideration..Waiting anxiously for a reply....

---

### Post by abc260191 on 2012-08-11
And yes, I tried all the keys on my keyboard during the blank phase but no gain! The only option that remains is forceful shut down & restart in windows..

---

### Post by abc260191 on 2012-08-11
In addition, tried Esc key for a different mode of installation boot up .. tried NORMAL MODE, GRAPHICS MODE, DEMO MODE .. in demo mode it also plays the intro music of ubuntu...screen remains completely blank !! :confused:

---

### Post by Bashing-om on 2012-08-11
abc;
  Not to fret.
1. What do you get at the install screen ?
     if only black screen and NO blinking cursor in the top left corner of the screen. then try 
2. Reboot the live cd and hold down the shift key, do you now get a menu ?
at the bottom of the screen there are some boot options (several) for starters try "nomodeset" ... and advise ...

BDQ

---

### Post by abc260191 on 2012-08-11
thanks for the reply..

But when I hols shift key during bootup with CD in drive.. i get a GNU GRUB menu with following options :

ASCL turnaround
DEMO Mode
Verbose Mode
Normal Mode

I have tried all these options.. all lead to blank screen with no cursor..there is <Tab> option for Command line but nomode command is not available there.. Should I re-install ubuntu??

Any suggestion would be a great help !

---

### Post by Bashing-om on 2012-08-11
abc;
 I have had no experience with the wubi install ... that said . the problem as I see it ,is graphical display in nature. ...need to get to the linux kernel boot line
something like this (
[COLOR=Red]linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro   quiet splash vt.handoff=7[/COLOR]and insert the "nomodeset" parameter after the "quiet splash" parameter.
 or maybe I best do some homework and look into wubi (OH NO! I do not like windows) ...will do !

---

### Post by Bashing-om on 2012-08-11
abc;
 Here we go try these and advise ... apologize if I am a bit obtuse!

 
[https://wiki.ubuntu.com/WubiGuide/](https://wiki.ubuntu.com/WubiGuide/)  has the following:
-----------
Video Problems after second reboot

If you experience problems after installation, press "Ctrl+Alt+F2" and run:

sudo dpkg-reconfigure xserver-xorg

Select the VESA driver and leave all other options at default. Then reboot. That will allow you to boot into a safe graphics mode (limited resolution) you should then be able to install the appropriate drivers or try other solutions as needed.

=========
For kernel command line, immediately after reboot, press the insert key rapidly after selecting Wubi and/or press ESC at the countdown after selecting "Ubuntu" and use "c" or "e" to enter the appropriate boot options manually 
--------------
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)  post nbr 8 has the excellent instructions for changing the graphics access.

---

### Post by marlow59 on 2012-08-11
you may also try to boot into recovery mode and see if some packages are damaged.

---

### Post by abc260191 on 2012-08-12
Thank You So much Bashing Om.. Ubuntu installed and boot up happened .. every time I press e and enter nomodeset ..

---

### Post by Bashing-om on 2012-08-12
abc ;
  Outstanding .... you do good work!
I look forward to your  enthrallment with ubuntu.

please mark this thread as solved ...

---

### Post by Bashing-om on 2012-08-13
abc;
 If and when you get back to this thread ... need to edit your grub file to make the change permanent .... will advise if needed ...

BDQ

---

