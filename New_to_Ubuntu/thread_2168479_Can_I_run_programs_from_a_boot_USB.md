---
title: "Can I run programs from a boot USB?"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by geronl on 2013-08-18
My laptop has Ubuntu 12.04 and I am very happy with it. Extremely. I have a 4GB USB and I have made it into a boot USB with Ubuntu 13.04.

My question is, if I now install Windows on my HDD and use the USB when I want to use Linux, can I run programs like Open Shot and Scrivener (sort of a Word processor that helps with story/book/script writing - linux beta free until end of this year or next or something) off the USB? How would I go about doing that, wouldn't they be "zipped" on the USB?

---

### Post by carl4926 on 2013-08-18
Are you saying you plan to remove 12.04 when you install winders?
And you want to make a persistent USB of 13.04?

---

### Post by carl4926 on 2013-08-18
Just FYI
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by geronl on 2013-08-18
I'll take a look

---

### Post by geronl on 2013-08-18
My eyes are glazed over. How about a never mind. lol ;)

---

### Post by geronl on 2013-08-18
OK... how about partitioning the hdd? Can I do that and not lose the data I have?

---

### Post by geronl on 2013-08-18
Never mind that too. I am not going through what I just read about. It's too complicated for me and if I mess up, its all over.

---

### Post by carl4926 on 2013-08-18
> **geronl said:**
> Never mind that too. I am not going through what I just read about. It's too complicated for me and if I mess up, its all over.
Are you sure installing windows isn't too much for your little grey cells?

---

### Post by geronl on 2013-08-18
I have have a partition apparently, the second one is called "Linux Swap" or something but appears to be empty.

Do I have to go into the BIOS and reformat the main HDD partition for Windows? Why wouldn't the Windows installation disc do that automatically?

---

### Post by geronl on 2013-08-18
Will Windows recognize a partition I make with GParted? Or will it just overwrite the whole thing when it reformats?

---

### Post by geronl on 2013-08-18
> **carl4926 said:**
> Are you sure installing windows isn't too much for your little grey cells?

I was referring to the partitioning.

---

### Post by carl4926 on 2013-08-18
State clearly what you need to achieve and add with it supporting information about your current partitioning.

But: You can create partition/s (NTFS) for windows with Gparted and windows will recognise them. 
It's more a question of what your partition layout is now and if the above is possible.
Your data in Ubuntu would be overwritten if you just let windows use the entire HD, obviously.
Windows needs a NTFS or FAT primary for it's boot code, otherwise it can be installed as an OS in a Logical Partition.

I suggest you take a screenshot of your HD in Gparted and post it here

---

### Post by r_avital on 2013-08-18
> **geronl said:**
> My laptop has Ubuntu 12.04 and I am very happy with it. Extremely. I have a 4GB USB and I have made it into a boot USB with Ubuntu 13.04.

My question is, if I now install Windows on my HDD and use the USB when I want to use Linux, can I run programs like Open Shot and Scrivener (sort of a Word processor that helps with story/book/script writing - linux beta free until end of this year or next or something) off the USB? How would I go about doing that, wouldn't they be "zipped" on the USB?

geronl,

I'm looking at your first post above, and then at the whole thread after that, and it seems to go in different directions all at once.  So let me see if I understand correctly what you're trying to do:

1. You have Ubuntu 12.04 on your HDD and you want to keep it there, correct?
2. You want to install Windows on the same HDD alongside Ubuntu 12.04 and dual-boot, correct?
3. You have Ubuntu 13.04 on a USB drive, and you would like to use it to create and save files in Ubuntu 13.04, without interfering at all with anything you have on the HDD, correct?

If any of the above is not correct, please let us know.  We'll have a better idea of how to assist you.

IF 1, 2, 3 above are correct, this means that in order to run Ubuntu 13.04 from your USB, you will need to:

1. Make a working installation of Ubuntu 13.04 on your USB, and,
2. Restart your computer and boot from the USB every time you want to use it.

If that's what you want to do, then to make a working installation of Ubuntu 13.04 on your USB, follow the steps on this post:
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It talks about Lubuntu, but I've reviewed the steps on that post carefully, and there's no reason it should not work with Ubuntu 13.04 just as well.  In fact, I've done it.

You will need to burn an image of Ubuntu 13.04 to a CD before you start, and be aware that anything you have on the USB will be lost, because it will hold a new working installation of Ubuntu 13.04

This is necessary, because when you say "the USB" it's not clear what you mean or how that was created -- Did you use "Startup Disk Creator" to put Ubuntu 13.04 on that USB?  Is it a USB stick, or a USB HDD?  See, we need to have more precise info to go further.

As far as installing Windows on your HDD, if you make an NTFS partition on your HDD with gparted, and it's large enough for the requirements of your version of Windows, then when you start the installation of Windows, it should find it, recognize it, and ask you permission to install on it.

Let us know.

---

