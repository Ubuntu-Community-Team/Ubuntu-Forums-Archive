---
title: "Booting laptop using Ubuntu flash drive without having hard drive"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by amolshende on 2011-09-16
Can I run Ubuntu from a flash drive without having hard drive in my laptop.
I have live USB of Ubuntu. My hard drive is toasted & so I thought i will be able to boot my laptop using usb flash drive. But it is not happening!! After clicking on "Run Ubuntu", it is giving I/O error.(My guess it is trying to red or wrtire some thing on my unresponsive hard drive)
 
So is there a way to disable my hard drive?? I don't want to dissassemble laptop & take it out, that i'll do when i'll recive my new hard drive. Any other way?...or do you want me to try any other version of Linux who can boot my laptop without accessing hard drive??

---

### Post by hyper2hottie on 2011-09-16
I'm not sure if what your trying to do is possible.  

If you go into your bios you should be able to dissable the drive though.  Make sure your booting from the usb first as well.

---

### Post by SavageWolf on 2011-09-16
This should be possible, though you may need to remove your HDD from your bios, it might be causing problems.

I assume you have gone through the correct steps to make it correctly, if so then check the MD5 sum thing.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Rex Bouwense on 2011-09-16
If you set your lap top to boot first from the flash drive in the BIOS then it will not even look to the hard drive.  However, unless you enabled persistent files on the flash drive when you created it, anything that you do to it will be discarded when you exit.

---

### Post by technosysind on 2011-09-16
disable your HD through bios settings and then boot using your usb drive. It should work

---

### Post by anewguy on 2011-09-16
I agree with disabling it in the BIOS, if possible. You may even need to disable the controller in the BIOS to get it to disable the drive.

If you can't disable it in the BIOS, about your only other choice is to take the hard drive out - this should be a simple process in a modern laptop - and then perhaps just putting the empty caddy back in so nothing can get in the slot while you are running.

Dave ;)

---

### Post by seawolf167 on 2011-09-16
As posted above - first disable the SATA (assuming) port that your hard drive is connected to in BIOS, then re-try to boot off the USB. I assume you made a bootable USB with something like [UNetbootin]("http://unetbootin.sourceforge.net/")?

> **amolshende said:**
> I don't want to dissassemble laptop & take it out, that i'll do when i'll recive my new hard drive.

This should be very easy - there should be 2 or 4 screws holding a little cover in place, just remove those screws, slide out the hard drive and you're done.

---

### Post by DogMatix on 2011-09-16
I have booted from a USB when my PC would not boot & it turned out the HDD had failed. So, yes it can be done.

---

### Post by jockyburns on 2011-09-16
My HDD packed in about 4 weeks ago. I waited almost a week on a new one being delivered. Meanwhile I downloaded Ubuntu 11.04 to a usb stick, (on a different computer ;-)) set the bios boot settings to usb first and Ubuntu ran off the usb stick, full access to the interwebthingymajig and once I'd set it up, email too. (although the usb stick probably didn't have enough room to continue downloading emails for very long) So I can't see why your lappy shouldn't run Ubuntu straight off the usb stick.;);););)

---

### Post by anewguy on 2011-09-17
I think it depends on the exact type of failure the hard disk is having.  Obviously, many of us have booted from USB when we either had a bad drive, no drive or didn't want to boot the drive.  There must be something different about the type of failure the drive is having.

Dave ;)

---

### Post by wildmanne39 on 2011-09-17
Hi, if you can not use ubuntu live usb then you may have a memory problem because the live usb does not touch your hard drive it loads everything into memory.
Thank you

---

### Post by haqking on 2011-09-17
> **wildmanne39 said:**
> Hi, if you can not use ubuntu live usb then you may have a memory problem because the live usb does not touch your hard drive it loads everything into memory.
Thank you

+1

I just removed the HDD from my other laptop and booted to USB fine

---

### Post by anewguy on 2011-09-17
I'm just wondering if, some where down in the initial recognition of the hardware, it detects the drive and just tries to "verify" by reading a block - if the read is failing that could cause the error.  It could be in at a low enough level that it's deceiving.

I've also boot laptops and desktops from USB, both with or without hard drives, both with and without a bad disk drive.  I also never had any problem.  But.....I can see where a hardware error at a low enough level in the detection process could cause a failure.

Dave ;)

---

### Post by oldfred on 2011-09-17
There are a few BIOS that check drive partitions for boot flag before letting you boot. I have seen this with Intel motherboards, not sure if any others.

They seem to assume Windows as grub or grub2 do not need a boot flag. I usually just recommend a boot flag on one primary partition if I do not know what BIOS is used.

---

### Post by anewguy on 2011-09-17
That's the type of thing I was thinking about - it happens at a level that is low enough.  The seek may be failing or the read failing, which would result in the type of problem being talked about.

Thanks, oldfred!

BTW - best of luck on your Ubuntu Membership!

Dave ;)

---

### Post by djarrell on 2013-02-23
> **amolshende said:**
> Can I run Ubuntu from a flash drive without having hard drive in my laptop.
I have live USB of Ubuntu. My hard drive is toasted & so I thought i will be able to boot my laptop using usb flash drive. But it is not happening!! After clicking on "Run Ubuntu", it is giving I/O error.(My guess it is trying to red or wrtire some thing on my unresponsive hard drive)
 
So is there a way to disable my hard drive?? I don't want to dissassemble laptop & take it out, that i'll do when i'll recive my new hard drive. Any other way?...or do you want me to try any other version of Linux who can boot my laptop without accessing hard drive??

You can disable your hdd thru bios usually delete at post. and you can boot windows from a bootable  flashdrive  but you cannot save any work or games. just look up how to make a bootable flashdrive. it should work on ubuntu if it works on xp.
good luck

---

### Post by overdrank on 2013-02-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

