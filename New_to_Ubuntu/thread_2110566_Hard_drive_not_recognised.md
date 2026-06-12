---
title: "Hard drive not recognised"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by mogsareus on 2013-01-30
Hi,
I have been trying to install Ubuntu on a Dell Inspiron 5150.
The machine had Windows XP on it which I don't want together with Registry Mechanic which just wouldn't die. I therefore used Darik's boot and Nuke on the whole hard drive. This has removed XP and registry mechanic. However when I try and install Ubuntu from a CD everything goes well (if it's not connected to the Internet - it locks up then) until I have to re boot to use the system. The machine doesn't seem to recognise the hard drive (no arrow by it in set up). I assume I need to 'mount' the hard drive, but I can't get a usable terminal to input commands.
Ubuntu 11.10 and 12.10 discs used. 
Pentium 2.66ghz processor, 512mb cache and 1280mb system memory
Any advice would be welcome.
Please note, I am definitely a beginner! 
Regards

Simon DENHAM

---

### Post by Mark Phelps on 2013-01-30
I would first boot from the CD to see why internet access is not being provided.  You will need that during the install as the CD can't possibly contain all the possible drivers and will use the Linux repos to obtain what it needs.

When the desktop comes up, choose the Try Ubuntu option.

---

### Post by Impavidus on 2013-01-31
Do you have a wired or a wireless connection? Wired connections (nearly) always work, wireless often needs extra drivers.

---

### Post by d4m1r on 2013-01-31
No, you should not have to "mount" your harddrive...It should automatically detected by both your BIOS and OS.

1) Does your BIOS detect the drive?

2) Have you tried installing Ubuntu 12.04?

---

### Post by mogsareus on 2013-01-31
Many thanks for your replies. 

I was trying to be brief in my initial description of the problem, and in doing so have miss-lead you, apologies.

If I connect to the Internet and Install Ubuntu everything goes as it should until downloads are sought. The machine tells me that it is getting updates, but sits for hours with no progress being made in the installation - according to the progress indicator at the bottom of the screen.

The Internet connection is wired.

I have tried both Install and Try Ubuntu on a number of occasions. I disconnected the Internet to see if it would just do a basic install. It does this but then when the reboot is required nothing happens. Trying to install again tells me that Unbutu is on the hard drive.

I don't think the hard drive is detected by the BIOS as it doesn't have an > next to it.  
If I move the hard drive to the top of the boot list the wording turns red. If I select it it turns yellow.

Esc gives the message no bootable devices., without a CD in the drive.

I did try the DELL drivers and utilities disc and at the first attempt  got into Ubuntu, but since then putting that disc in hasn't done  anything except run tests on the machine. (which it passes)

I should be grateful for any further advice.

Regards

Simon DENHAM

---

### Post by Mark Phelps on 2013-01-31
Sorry, but some of your comments are confusing.  You say you can install Ubuntu and it goes fine until updates are needed -- clearly indicating that not only can Ubuntu "see" your hard drive, but it can also write to it.

As to moving your drive to the "top of the list", I'm presuming you mean in the BIOS screen, right?  Typically, BIOS screens have two lists of devices, the first being the boot order, the second being the order of hard disks (if you have more than one).  To install and then boot using Ubuntu, the drive you install to has to be at the top of BOTH lists.

As to updates hanging, you should try installing with the updates option turned off.

Then, when you reboot, if you get to a desktop, see if you can browse using Firefox. If you can, then you are getting an Internet connection OK.

If, when you reboot, you only get the screen with the dots and don't get a desktop, or if you only get a black screen, you need to tell us that as different solutions are then needed.

---

### Post by mogsareus on 2013-01-31
Hi Mark,

Many thanks for your reply.

The grey cells are a bit tired at this time of night but will research your advice tomorrow - I admit I was not aware there were two lists to alter  - this may account for the red type??

Regards

Simon DENHAM

---

### Post by Mark Phelps on 2013-01-31
There are only two lists if you have more than one physical hard drive in your system.  The boot order list selects the order of devices to examine for the presence of boot code.  The drive order list sequences the drives from "first" to "last".

Lets say you have a CD/DVD drive and two hard drives.

Then, you want to select Hard Drive as first in the boot order list (or, if you like to boot from CD/DVD, you leave that as first and leave the drive empty when you aren't using it -- it will jump to the next item in the list if the drive is empty).

And, lets say the "second" drive is the one with the boot code on it.  Then, you want to move it to the top of the drive order list.

If you only have one physical drive, it is always at the top of the drive order list.  Nothing to change.

---

### Post by mogsareus on 2013-02-01
Thanks for your message Mark.

The machine is a Dell 5150 laptop with one hard drive.

I altered the BIOS  boot order to put  the CD/DVD drive at the top to clean the hard drive with Darik's boot and nuke.

If I now restore the boot order manually the list shows 

Internal HDD first in white print.
CD/DVD drive IN RED PRINT prefixed with an arrow head
Diskette drive IN RED PRINT  prefixed with an arrow head
USB storage device in white print
CArdbus NIC - white print
Onboard NIC in white print

Nothing changes when trying to restore the BIOS defaults using Dell's instructions f9 and f10.

Escaping from setup  gives the message No bootable devices.

Inserting Ubuntu disc gives welcome to GRUB and the opportunity to install or try Ubuntu, using either option doesn't give a bootable system from the hard drive.

Regards

Simon DENHAM

---

### Post by mogsareus on 2013-02-03
Tried removing battery for 48hrs to see if this improved the BIOS information. It doesn't.
Tried installing Ubuntu 10.10 - this worked and allowed me to open a terminal before rebooting.
Tried re installing grub. Result
Unable to open - 
/user/sbin/grub-probe: error: cannot find a device for /boot/grub (is dev mounted?).

Advice appreciated.

Simon DENHAM

---

