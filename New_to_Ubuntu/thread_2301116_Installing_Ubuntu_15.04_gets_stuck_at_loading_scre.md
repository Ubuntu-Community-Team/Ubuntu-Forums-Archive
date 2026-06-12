---
title: "Installing Ubuntu 15.04 gets stuck at loading screen."
date: 2015-10-30
forum: New to Ubuntu
---

### Post by Wawrzyn on 2015-10-30
Hello. I wanted to install Ubuntu 15.04 (64 bit) so i burned the ISO file(downloaded from Ubuntu's official site) and booted my computer from it.
Everything went fine, but at some point, the loading process stopped at this screen: [http://i1243.photobucket.com/albums/gg558/squiffyk7/Ubuntuscreen.png](http://i1243.photobucket.com/albums/gg558/squiffyk7/Ubuntuscreen.png)
I also ran diagnostics on the DVD I'm booting from but no problems were found.
I tried both installing and running it without installation but i have the same problem. After a little bit of searching i found that i can hide the loading screen with F6 and see what the problem is. The bad news is that there were no problems. The installation just stopped at a certain line and did nothing. I found no other issues like this one. Here is a photo i took of the logs: [http://i63.tinypic.com/28bwqcx.jpg](http://i63.tinypic.com/28bwqcx.jpg)

My computer specs are:
CPU : Intel Core i7 4710HQ
RAM : 8GB
Graphics : Nvidia GeForce GTX860M

Also it might be of importance to mention that i already have Windows 8.1 installed and I'm trying to have dual booting.
What is the problem and how can i solve this?

Please ask to get any additional info I might have missed.

EDIT: I dont know how to properly link pictures, so I'm gonna put links instead.

---

### Post by Geoffrey_Arndt on 2015-10-30
OK, to be sure we understand what you're actually doing . . . what is the "loading" process?   Does that mean the live iso did not boot up to a desktop with the "try ubuntu" or "install ubuntu" options?    Or does that mean, IF, you did get to that initial desktop screen, did you start the actual install process (by clicking the install option)?    Also, since you have Windows 8.1 . . . what did you do in Windows to prepare the system for an install?

These would be (but are not limted to):
>   shrink windows partition (using windows tools)
>   rebooting into windows twice after reduction (so windows can run repairs via chkdsk)
>   creating hdd space (unallocated OR a partition with a linux file system such as ext4)
>   disabling win secure boot, fast/quick boot, hibernation (all via uefi firmware setup screens).   

Just some food for thought - - IF you did all the above, and were in process of the actual install, the nvidia system often does not allow to boot into Ubuntu (without install of proprietary gpu drivers), thereby requiring a boot option of "nomodeset"

Anyway, more info may help.

BTW . . . as 15.04 only has a couple months support left . . . . best to install 15.10 instead.

One final question - - are you installing using UEFI mode?  Or did you by chance, enable legacy bios/mbr mode instead?

---

### Post by Wawrzyn on 2015-10-31
> **Geoffrey_Arndt said:**
> OK, to be sure we understand what you're actually doing . . . what is the "loading" process?   Does that mean the live iso did not boot up to a desktop with the "try ubuntu" or "install ubuntu" options?    Or does that mean, IF, you did get to that initial desktop screen, did you start the actual install process (by clicking the install option)?    Also, since you have Windows 8.1 . . . what did you do in Windows to prepare the system for an install?

These would be (but are not limted to):
>   shrink windows partition (using windows tools)
>   rebooting into windows twice after reduction (so windows can run repairs via chkdsk)
>   creating hdd space (unallocated OR a partition with a linux file system such as ext4)
>   disabling win secure boot, fast/quick boot, hibernation (all via uefi firmware setup screens).   

Just some food for thought - - IF you did all the above, and were in process of the actual install, the nvidia system often does not allow to boot into Ubuntu (without install of proprietary gpu drivers), thereby requiring a boot option of "nomodeset"

Anyway, more info may help.

BTW . . . as 15.04 only has a couple months support left . . . . best to install 15.10 instead.

One final question - - are you installing using UEFI mode?  Or did you by chance, enable legacy bios/mbr mode instead?

I did get the desktop with "Try Ubuntu" and "Install Ubuntu", and i tried both options, and both of them get locked in the same place. If you take a look at the first picture i added, you will see the screen I'm stuck at.

And yes, I did all the initial Windows preparations you named. I'm also installing using UEFI mode (i saw that setting in the bios, and did not change it to legacy).
I'm going to search a little and try to figure out how to start the installation with "nomodeset". Thank you for that suggestion.

When it comes to the version, is it possible to upgrade after installation? I dont have any spare DVDs laying around for the newer version.

---

### Post by Geoffrey_Arndt on 2015-10-31
Yes . . . you can update after install of 15.04.    By the time you've completely brought 15.04 up to date, you are in an optimal place to upgrade, but the upgrade can take another couple hours of attentive time.

I suspect the nomodeset boot option is your best 1st solution to finishing the install . . . just let us know how it goes because there are other options also.

Note that Ubuntu will display in a lower res, slower version UNTIL you've completed the "system settings>Software & Updates>add'l drivers tab" driver install process.

---

### Post by Bucky Ball on 2015-10-31
> **Geoffrey_Arndt said:**
> BTW . . . as 15.04 only has a couple months support left . . . . best to install 15.10 instead.

+1. 15.04 reaches end-of-life in January 2016 when you are going to need to upgrade to 15.10 anyway so may as well start there. You can upgrade directly to the next LTS release, 16.04 LTS, from 15.10 and that is supported for five years, until 2021. You can [use a USB to install Ubuntu]("www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). You don't need a DVD. :)

The other option is to install 14.04 LTS and upgrade directly LTS to LTS when the 16.04 LTS upgrade is available. Good luck. :)

---

### Post by Wawrzyn on 2015-10-31
> **Geoffrey_Arndt said:**
> Yes . . . you can update after install of 15.04.    By the time you've completely brought 15.04 up to date, you are in an optimal place to upgrade, but the upgrade can take another couple hours of attentive time.

I suspect the nomodeset boot option is your best 1st solution to finishing the install . . . just let us know how it goes because there are other options also.

Note that Ubuntu will display in a lower res, slower version UNTIL you've completed the "system settings>Software & Updates>add'l drivers tab" driver install process.

I did complete the installation with nomodset and everything works fine except for the real hardcore crashes i keep getting after a minute or so using Ubuntu. It doesn't even respond to Alt + Rq Sys + R E I S U B. But I'm gonna search the internet first before I waste your time here. Thank you very much for the help!

---

### Post by Bucky Ball on 2015-10-31
If you find no joy you would be best marking this thread as solved and starting a new one for your new issue. It will certainly improve your chances as it has nothing to do with the original thread topic and title. Good luck.

PS: Have you got internet up? If so, perhaps do a full update/upgrade and see if that helps:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	 

These commands will not upgrade your currently installed release to a newer one. If they cough up any errors, please post them on your new thread between code tags (see the last link in my signature). You can link to that thread here if you like. Good luck.

---

### Post by Geoffrey_Arndt on 2015-10-31
The first thing to do after the install completed and a successful nomodeset boot is to get the nvidia driver installed.   Do nothing else until that's done.   Some systems are not stable with only the vesa driver or the wrong nvidia driver installed.   

Did you go through the Ubuntu "additional drivers" process (means _not installing the driver via the nvidia_ site)?    System Settings>Software & Updates>Additional Drivers Tab  . . . . let the ubuntu scan finish on this page, do the install, and restart the system.

---

### Post by mörgæs on 2015-11-01
For a processor of the Haswell family there is only one useable option and that is a fresh install of 15.10. 

15.04 gives mediocre results:
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-HSW-Gfx](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-HSW-Gfx)

and 14.04 should in general only be used for old and semi-old hardware.

---

### Post by Wawrzyn on 2015-11-01
Im sorry for taking so long to reply. I did manage to fix the freezes and boot errors by switching to proprietary nvidia driver. Thank you all again for the answers.

---

