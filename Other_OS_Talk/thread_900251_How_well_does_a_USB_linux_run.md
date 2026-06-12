---
title: "How well does a USB linux run?"
date: 2008-08-25
forum: Other OS Talk
---

### Post by Fzang on 2008-08-25
I'm thinking about installing linux to my USB (from windows, possible..?)

...But I was wondering how sluggish a full GUI distro would be on a 4 GB USB, because the live CD is preeeetty slow.... or is that just because CDs are oooooold?

---

### Post by Dougie187 on 2008-08-25
From what I hear running from a USB drive is pretty speedy. And the slowness is due to the whole cd crap.

---

### Post by wannadumpwindows on 2008-08-25
I've done it with a few of mine. I can tell you it doesn't boot any faster than a CD in my experience. It is a little faster once you're logged in.

But don't expect anything crazy.

It also depends on what distro you're using, some will be faster than others.

---

### Post by Dougie187 on 2008-08-25
True. I haven't done it myself, and the person who was feeding me this information might have been running DSL.

---

### Post by Fzang on 2008-08-25
I was thinking about something with e17 as window manager, heard it should use very little resources

Oh, and of course the distro should have decent hardware support... can't have a USB that only fits on a single computer >_>

Halp meh!

---

### Post by prshah on 2008-08-25
> **Fzang said:**
> I'm thinking about installing linux to my USB (from windows, possible..?)

...But I was wondering how sluggish a full GUI distro would be on a 4 GB USB,

Yes, you can install from Windows, see [www.pendrivelinux.com](www.pendrivelinux.com) for a comprehensive series of guides.

I run both Xubuntu and DSL from pen drives; DSL is great, since it just loads itself entirely to RAM from the beginning.

Xubuntu is _very_ slow to start (bootup process), but relatively snappy during use (after login).

---

### Post by rokytnji on 2008-08-25
I just recently downloaded and burned a live cd of OzOS .5 i386 with EI7 Elive Desktop from Linux Cafe. It picked up my internal wireless intel chip from bootup and is based on Ubuntu. Ihaven't any distros installed on USB so I can't be of any help there. Gotta   
say it is a speedy Ubuntu alternative.

---

### Post by Fzang on 2008-08-25
Last things before I venture into my project:

1. A guide for this sorta thing...? Is there a specific good site or do I just google and cross fingers?

2. I just saw another topic like this, and the guy said that he had used... 2 GB!?!? for the.... GRUB!? Does a bootloader need 2 GB!?

---

### Post by prshah on 2008-08-25
> **Fzang said:**
> 

1. A guide for this sorta thing...? Is there a specific good site or do I just google and cross fingers?

2. I just saw another topic like this, and the guy said that he had used... 2 GB!?!? for the.... GRUB!? Does a bootloader need 2 GB!?

1. [www.pendrivelinux.com](www.pendrivelinux.com)

2. No. You need under 800Mb for Xubuntu; a little more if you want persistance.

---

### Post by Fzang on 2008-08-25
Hmm... What about swap space? I heard it should be like 5 times your RAM or something...

---

### Post by prshah on 2008-08-25
> **Fzang said:**
> Hmm... What about swap space? I heard it should be like 5 times your RAM or something...

Nope, you've heard wrong. Swap is required only if you have less than 512Mb RAM, and in some cases, not even then.

Typically, you should have 1.1 times your RAM as swap if you plan to use hibernation; otherwise:

a) If you have 512Mb or less RAM: Give Swap of at least 512Mb ~ 1 Gb
b) If you have 1Gb or more: Swap of about 512Mb is OK

In no case should you have zero swap (excepting live CDs/live USBs). Even live distros will detect, use and benefit if swap is available; but they will run without swap if enough RAM is available.

---

### Post by Fzang on 2008-08-25
Alright, another question I just thought of...

Can I put my USB linux to sleep/hibernate mode without somehow disconnecting the USB when starting up the computer again?

---

### Post by Pogeymanz on 2008-08-25
Do not make a swap partition on your usb device.

Flash drives such as those on usb sticks wear out more quickly than an old-school hard drive. If you need to use swap space, then you will be writing to the device frequently and it will wear out that part of the drive very quickly.

You probably wont need swap space anyway.

I usually recommend Puppy Linux for USB sticks. You can load the whole thing into RAM and it usually boots very quickly, even on older hardware.

---

### Post by wannadumpwindows on 2008-08-26
I have 2 4 Gb Kingston DataTravelers. I had OS's installed on both. One had swap space, the other didn't.

The one with swap was dead in 2 months.

It could've been a bad drive, but I never had any problems with it. So I'm led to believe that it was the swap that killed it, but it's up to you.

---

### Post by prshah on 2008-08-26
> **Fzang said:**
> 
Can I put my USB linux to sleep/hibernate mode without somehow disconnecting the USB when starting up the computer again?

Yes, theoretically, you can; but you must remember that if the USB stick is not plugged in _before_ powering up the computer, then grub _might_ shift hdd numbers around.

However, as other posters have noted; you probably should _not_ to put swap on your usb pen device. You can put swap on the (fixed) hard disk drive, and then hibernate your usb linux. Is putting swap on the pen device harmful? I'm not certain; the logic is quite correct and I subscribe to it; but then Windows Vista uses something called ReadyBoost that is similar (but not exactly the same) as swap. Linux uses swap as "extra memory" for sleeping processes; Windows Vista uses ReadyBoost as a caching technology, where frequently used data is cached to the pendrive so that main memory can be freed up. Again, I don't know if this will kill pen devices; I suspect it will, but I am not sure.

And personally, it will be a minor miracle to get hibernate/resume working properly in such a setup, and it will break easily; so in my opinion, it too much trouble and should not be attempted.

Once again: avoid this hibernation issue; it will not help bootup time any. If you hibernate on one machine and then try to resume on another, even with the same amount of memory it may not work.

---

### Post by zmjjmz on 2008-08-26
There is a [guide](https://help.ubuntu.com/community/Installation/FromUSBStick#Automatic Approaches) for putting Ubuntu (and subsequent derivatives, I believe) on a flash drive, but you'll need to use the LiveCD (once).
Chances are you could try that with OzOS, it's not very different.

---

