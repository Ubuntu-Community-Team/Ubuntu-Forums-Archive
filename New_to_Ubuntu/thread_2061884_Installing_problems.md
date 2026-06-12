---
title: "Installing problems"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by Boomshakaka on 2012-09-23
I have a ASUS laptop with Windows 7. I want to install Ubuntu over it but I am having a lot of problems doing it. 

I had to force my laptop to boot the disk through the boot menu. It gives me this strange purple screen. Booting it with UEFI(No idea what that is) gives me a few options. All lead to a bank screen

Running the wubi I couldn't get it to boot from the disk. So it installed some program to help me boot from the disk. After that it went to a blank screen saying Completing Ubuntu install. It never moved so I restarted my computer. I now have to options to boot. One being Windows 7 and the other being Ubuntu. But booting Ubuntu always going to the blank screen saying Completing Ubuntu install. 

Any suggestions?

---

### Post by Bashing-om on 2012-09-23
Boomshakaka; Hi ! Welcome to the forum.

My suggestions:
 In bios-in order to boot the live/install cd- set to boot cd as 1st boot priority.
 As soon as the bios screen clears, depress the shift key and hold until -> ubuntu boot options menu is available.
  In these options choose "nomodeset" and continue to boot into ununtu.

  If you are able to boot at this time (try ububtu) ...advise us of the results. Instructions to install appropriate graphics driver in your installation to follow.

UEFI ...Format on new systems ...we are learning to cope with.
see these links for info:
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise]("http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise")
[http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI]("http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI")

                       hth <==BDQ

---

### Post by Boomshakaka on 2012-09-23
Okay. I changed my boot order so the CD  boots first. Then I held shift. It went to the purple screen but this time actually had a menu with options like install Ubunutu, or check disc for defects. It also had an option menu and I selected the nomodeset. I then clicked install Ubuntu and it went to a blank screen with a blinking cursor and does nothing.

---

### Post by Bashing-om on 2012-09-23
Boomshakaka;

  I regret I was unclear ..What we want to do is get up in the "try ubuntu" mode. The purple screen indicates a graphics problem, "nomodeset" option boots disregarding the onboard chip controller thus defaulting to a vesa mode.

 If we can get you up in "try ubuntu" we know what to do in the real install for permanent fix.

so try ubuntu and advise.

             try'n to help ==>BDQ

---

### Post by Boomshakaka on 2012-09-23
I actually managed to fix the problem by myself. Thanks for the help though

---

### Post by daslinkard on 2012-09-23
> **Boomshakaka said:**
> I actually managed to fix the problem by myself. Thanks for the help though

Please let us know what it was that worked for you so that in the future someone else might benefit from your work around as well.  Also remember to mark the thread as solved!  Thanks!

---

### Post by Boomshakaka on 2012-09-23
Well I have a new problem. I am such an idiot. After Ubuntu was installed it ran great and was awesome. But I turned off my computer without installing my graphic drivers so now it boots to a blank screen with a blinking cursor. Booting in recovery mode or adding nomodeset leads to a screen saying things like Watchdog enabled.
Did I ruin my laptop or what?

---

### Post by Boomshakaka on 2012-09-24
Okay this is getting really strange. 
Okay I reinstalled Ubuntu. I have to use nomodeset to do it. 
The last time I turned off my laptop it wouldn't boot even with adding nomodeset.
So I would think I need to add my graphics driver. The problem is additional drivers doesn't pick anything up and the system says I have a unknown card. I have this computer [http://www.asus.com/Notebooks/Superior_Mobility/U46E/#specifications](http://www.asus.com/Notebooks/Superior_Mobility/U46E/#specifications) and have no idea how to add its drivers to my laptop. 

Any Ideas what to do?

---

### Post by Bashing-om on 2012-09-24
This is a good candidate for  the solution (a Bug no less) here:
[http://askubuntu.com/questions/85318/how-can-i-get-my-intel-integrated-graphics-to-be-recognized-in-system-info](http://askubuntu.com/questions/85318/how-can-i-get-my-intel-integrated-graphics-to-be-recognized-in-system-info)

A simple solution that looks good; Apply it and advise.
[INDENT]just try'n to help <==BDQ
[/INDENT]

---

