---
title: "Ubuntu install without CD or USB stick"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by jminor2 on 2015-02-03
I just bought a brand new Dell Latitude e7450 and want to install Ubuntu.  Can you download and install Ubuntu directly to the machine without first burning a CD or USB stick?  I want to wipe Windows off the hard drive and just run with Ubuntu.
Thanks,
John

---

### Post by Bucky Ball on 2015-02-03
Welcome. The answer [here]("http://askubuntu.com/questions/340156/install-ubuntu-from-iso-image-directly-from-hard-disk-of-a-system-running-linux") might get you started. Search around a bit more for 'install ubuntu from iso' and no doubt you'll find more clues. There is also the netboot install option, but never used that myself. Might do what you're after. [This]("https://help.ubuntu.com/community/Installation/Netboot") will give you some background.

I'm guessing you have no disk or USB stick to install from? Easier if you did. Good luck. ;)

---

### Post by yancek on 2015-02-04
> Can you download and install Ubuntu directly to the machine without first burning a CD or USB stick?

You can download the iso but in order to install it you will nee to boot it in some fashion.  An Ubuntu iso file can be booted directly and used to install to another partition IF, you have the Grub2 bootloader installed.  This is explained in the first link posted above.  The second link posted seems to require a CD at some point but I've never used that method either.

If all you have to work with is the windows bootloader, good luck!

---

### Post by jminor2 on 2015-02-04
Here's what I've done so far.  I downloaded Rufus to create a bootable USB drive, then downloaded Ubuntu 14.04.  When the download was complete, I used Rufus to create a bootable USB drive with the 14.04 iso.  I did this on my Lenovo T530 last night.  Today My Dell Latitude e7450 was delivered.  I fired up the Dell and went through the initial Windows setup, then shut down.  I inserted the USB drive and re started the Dell.  When the Dell logo appeared, I pressed the <f2> key, then the <f12> to bring up the boot menu.  The left side had the boot options, HDD, USB, DVD, and HHI (or something like that) with all the check boxes checked.  I turned off all the boxes except USB. The right side had a box where you could change the boot order.  I left that unchanged. I clicked on apply, then exit.  The machine ran for a few minutes with a blank screen, then a blinking cursor appeared in the upper left corner.  From here nothing happened.  I pressed the <f12> key and the boot menu returned.  This time I changed the boot order to show USB first.  Then clicked apply and exit with the same results.  I don't know what I'm doing wrong.  
Any help would be greatly appreciated.
Thanks,
john

---

### Post by yancek on 2015-02-04
When I boot a flash drive, I need to go to the HD options there and will see the name of the various drives, Seagate, Toshiba, Sandisk or whatever.  I would look for the drive name somewhere under HDD or USB or the boot priority section.  I'm not using a Dell so I don't know what different options you will have.

---

### Post by jminor2 on 2015-02-04
Well, I figured it out.  Just had to click on the <12> when the Dell logo appeared and it brought me to a one time boot menu.  From there it was an eazy peazy :-D quick install.  Everything seems to be working great.  I guess clicking on the <f2> screwed things up....
thanks again for the replies to my questions...
John

---

### Post by JeQhdMD on 2015-02-05
I'm just curious.   Did your new Dell come with UEFI/GPT partioning versus standard BIOS?  If so, can you briefly describe your install method and process (e.g., did you need to do anything related to using a boot repair tool, are you using the standard Grub2 to manage the OS loading)?

   Perhaps the Dell is just more Linux friendly (than Toshiba or HP for example) and other forum readers can benefit from an "easy-peazy" install on new laptop hardware (instead of the opposite which we see too often on these boards).

---

### Post by jminor2 on 2015-02-09
> **JeQhdMD said:**
> I'm just curious.   Did your new Dell come with UEFI/GPT partioning versus standard BIOS?  If so, can you briefly describe your install method and process (e.g., did you need to do anything related to using a boot repair tool, are you using the standard Grub2 to manage the OS loading)?

   Perhaps the Dell is just more Linux friendly (than Toshiba or HP for example) and other forum readers can benefit from an "easy-peazy" install on new laptop hardware (instead of the opposite which we see too often on these boards).

First let me say I have no experience with Linux at all, just wanted to give it a try and support the open source community.

Once I created the bootable USB stick as mentioned above, I started the machine, when the Dell logo appeared I clicked on the f12 key and the one time boot menu appeared.  I selected boot form USB and it opened the Ubuntu desktop.  On the upper left side of the screen I had the option to try Ubuntu from the USB or Install.  I clicked on install and it installed without any input from me.  I had it wipe Widowns from the machine as I have another laptop to run Wisdows and wanted this to be exclusivly a Linux machine.  

Later this week I'm going to start the "Introduction to Linux with Ubuntu 14 Desktop" at Linux Academy, to begin the learning process on how to get the best out of Linux....
I hope this helps a bit.
John

---

### Post by oldrocker99 on 2015-02-09
A lot of getting used to Linux is just to play around with it a bit, keeping in mind that anything you do as sudo (root) can, and will, bork your system if you don't know exactly what you're doing. 

Not that that should scare you. I have been using Ubuntu for seven years this April, and these forums are the very best place to get questions answered, still, for myself. You'll find, after a bit of time and usage, that Ubuntu, or any other Linux distribution, is a **BIG** upgrade from Windows, for the **freedom** that Linux gives you, and for the loss of the little, or big, Windows annoyances. I had been dual-booting, strictly to play Windows games, until last year, when some big AAA games (CIV V, Borderlands 2, X-COM:Enemy Unknown, The Witcher 2, Empire:Total War) made their way onto Steam for Linux. I deep-sixed my Windows partition, and haven't looked back.

---

