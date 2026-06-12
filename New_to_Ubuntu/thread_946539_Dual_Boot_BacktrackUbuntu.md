---
title: "Dual Boot Backtrack/Ubuntu"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Forgery on 2008-10-13
Hey guys, I'm loooking at dual booting backtrack and ubuntu and just get amazingly confused when it comes to sorting out grub or lilo, I understand I need to use one of the other. I can install ubuntu or backtrack and they both work fine, I just can't get them both to be able to dual boot. 

I have two questions about it mainly

First of all, can I share boot partition, if I can how do I go abotu this

Also, what exactly do i need todo with either grub or lilo.conf to give me the ablility to dual boot either distro from boot.

This has had me stumped for a long time now, it is obviously something I simply do not know about.

Thank you

Forg

---

### Post by caljohnsmith on 2008-10-13
I think Backtrack only has a few boot files that hardly take up any space, so I don't think there would be any good reason to share a /boot partition between Backtrack and Ubuntu. I would use Grub to boot both distros, and then in your Grub's menu.lst you can use something like the following to boot Backtrack I think:
```
title		BackTrack3 (sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 ro vga=773 
```
Of course you'll need to change it for your Backtrack partition. Does Backtrack install its own boot loader? Is it Lilo? If it does, just tell it to install Lilo to the Backtrack partition instead of the HDD's MBR (Master Boot Record) so that it would be easier to boot Backtrack from Grub. 

But first how about posting:
```
sudo fdisk -lu
```
And explain which OS is on which partition, and we can work from there if you want.

---

### Post by Forgery on 2008-10-13
Thanks a lot for the response. I actually bodged up the harddrive last time I tried doing this so I am ready to fresh install both distros again so my partitions can be anything. Whatever is best recommended.

Backtrack does come installed with lilo, don't know how to tell it to install that else where there.

Thanks for your kind response

Forg

---

### Post by caljohnsmith on 2008-10-13
I've never installed Backtrack, so I don't know about how it installs Lilo; at least for Ubuntu, when you get to the final stage of installation, you can click on the "advanced" button and tell Grub to install to say /dev/sda2 instead of /dev/sda or (hd0). Using /dev/sda2 installs Grub to the boot sector of partition sda2, and makes it really easy to boot that partition. Using /dev/sda or (hd0) installs Grub to the MBR of sda. Anyway, if Backtrack gives you any options like that when you install it, tell it to install Lilo to the Backtrack partition boot sector rather than the MBR. That would make it really easy to boot Backtrack. :)

---

### Post by Forgery on 2008-10-13
Thanks again Caljohnsmith. So you suggest I save lilo.conf which is /etc/lilo.conf to /dev/sda2 rather than /dev/sda0?

To install backtrack I am following the commands here hxxp://forums.remote-exploit.org/showthread.php?t=14751 the command that seems to transfer lilo is ```
bt~#cp --preserve -R /{bin,dev,home,pentest,root,usr,etc,lib,opt,sbin,va r} /mnt/backtrack/
``` so I assume I need to work around that maybe?

So If I move lilo then grub will automatically pick up Backtrack?

Finally would it be an option to change the order I install Backtrack and Ubuntu, dunno if that makes things easier but hasn't really been mentioned, maybe one before the other would make things easier.

Thanks again for everything

Forg

---

### Post by caljohnsmith on 2008-10-13
From that tutorial you link to, I see there is no real installer to install Backtrack to your HDD; they instruct you to basically copy the most of the CD file system over to your HDD directly. Also, even if you were able to install Lilo to the partition boot sector, it's not really going to help, because they tell you to manually modify your lilo.conf file anyway for your particular setup. 

So the bottom line is, if I were you, I would follow that tutorial, and once you have Backtrack installed to your HDD, you should be able to use the Grub entry I gave in post #2, but modify the "vga" setting for your monitor; I noticed some other people in that thread you linked to used that same syntax to boot Backtrack from Grub, so it should work. But I don't know how to find the correct "vga" number for your monitor, so I can't help you with that. :)

Let me know how it goes or if you run into problems.

---

### Post by Forgery on 2008-10-13
Ok, So tomorrow I shall take these steps.

Install ubuntu using
sda0 /
sda1 swap space
sda2 free space

Then install Backtrack using sda0 also as the boot partition and storing everything else in sda2

Then finally adding the extra grub information

Will that hopefully put me in the best direction?

Or do I install everything for backtrack in sda2 and tell the grub to point to sda2 when booting backtrack? A little confused about that point

Many Thanks

Forg

---

### Post by caljohnsmith on 2008-10-13
I think you might be confusing Grub's partition numbering with how partitions are numbered for drives in /dev. Your first drive will be sda, and the first partition will be sda1, not sda0. :)

Also, I would recommend not putting Backtrack's boot partition in the main Ubuntu install like you described, because for one thing that could possibly overwrite some of your Ubuntu boot files. That tutorial you linked to also says you can keep the Backtrack /boot directory in the main Backtrack partition, so I don't see any advantage in your case to have it separate. In other words, I would recommend:
```

sda1 = Ubuntu main install mounted on "/"
sda2 = swap space
sda3 = Backtrack install, including the /boot directory
```

---

### Post by Forgery on 2008-10-13
That makes perfect sense, thank you very much. I shall try this in the next day or two and get back to you how it went.

I cannot thank you enough for the amount of help you have given me.

if we ever meet in some very odd and strange occurance, I owe you a pint!

Many Thanks

Forg

---

### Post by Forgery on 2008-10-14
Hey again, good progress is gettind made.

Ubuntu installed and Backtrack installed in /dev/hda5 (logical partition)

I have added the extra lines to the grub the only problem is it is still booting with lilo so I can only select backtrack

How do I get it to boot using grub again?

Many Thanks

Forg

---

### Post by caljohnsmith on 2008-10-14
That's great news you're making progress; to install Grub to your HDD's MBR (Master Boot Record) so you can use Grub rather than Lilo, boot your Live CD, open a terminal (applications > accessories > terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1

```
The above command should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,1), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you run into any problems, please post:
```
sudo fdisk -lu
```
And we can work from there. Otherwise let me know how it goes. :)

---

### Post by WWSmith36 on 2008-10-14
You also might want to edit your /etc/lilo.conf file so that it will not over-write grub.

You should change the line
boot=/dev/hda

to
boot=/dev/hda5

so that lilo will only install on the Backtrack partition rather than the MBR, when up perform kernel updates

---

### Post by Miljet on 2008-10-14
You could have saved yourself a bit of trouble by installing backtrack before installing ubuntu. The last distro that you install will be the boot loader that is installed to the MBR. I have an old computer that is dedicated to trying different distros. Every time I add another one, the MBR gets overwritten by the boot loader of the new distro. You can avoid this by making either a boot floppy (if you have a floppy drive) or a boot CD. A floppy is easier to change.

You can learn everything you ever want to know about GRUB here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
I actually printed it out....all 116 pages, for reference.

---

### Post by Forgery on 2008-10-14
Well... I feel numb... my brain can stop thinking about this problem, which it has been thinking about for about a month. It Works!!!! =D I can now dual boot between the two! Thank you all so much, I have learnt so much from this exercise now I can finally start playing with the Distros rather than keep reinstalling them all the time! Yay! I'm so happy!

Thank you everybody for all of your help!

Much Love
Forg

---

