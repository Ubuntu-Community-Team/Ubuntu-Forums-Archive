---
title: "Booting Live CD = no init found error"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by kalebka55 on 2012-01-12
Hi all

My laptop had frozen this afternoon and I had to hit power button to restart.  On restart i get the no init found message.
i.e. 

"No init found. Try passing init= bootarg

Busybox v1.13..........
Enter 'help' for a list of built-in commands"

I have searched the forums and there is a solution to this problem, HOWEVER, all solutions require that I boot from a live CD... The problem is that I get the same message when I restart with the live cd in the tray.  I have tried using 2 types of live CD - the ubuntu 10.04 (my current OS); and the most recent 11.10.  Both CD's give the same error.

I have heard that this may be the initiation of a deteriorating hard-drive.... PLEASE HELP!

---

### Post by kalebka55 on 2012-01-13
I too have tried the USB option, i.e. booting form a live USB... but no luck.  Please help!
I have access to the GRUB terminal but I dot really know what to do from there (if there is anything to do)?  can I somehow use grub to access cdrom/USB, or run terminal?  

Getting desperate....!

EDIT:

apparently GRUB offers no such option....

---

### Post by varunendra on 2012-01-13
> **kalebka55 said:**
> I too have tried the USB option, i.e. booting form a live USB... but no luck.  Please help!
Are you able to boot from USB but can't implement the fix, or is it that you can't boot from the USB as well and get the same error message?

If you are getting the same error and the same way.. then most probably your laptop isn't picking up the CD or usb at all, and is going straight to HDD booting regardless of what you have opted to boot from.

If the CD or USB is able to boot other systems, there is no reason why it should give such an error on the laptop.

---

### Post by kalebka55 on 2012-01-13
> **varunendra said:**
> Are you able to boot from USB but can't implement the fix, or is it that you can't boot from the USB as well and get the same error message?

If you are getting the same error and the same way.. then most probably your laptop isn't picking up the CD or usb at all, and is going straight to HDD booting regardless of what you have opted to boot from.

If the CD or USB is able to boot other systems, there is no reason why it should give such an error on the laptop.


===>  I managed to get  PuppyLinux Live CD to work on this Mac that I am using now.... But it won't pick it up on my laptop...  So seems that yes, the HDD is not picking up the CD.  
Has my HDD crashed completely?

---

### Post by varunendra on 2012-01-13
> **kalebka55 said:**
> ===>  I managed to get  PuppyLinux Live CD to work on this Mac that I am using now.... But it won't pick it up on my laptop...  So seems that yes, the HDD is not picking up the CD.  
Has my HDD crashed completely?
It is not the job of the HDD to pick up or drop a device for booting. It's just a storage device itself, nothing more. It is the BIOS that decides which device to boot from. Even if the HDD is corrupt or completely gone, it should not affect the initial process of booting from another device (eg- cd drive or USB), although the booting may get slow or sometimes completely hung if the HDD is corrupt in a few certain ways.

By your description so far (which needs to be a bit more detailed) it seems the BIOS just skips to the HDD booting, meaning - either it is not detecting the CD/USB, or is set to boot from HDD first. Accordingly, please go into your BIOS and change the boot order to set the CD/USB as First boot device. If it is USB you want to boot from, make sure it is already plugged-in and is detected by the BIOS.

As for the HDD status, look for an option in the BIOS which says something like "Scan (or check) Hard Drive".. Most of the laptop BIOS have this or similar option. You can use this option to scan your hard drive for errors. But whatever the problem is, you DO need to boot from CD/USB to correct it.

---

### Post by kalebka55 on 2012-01-13
Thanks Varunendra,

It is relieving to hear that there is still some hope.  With respect to giving a more detailed explanation.... all that I have said is all there is (to my knowledge).  I had done no upgrades before the stall... or anything such that it would alter the OS in any way.  My open office package had malfunctioned and I decided to restart... During the restart, it stalled.... and I was forced to shutdown manually.   The message in post 1, is literally all I get at start-up.... when I put in a mount command (for the USB), an error message appears relating to  /bin/sh:  
Doing an 'ls /' command lists the directories in the root - But I am unable to do anything constructive (lack of knowledge).
Sudo is also unrecognized  (do these extras help at all?)

I shall try your suggestion regarding BIOS.... I really appreciate your help (after 168 views of this post-and no response).  If you have any questions, I will try to help you in helping me sort this issue out.

---

### Post by kalebka55 on 2012-01-13
Ok... well no good news.

changing the boot order had no effect on start-up.... same message appears. -- (but only for the CDrom at position 1)
resetting default factory setting has no effect on startup.
even the Hard drive system scan failed at 0% completion.

There are new messages on the startup screen relating the USB being disconnected and a new high speed USB device at some address.

(sigh). . .

---

### Post by Miljet on 2012-01-13
I have had great success in using a gparted live CD to repair this problem. Just select your / partition and click on "check for errors".  I don't know how this will help you, however, if you can not get your computer to boot from a CD.

---

### Post by kalebka55 on 2012-01-13
I have browsed several forums and yes, your suggestion is one that seems simplest.  But yes, it wont help if i cant get the cdrom to run....  Thanks for the message though - appreciated!!

---

### Post by varunendra on 2012-01-14
> **kalebka55 said:**
> even the Hard drive system scan failed at 0% completion.
..then it most certainly is a hardware problem. How old is you laptop and what is its model and specs?

If you can (and if the laptop is out-of-warranty), please try to open the case > disconnect the hard drive and retry with CD or USB booting. Alternatively, you can try to disable hard drive in the BIOS if there is any option like that (although I doubt there may be any). Also, are you sure your cd drive is in good enough condition to read and boot from a CD?

If possible, please upload some screenshots of the error messages you get and post their links here. They may be able to give us a better picture.

---

### Post by kalebka55 on 2012-01-14
The laptop is old... a good 5/6 years.  It is an Hp pavillion dv2000.  you can probably get the specs from the net (I have done no hardware changes)
CD drive is in good condition... hardly ever use it.

Screen shots will be difficult....   it will require me to enter them in manually.... if i have time I may consider it.

I will see if I can get the hard drive out and get it checked out.   Seems like it is a HDD malfunction requiring it to be replaced....

Thanks for your help!

---

### Post by varunendra on 2012-01-14
> **kalebka55 said:**
> changing the boot order had no effect on start-up.... same message appears. -- (**but only for the CDrom at position 1**)
The above part of your earlier post makes be suspect that probably your cd drive is too old to be able to read the cd. Hence this may be what is happening: Laptop tries to boot from CD >> detects No CD in the drive or has difficulty reading it >> gives up on it and skips to hdd - giving you same results as when hdd is on top in booting order.

Else, as I said earlier, there should be no problem in booting from CD if the cd is really bootable (i.e., boot fine on any other computer), regardless of hdd status.

But then the USB booting failure remains unexplained. That's why I thought screenshots might give me some clue about it. If you can note down the exact error messages, posting them back would serve the purpose. Here I suspect that it is skipping the USB too for some reason (either the USB is not bootable, or the BIOS is incapable of recognizing it as a bootable device, or the waiting time for USB boot times-out before the USB gets ready)

Accordingly, you may try a few things to determine if it is possible to get it running in its current state:

[LIST=1]
[*]Make sure the USB is bootable (by trying to boot any other computer with it), then retry with it.
[*]Besides setting the USB on top in BIOS boot order, also try to select it from the boot device menu of the BIOS. Usually the hot key to bring up the boot-device menu (to be pressed while the laptop just starts to boot) is F9, but it can also be any of - F8, F10, F11, F12, Esc, Tab, (or who knows what!) depending on the BIOS version. If the USB drive does not show up in the boot-device menu, then most probably the BIOS does not have the capability to boot from USB thumb drives (even some modern computers don't have it!).
[*]Borrow an external CD/DVD drive if you can from somewhere. If it succeeds, you may consider to buy one.
[*]Almost all the computers (even older than yours) have the option to boot from network. Just to get it running to try accessing the hdd from inside an OS, you may try that option. The easiest way I've tried personally is to boot another computer with a [Slax Live CD]("http://www.slax.org/get_slax.php") with "Start as PXE server" option > connect the laptop to it directly with a network cross cable or through a network switch > boot the laptop from LAN (either through boot-device menu, or by setting "boot from LAN" option on top in BIOS boot order). It can't be easier!
[/LIST]
The objective is to get the laptop in running state so that we can see if it can be repaired at software level. If it cannot be, we'll be sure that either you have to get a new hard disk for it, or you are bound to limited boot options like booting with a USB drive.


But in the last, taking it to a nearby repair-shop is the best and easiest option if you can afford it ;)


All the best!

---

### Post by kalebka55 on 2012-01-14
Thank you for your suggestions.  

I will try keep an update going when/if a solution is found....

I will definately mark as solved if that be the case...

Yours gratefully

---

### Post by varunendra on 2012-01-14
You're always welcome!

I wish and hope it gets 'really' solved.

---

### Post by aditya3098 on 2012-01-14
Make sure your computer can boot from a cd.

---

### Post by kalebka55 on 2012-01-14
GREAT NEWS!

I managed to make a bootable USB drive and load the live OS.  Mac works a little differently to other computers.....the reading was exhausting.
 I loaded GParted and checked the root drive..... back to normal!!

In retrospect, I am still puzzled why the CD drive did not work....  actually I am still puzzled with everything that happened....

Thanks varunendra for being by my side all this time....  this community rocks!!!!


Thread SOLVED

---

### Post by Miljet on 2012-01-14
Just for what it is worth, don't be surprised if the same thing happens again. This problem seems to indicate that the hard drive is beginning to fail. The same thing happened to my wife's old desktop computer three times before I gave up and replaced the drive. If you aren't going to replace the drive right now, be sure to keep your data backed up.

---

### Post by varunendra on 2012-01-15
> **kalebka55 said:**
> GREAT NEWS!....
Great News indeed!

However, *Miljet's* suggestion is an important one, especially when it comes with a first hand experience. You should also consider running some disk-surface scanning tools as well as enabling SMART status reporting feature in BIOS if available.

As for the CD drive's failure to boot, my guess is either a weak or totally dead laser-eye (reading lens), or a misconfiguration in boot order (assuming the CD itself is ok - which is another point of concern). Even if the CD is on top in boot order in the BIOS, it sometimes gets skipped if fails to reply immediately when BIOS queries for a bootable CD/DVD. In such a case, you may be able to read CDs when an OS is loaded (due to better drivers and longer waiting time), but any attempt to boot from it will almost always fail.

Anyway, congratulations for the current success, and don't forget to create backups if you already haven't.

---

### Post by kalebka55 on 2012-01-15
> **Miljet said:**
> Just for what it is worth, don't be surprised if the same thing happens again. This problem seems to indicate that the hard drive is beginning to fail. The same thing happened to my wife's old desktop computer three times before I gave up and replaced the drive. If you aren't going to replace the drive right now, be sure to keep your data backed up.

I will without a doubt take your comments seriously.  Backing up will be in progress soon.  I will too research into some new hard drives, or perhaps consider something new.  I will stay with ubuntu either way.
Thanks for keeping check on this thread... 

Best wishes

---

### Post by kalebka55 on 2012-01-15
> **varunendra said:**
> Great News indeed!

However, *Miljet's* suggestion is an important one, especially when it comes with a first hand experience. You should also consider running some disk-surface scanning tools as well as enabling SMART status reporting feature in BIOS if available.

As for the CD drive's failure to boot, my guess is either a weak or totally dead laser-eye (reading lens), or a misconfiguration in boot order (assuming the CD itself is ok - which is another point of concern). Even if the CD is on top in boot order in the BIOS, it sometimes gets skipped if fails to reply immediately when BIOS queries for a bootable CD/DVD. In such a case, you may be able to read CDs when an OS is loaded (due to better drivers and longer waiting time), but any attempt to boot from it will almost always fail.

Anyway, congratulations for the current success, and don't forget to create backups if you already haven't.


Thank you for your notes.  I will look into what you have suggested.  And again, thank you for keeping tabs on the thread and having patience with a mere beginner.

Best wishes!

---

### Post by varunendra on 2012-01-15
Welcome mate! :)

---

