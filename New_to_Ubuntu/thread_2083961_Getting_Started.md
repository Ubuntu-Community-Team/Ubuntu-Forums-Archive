---
title: "Getting Started"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by RussellXPD on 2012-11-14
Hi
I've been browsing the site to gain as much info as possible before asking a question. I've concentrated on the Absolute Beginners' section because that's what I am.

I came from How-To-Geek with the idea that I could install Ubuntu 12.0.4 on a memory drive.  I'm running XP with 2Gb of memory and so far I've installed the 685 Mb download with wubi.exe and Casper onto the memory drive.

The question I want to ask, and I'm sure this is the wrong place to ask it, is, how can I boot from the 4Gb (Integral) drive?

When I go into BIOS I can make Removable Drive the first option but when I then boot, the system ignores this and restarts XP.

---

### Post by nothingspecial on 2012-11-14
*Thread moved to **Absolute Beginners Section**.*

---

### Post by blade4 on 2012-11-14
Use Unetbootin . It will create a bootable usb for you . Its freeware and the steps are self-explanatory . 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Cheers

---

### Post by Lars Noodén on 2012-11-14
> **blade4 said:**
> Use Unetbootin . It will create a bootable usb for you . Its freeware and the steps are self-explanatory . 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Cheers

It is not 'freeware' but instead it is [Free software](http://unetbootin.sourceforge.net/#credits), a subset of Open Source.  There's a world of difference.

But yes, it is a good tool to create a bootable USB stick.

---

### Post by mastablasta on 2012-11-14
another good windows tool is Linux Live USB. 
 
in any case you need to first verify that donwloaded image is exactly the same as the one on the server. here is how you do it: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
after you verified it is the same you use the software previously mentioned to create a bootable USB stick.
 
note that 
- not all USB sticks are recognised by USB as bootable drives
- it is good to preformat the stick (this will erase all data on it) to FAT32. often this type of USB live creating software will do this for you.
 
nice instructions with pics.: [http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)
 
if USB is not recognised as bootable disk you can use floppy or CD usign PLOP boot manager to make it bootable. i use it on old maschine with floppy, so i can try different version using same USB instead of burning new CD every time i want to try something.
 
and speaking of trying virtual box can also boto live image. you just point it to the image and it will boot. no need to live windows. but with 2GB you would be limited to about 512MB RAM in vbox. still it's an option: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by RussellXPD on 2012-11-16
Thanks, fellows.

I've not been able to work on this for the last few hours but will follow up all your suggestions and report back. 

What I did meanwhile was apply this to my Windows7 machine, created a pen version of 12.0.4 and successfully booted that PC with it.

On two successive reboots I had a few problems, but I don't expect an easy ride and I'm prepared to fiddle until I understand what's going on.

I'll try again on XP and let you know how it  goes.

Russell

---

### Post by MG&amp;TL on 2012-11-16
> **RussellXPD said:**
> Thanks, fellows.

I've not been able to work on this for the last few hours but will follow up all your suggestions and report back. 

What I did meanwhile was apply this to my Windows7 machine, created a pen version of 12.0.4 and successfully booted that PC with it.

On two successive reboots I had a few problems, but I don't expect an easy ride and I'm prepared to fiddle until I understand what's going on.

I'll try again on XP and let you know how it  goes.

Russell

Post about these problems-they're probably resolvable. :)

---

### Post by RussellXPD on 2012-11-20
Following your suggestions I checked the stages I've been through and I came upon this first question.

I've downloaded Ubuntu 12.0.4 to a 4Gb disk and now have no initial difficulty in starting the OS up on my Windows 7 machine. With the memory stick inserted I'm offered the choice of W7 or Ubuntu, I select Ubuntu and I'm off.  [Problems in actually using the OS come later but I'll find out a lot of those answers without help.]

I conclude from this that the download on the stick (685Mb) is the complete package to run the program.  

I have downloaded **UNetbootin-windows-581.exe**, 4.90 Mb and it's sitting on the desktop of the Windows XP PC.  I've looked at the instructions on the Sourceforge site about Unetbootin, and what worries me is that if I make any changes to the contents of the stick that I won't be able to continue to boot on the Windows 7 machine. 

Do I need an ISO file if the stick works on at least one computer?

I'd appreciate your advice and thanks for the comments so far.

Russell

---

### Post by MG&amp;TL on 2012-11-20
I'm not entirely sure what you've done- the normal situation is that if the stick is booted from, it boots straight into a menu that just has ubuntu options on it (blue and white), and if not, boots into windows if you haven't installed and ubuntu/windows if you have.
 
Simple trial: remove the stick and see what happens. You can always reinsert the stick if you need to.

---

### Post by Bucky Ball on 2012-11-20
Welcome to the forums. If you have created the stick and it is booting Ubuntu fine then you don't really need Unetbootin any more. You've done what you were going to use it for.

[QUOTE=RussellXPD]... I don't expect an easy ride and I'm prepared to fiddle until I understand what's going on.[/QUOTE]

Good and right attitude! Enjoy the learning curve and the OS. ;)

---

### Post by RussellXPD on 2012-11-20
I'm inclined to mark this thread as solved.

I needed Ubuntu on one machine, and I've got it. It's set up so that I can easily log in to either Ubuntu 12.0.4 or W7. I will be able to explore, get used to some unfamiliar terms and tackle the fact that I can't get it on the XP machine, as a task for a later time. 

As to that, I've just tried the XP set up again. The system ignores the memory stick in all cases. When I changed boot order, that made no difference either.
I could try again with a different memory stick, but I should probably leave it.

(The main benefit of doing it would be if I could find out what the obstacle was so I could report back.)

If one of the Forum staff concurs, I'll do that.

Russell

---

### Post by MG&amp;TL on 2012-11-20
You might want to try a CD/DVD on the XP machine. One of my older machines has been known to be dubious when booting from a USB.

Also, you might want to try a lighter derivative like Xubuntu or Lubuntu on the XP machine...the graphical richness Ubuntu has doesn't always play nice with older hardware.

---

### Post by Bucky Ball on 2012-11-20
If you feel your original problem is solved, I would mark it that way and post a separate thread regarding the XP machine with descriptive title.

Good luck. ;)

PS: You can also mark a 'Solved' thread 'Unsolved' if you decide it's not solved after all ...

---

### Post by RussellXPD on 2012-11-21
Some good tips there, MG&TL. I did set off earlier with a rewritable DVD disc but got stalled when it relayed a string of sector errors. At some point I'll start over with a fresh DVD.   I'll bear in mind what you say about Xubuntu and Lubuntu. The XP machine is 6 years old but it generally sails well in the high seas.

I'll mark the thread as solved and treat the XP problem as a Part Two. Thanks to all.

Russell

---

### Post by Bucky Ball on 2012-11-21
> **RussellXPD said:**
> The XP machine is 6 years old but it generally sails well in the high seas.

See you on the next thread, RusselXPD, but just as a preliminary to that and endnote to this; I also have a nine year old desktop with a P4 and 1Gb of RAM which dual-boots XP and a complete hybridised mishmash of Ubuntu faultlessly. There is hope!!!

---

