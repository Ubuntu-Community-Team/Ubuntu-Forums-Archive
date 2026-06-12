---
title: "Tried to Alter Boot Priority ~ Now Can't Boot At All"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by Andavane on 2012-07-15
Machine = Lenovo Thinkpad X201i.
Dual-booted Windows 7 from bootable USB
History Ubuntu 11.04 > 11.10 > 12.04 (following upgrade path in each case)
               Evverything going well.
Last week acquired another Thinkpad X-121E with AMD E300 Dual Core Processor
and am in process of setting up dual-boot on that one.
 
Before proceeding my plan was to use my GParted-Live 0.4.8-6 USB stick to boot into my first Thinkpad X201i to look at the arrangement, to familiarise myself with what I did.

I was surprised that it continued to Windows & didn't load GParted, so I went into The BIOS to change the boot order and after doing this I now am unable to boot into anything! The bootloader was GRUB so I suspect I have somehow damaged it.

I have learned NOT to go into the BIOS late in the day when tired. I have learned a lot of things and would really appreciate some help as to how to get back on my feet after this stumble.

I've attached some snaps of the current BIOS arrangement and eagerly await and help, any advice, any anything!

Regards, John

---

### Post by Shadius on 2012-07-15
Have you tried changing the boot order to boot from CD/DVD first, then HDD? 

**To simplify**:

1: CD/DVD
2: USB
3: HDD

Since you're trying to boot into GParted using a USB, the USB should be before the HDD. Also, what happens when you try to boot into the operating system? Do you get any type of screen? Anything at all?

---

### Post by mapes12 on 2012-07-15
Looks like GRUB is messed up. Try this:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Andavane on 2012-07-15
> **Shadius said:**
> Have you tried changing the boot order to boot from CD/DVD first, then HDD? 

**To simplify**:

1: CD/DVD
2: USB
3: HDD

Since you're trying to boot into GParted using a USB, the USB should be before the HDD. Also, what happens when you try to boot into the operating system? Do you get any type of screen? Anything at all?

thank you. The wording in the BIOS doesn't say quite the same, I get ie I changed it to:

1. USB CD
2: USB FDD:
3. ATA HDD1:

>"Do you get any type of screen? Anything at all?" I am getting a black screen with a cursor winking on the top left. That's it.

I'll try booting from that GParted usb stick again though, except, i wonder if it's and old version of GParted that somehow caused this?

>"When you break a lot of things, you learn a lot of things."
Sure, mate. This seems to be one helluva break. Hope I AM learning something (or other)....

> **mapes12 said:**
> Looks like GRUB is messed up. Try this:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That would be good, but it seems my entire machine is doomed!

---

### Post by Steve619 on 2012-07-15
After way too many years my desires (finances) convinced me that I needed to give up my addiction to MS. With support running out for my XP sp3 and seeing a better way with open source to get away from MathCAD, SolidWorks, Mathamatica, Corel, etc ect.
   
  I put together a relatively good box with a GigaByte MB and a dual core 3.6 GB Pentium 4. Two cheep 500 GB Seagate sata HD&#8217;s, and my ATI FireGL L7100 video board. Installed all my Windows stuff on the 1st drive and it worked fine across two 1920x1200 monitors.
   
  Fortunately, I backed up the whole thing with Paragon (free backup and recovery) on to a 32 GB USB stick and all my data on an external USB Drive.
   
  I thought I could keep my windows stuff running if I loaded Ubuntu into a VirtualBox in XP but that was horrible and I recovered back to the working XP.
   
  So, I pre-partitioned my second HD for a Ubuntu installation and burned a bootable installation CD. Everything went fine and I fully loaded all the default to a full installation. Then I faced the dreaded GRUB monster.
   
  When I tried to restart, I caught a glimpse of  GRUB during the boot load, XP started to load then crashed and burned. Got stuck in a loop of rebooting. So, I recovered (Paragon) my XP drive and XP was fine. (No GRUB) But I couldn&#8217;t boot to Ubuntu,
   
  Finally, I noticed that the boot order in the BIOS advanced options gave the choices: CD/DVD, USB, HDD, ect. But only in the secondary menu did it let me choose WHICH HHD to try first. I choose my second drive and it booted to Unbuntu drive complete with the GRUB menu that gives me all the choices including booting to XP. Solved for me and now I love the GRUB.

---

### Post by Shadius on 2012-07-15
> **Andavane said:**
> thank you. The wording in the BIOS doesn't say quite the same, I get ie I changed it to:

1. USB CD
2: USB FDD:
3. ATA HDD1:

>"Do you get any type of screen? Anything at all?" I am getting a black screen with a cursor winking on the top left. That's it.

I'll try booting from that GParted usb stick again though, except, i wonder if it's and old version of GParted that somehow caused this?

>"When you break a lot of things, you learn a lot of things."
Sure, mate. This seems to be one helluva break. Hope I AM learning something (or other)....



That would be good, but it seems my entire machine is doomed!

You might try getting the latest version of GParted since I believe yours isn't the latest. Also, set your BIOS Boot Order like this:

1. USB CD
2. ATA HDD0
3. USB FDD

Then try to boot into GParted (the lastest release) or an Ubuntu 12.04 LiveCD. We'll try to get back your operating systems before we do anything with GParted.

---

### Post by Andavane on 2012-07-16
> **Shadius said:**
> You might try getting the latest version of GParted since I believe yours isn't the latest. Also, set your BIOS Boot Order like this:

1. USB CD
2. ATA HDD0
3. USB FDD

Then try to boot into GParted (the lastest release) or an Ubuntu 12.04 LiveCD. We'll try to get back your operating systems before we do anything with GParted.

OK mate, great we have a Plan!
Next step is getting latest GParted on another machine (I feel it may be that older version which skewed things. 

Only other thing to mention is there's no CD on this machine as I made a bootable USB.

I also have an external CD drive on my list of things to get, but at present am not sure which is a good choice for this machine. Please say if you have suggestions about this.

Getting back on this....

We live in hope! :)

Kind regards

John

---

### Post by Shadius on 2012-07-16
> **Andavane said:**
> OK mate, great we have a Plan!
Next step is getting latest GParted on another machine (I feel it may be that older version which skewed things. 

Only other thing to mention is there's no CD on this machine as I made a bootable USB.

I also have an external CD drive on my list of things to get, but at present am not sure which is a good choice for this machine. Please say if you have suggestions about this.

Getting back on this....

We live in hope! :)

Kind regards

John

Since you have no CD/DVD drive on the system, we'll use a LiveUSB then. Do you have an Ubuntu 12.04 LiveUSB?

---

### Post by oldfred on 2012-07-16
If you do not have a CD, do not make it first in BIOS boot order. It just slows booting.

My desktop system has many USB choices and at first I could not get it to boot my USB flash drive no matter what USB choice I used. I tested flash on laptop and it worked, so I knew it was good. One day in choosing boot drive I had flash plugged in and it was a choice under hard drives. Many BIOS see flash drives as a hard drive not a USB device.

I prefer to leave boot order in BIOS set to hard drive and use one time boot key (f12 on my system) to choose to boot other devices on occassion.

---

### Post by Andavane on 2012-07-16
**_STOP PRESS: VITAL INFO AT END OF THIS POST!_**

> **Shadius said:**
> You might try getting the latest version of GParted since I believe yours isn't the latest. Also, set your BIOS Boot Order like this:

1. USB CD
2. ATA HDD0
3. USB FDD

Then try to boot into GParted (the lastest release) or an Ubuntu 12.04 LiveCD. We'll try to get back your operating systems before we do anything with GParted.

Yes Sir, I have 12.04 in 64-bit and also the 32 bit i386 disc.
In the machine which won't boot, it started as 11.04, and has stepped up to 12.04 through following upgrade paths. So I'll set the boot order as you suggest then insert the 64-bit usb stick before pressing F10 to see what happens there.

For some reason I got the attached message when trying to make a GParted. (Attach shot)

I'll try again tomorrow when things are fresh"

> **Steve619 said:**
> After way too many years my desires (finances) convinced me that I needed to give up my addiction to MS. With support running out for my XP sp3 and seeing a better way with open source to get away from MathCAD, SolidWorks, Mathamatica, Corel, etc ect.
   
  I put together a relatively good box with a GigaByte MB ...XP was fine. (No GRUB) But I couldn&#8217;t boot to Ubuntu,
   
  Finally, I noticed that the boot order in the BIOS advanced options gave the choices: CD/DVD, USB, HDD, ect. But only in the secondary menu did it let me choose WHICH HHD to try first. I choose my second drive and it booted to Unbuntu drive complete with the GRUB menu that gives me all the choices including booting to XP. Solved for me and now I love the GRUB.
   Steve, I didn't see any secondary menus in this BIOS. Am logging ur story though, very interesting.

> **oldfred said:**
> If you do not have a CD, do not make it first in BIOS boot order. It just slows booting.

My desktop system has many USB choices and at first I could not get it to boot my USB flash drive no matter what USB choice I used. I tested flash on laptop and it worked, so I knew it was good. One day in choosing boot drive I had flash plugged in and it was a choice under hard drives. Many BIOS see flash drives as a hard drive not a USB device.

I prefer to leave boot order in BIOS set to hard drive and use one time boot key (f12 on my system) to choose to boot other devices on occassion.

Fred, I am now stunned and amazed! I press F12 at the beginning and got the attached shot. 
Or rather this is the shot my  care giver took with his phone. But honestly, I am a bit confused as to what happened next. I THINK I pressed enter and it dropped down with that minus sign there. When happened next must have flashed gthe BIOS in my brain because I was staggered to see the boot menu GRUB all come upo and it all went merrily away as if nothing had happened. I am eternally grateful, and relieved beyond words. Thanks for all the help in this thread.

Now before I mark this thread as solved I'd really appreciate understanding a bit more about what happened, as for me, SOLVED means solved and understood.

Thanks again, while I let it sink in with a cuppa!  [IMG]http://smileys.on-my-web.com/repository/Drinks/drinking-45.gif[/IMG]

--John

PS: Of course I hope it'll boot again!

---

### Post by Andavane on 2012-07-17
Gentlemen (includes Ladies):

I have arrived at the boot order in which the machine boots perfectly into the GRUB and I select either Ubuntu or Windows, and attached the shot shown below.

I have learned so much from this thread and want to take the opportunity to thank everybody with their help. 

My admiration and love of Ubuntu has grown apace!

Kind regards,

John

---

### Post by Shadius on 2012-07-17
Congratulations! It was fixed by changing the boot order so that the HDD was first?

---

### Post by Andavane on 2012-07-17
> **Shadius said:**
> Congratulations! It was fixed by changing the boot order so that the HDD was first?

Yes. the one that says ATA HDD0
There are other ATA's there. I guess it might be an idea to get a rough idea of what ATA is, instead of being afraid of seeing it.

The valuable thing to know here is the F12 key which gives a one-time option to make the 1st boot of your choice :)

Really useful to know.

---

### Post by Shadius on 2012-07-17
> **Andavane said:**
> Yes. the one that says ATA HDD0
There are other ATA's there. I guess it might be an idea to get a rough idea of what ATA is, instead of being afraid of seeing it.

The valuable thing to know here is the F12 key which gives a one-time option to make the 1st boot of your choice :)

Really useful to know.

Glad you understand how to solve it now. Yes, it might be worthwhile to know a little bit of what ATA is. Here's a link for you: [ATA]("http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1")

---

