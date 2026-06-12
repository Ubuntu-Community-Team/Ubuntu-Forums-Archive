---
title: "Dual-booting problem, Win7/Natty"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by AnylaWhere on 2012-02-11
Hi. I posted this over in the other support section, but the answer went /way/ over my head. So I guess I'm a lot more of a beginner than I realised.

I bought a Sony Vaio C series last week, running the Windows 7 I need for my classes. But for personal  use I tried to install the 11.04 that I've got on my  old desktop, a dual-boot.
I've done this before on my sisters' computers and installed it completely on my desktop, with no problems, so I  was unprepared for everything that's gone wrong in the first week of  owning this thing.

*A note in case it's relevant:*
I flubbed the install the first time (something called a server instead of the actual Ubuntu...interface?) and had to wipe the computer back  to factory setting mode, for which I had to install Lilo. But then I  restored it and tried Ubuntu a second time once Windows was back and running.

And at the first bootup after that Ubuntu was working  perfectly. But immediately after, it stopped working altogether.

**What happens:**
When I boot up, I get the purple screen asking me which OS I want to  use. But it doesn't have that countdown that'll choose the one selected automatically.
I can load Windows 7 just fine every time, do whatever I want on it  (I'm on it now). But every time I choose Ubuntu, it sits on the blinking underscore for awhile and then blanks out to a  completely dead screen--not black, dead as if it's shut down. My computer is still on, flashy  keyboard lit up and all, but nothing will make the display work, and no matter  how long I leave it be it never gets anywhere or loads anything.

I've tried rebooting and retrying multiple times over multiple days, been up at nights looking  for solutions, and even uninstalled, reinstalled, and replaced the  Ubuntu portion more than once, each time after which it will work once, and when I  reboot it, nothing again.

My face right now rather resembles this: :confused:

Any help would be seriously awesome.
Thanks!

---

### Post by clausrei on 2012-02-11
I read, that there was a problem with Window 7 because the OS don't allow anymore a second OS running on the same HDD or computer. This might be your basic problem you are facing.

If I am right, I am sure this problem occurred already and there must be a fix to it. 

Did you try this: Often, especially with an early Vista or Windows7, it is better to shrink the Windows partition from inside Windows.  Have a look at this:   [https://help.ubuntu.com/community/DualBoot/WindowsFirst](https://help.ubuntu.com/community/DualBoot/WindowsFirst) 
  

Good luck !

---

### Post by Mark Phelps on 2012-02-12
> **clausrei said:**
> I read, that there was a problem with Window 7 because the OS don't allow anymore a second OS running on the same HDD or computer. This might be your basic problem you are facing.

What you read was totally wrong!!

You're talking about OEM-provided Windows 8 (that's EIGHT) running ARM processors...

Which has absolutely nothing to do with Windows 7 and multi-boot.

---

### Post by Mark Phelps on 2012-02-12
To the OP:

Let's get a luck at what's on your drive.  Boot from an Ubuntu desktop CD, select the Try Ubuntu option, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive.

---

### Post by AnylaWhere on 2012-02-13
Thank you for responding! Okay, I finally got a chance to run the disk between classes. This is what it's telling me when I put the code in:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5405971

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    35274751    17636352   27  Unknown
/dev/sda2   *    35274752    35479551      102400    7  HPFS/NTFS
/dev/sda3        35479552   347849098   156184773+   7  HPFS/NTFS
/dev/sda4       347850750   625141759   138645505    5  Extended
/dev/sda5       616939520   625141759     4101120   82  Linux swap / Solaris
/dev/sda6       347850752   608733183   130441216   83  Linux
/dev/sda7       608735232   616927231     4096000   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oldfred on 2012-02-14
Other than an extra swap partition, partition table looks ok.

If you can boot Windows and start to boot Ubuntu, grub2's boot loader must be installed ok. So then it may be a video card/chip issue.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by AnylaWhere on 2012-02-14
Would an extra swap partition do anything weird to the computer?

I'm looking through the threads you linked, and it looks like there's several different options in each one.
I'm certainly able to do all of that, but I'm apparently too much a beginner to know what it all means; is there any particular option I should start with? If I just go for it, will I mess anything up/be able to undo it?

---

### Post by oldfred on 2012-02-14
Extra swap will not cause any issues. System may or may not be using both. You would have to check fstab to see what is used.

I would always try nomodeset first but what works best may depend on what video you are using.

---

### Post by AnylaWhere on 2012-02-14
[SIZE=2]Thanks! How do I check fstab to see what is used? Or do I need to?

On the first thread for nomodeset, [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
which option of the three would be best to try first?
[/SIZE][SIZE=2][B]-How to enable kernel options on the livecd (before install)
-How to temporarily set kernel boot options on an installed OS (not wubi)
-How to permanently set kernel boot options on an installed OS (not wubi)
[/B][/SIZE]

---

### Post by oldfred on 2012-02-14
Have you installed, if not you need the liveCD instructions.

Then you test different choices with the boot changes. 

Only after you find if nomodeset or other settings are required should you make setting permanent.

---

### Post by AnylaWhere on 2012-02-17
Alright, I tried the nomodeset setting temporarily. The line I'm supposed to modify didn't end with "quiet splash"; it had something else after the quiet splash. But I put the nomodeset at the end of the line anyhow after the extra text and it seemed to boot alright.

When I logged in, though, it popped up a message that said I didn't have the hardware to run Unity, and to choose Ubuntu Classic. And then loaded a different setup for Ubuntu than I've seen before, with an "Applications," "Places," "System," and Firefox logo across the top bar, instead of a line of launch bar down the left side of the screen. Is this part of nomodeset or is it something I should be worried about?

---

### Post by oldfred on 2012-02-18
I do not know what the hardware requirements are for Unity. 

I am still running 10.10, so I have the old style gnome2 classic gui. When I installed the newer versions to test with Unity I try it for a while and then install the fallback which is somewhat like the gnome2 classi version. That must be what you have gotten?

---

### Post by AnylaWhere on 2012-02-18
Well at least Ubuntu is working again, even if it looks different.
Thank you!

---

