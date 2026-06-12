---
title: "pc wont start after using startup manager"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by zabih on 2012-02-27
Hi everyone

I wanted to make windows to start first. I searched on google and installed start up manager on my Ubuntu 11.10 the latest version. and windows 7 PC. I also burned the hbcd ISo desk which got stuck at generating md5 since then my PC when I start screen flashes couple of times and nothing g happens. 

pls help.....

---

### Post by Jake5 on 2012-02-27
I think I've seen this before.....
I suppose try
# sudo update-grub
If you can get to the terminal...
If that doesn't work I've heard that holding down the shift key
will bring you to another screen, and from there you replace some file with another. I can't remember, but someone else with far greater knowledge than mine will be along shortly to help.

---

### Post by zabih on 2012-02-27
> **Jake5 said:**
> I think I've seen this before.....
I suppose try
# sudo update-grub
If you can get to the terminal...
If that doesn't work I've heard that holding down the shift key
will bring you to another screen, and from there you replace some file with another. I can't remember, but someone else with far greater knowledge than mine will be along shortly to help.

Thx for quick reply

Waiting for solutions

---

### Post by HeroOfCanton on 2012-02-27
To clarify, does the screen flash when trying to boot into ubuntu or is this on boot before getting to select the OS?

---

### Post by zabih on 2012-02-27
> **HeroOfCanton said:**
> To clarify, does the screen flash when trying to boot into ubuntu or is this on boot before getting to select the OS?

On boot before selecting OS. When I press power button after bios screen the screen flashes

---

### Post by HeroOfCanton on 2012-02-27
> **zabih said:**
> On boot before selecting OS. When I press power button after bios screen the screen flashes

Eek! First try holding Left Shift while booting to see if the boot manager will open up.

If that doesn't work you will need to rebuild GRUB so you can boot. You will need a live CD or USB for this, then create a cd for the boot repair software from there.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Once that's done (and if you didn't change the boot order during the rebuild) I would personally try to edit the default boot OS manually in GRUB. It's really not hard enough to justify needing to install software.
[http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/](http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/)

(FYI, that article actually mentions not using startup manager because of bugs with grub 1.99. Oops!)

If that doesn't help, someone with far greater knowledge than mine or Jake's will be along shortly to help. :D

---

### Post by zabih on 2012-02-27
> **HeroOfCanton said:**
> Eek! First try holding Left Shift while booting to see if the boot manager will open up.

If that doesn't work you will need to rebuild GRUB so you can boot. You will need a live CD or USB for this, then create a cd for the boot repair software from there.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Once that's done (and if you didn't change the boot order during the rebuild) I would personally try to edit the default boot OS manually in GRUB. It's really not hard enough to justify needing to install software.
[http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/](http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/)

(FYI, that article actually mentions not using startup manager because of bugs with grub 1.99. Oops!)

If that doesn't help, someone with far greater knowledge than mine or Jake's will be along shortly to help. :D
Thx Wii try and update this thread when I finish work

---

### Post by zabih on 2012-02-27
> **HeroOfCanton said:**
> Eek! First try holding Left Shift while booting to see if the boot manager will open up.
 
If that doesn't work you will need to rebuild GRUB so you can boot. You will need a live CD or USB for this, then create a cd for the boot repair software from there.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
Once that's done (and if you didn't change the boot order during the rebuild) I would personally try to edit the default boot OS manually in GRUB. It's really not hard enough to justify needing to install software.
[http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/](http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/)
 
(FYI, that article actually mentions not using startup manager because of bugs with grub 1.99. Oops!)
 
If that doesn't help, someone with far greater knowledge than mine or Jake's will be along shortly to help. :D
 
 
thank you, this worked but i got 3 new problems
 
ubuntu wont connect to wifi ( i dont have a rj45 cable to test wired internet)
mouse doesnt work
graphic is funny

---

### Post by oldos2er on 2012-02-28
Just FYI, Startupmanager is no longer being developed; Grub Customizer is recommended instead. [https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

---

### Post by Mark Phelps on 2012-02-29
> **zabih said:**
> thank you, this worked but i got 3 new problems
 
ubuntu wont connect to wifi ( i dont have a rj45 cable to test wired internet)
mouse doesnt work
graphic is funny

Sorry to hear that ... but don't start adding problem after problem to an existing thread.  That really makes problem solving very difficult.

Please open new threads for your new problems.

And "graphic is funny" tells us nothing useful.  Need to be more descriptive if you want help.

---

