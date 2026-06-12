---
title: "Windows 7 and the Raring Ring Tail"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by Julian_Kirsch on 2013-08-23
Hi,
I am a abolute beginner with Linux. I even don't have installed Ubuntu yet.
Still I am asking.

Well, 6 weeks ago, my shiny new Gamer PC arrived. It had no OS on it yet and I was always curious in Linux so I decided to
install Ubuntu. Everything was fine at the beginning. Loaded Ubuntu 13 on my USB-Stick, installed Ubuntu and bootet up.
That's where the problems begin to appear. I've set up an Account with a Name and Password. When I am trying to log in, my Keyboard seems not to react. It's a new (USB-) Keyboard from Speedlink. It just didn't react. First I thought my Keyboard was broken, to clarify the situation I switched to UEFI-Bootmenu. There it seems be fine.
I tried around several thing, nothing seemed to work then I remembered I had an old USB-to-SP2 adapter. I linked everything and the keyboard worked again.
But this wasn't the end of my problem on top of that Ubuntu refused to work with my USB Wifi Doongle.
Within the time I was pissed off. Grabbed an Windows 8 ( Trial ), <3 Windows.
Everything worked.
Everything would have been fine if I had have an Windows License, but had none.

2 weeks ago my uncle gave me an Win 7 Home Basic Key ( unused, yey! ).
I thought, I'll install Win 7 anyway ( and format the driver ! ), I could give Linux a second try.
I googled around, have been reading through posts, found that USB Keyboard problems may be related to my Mainboard.
The problem could be solved by turning IOMMU in UEFI to Enabled.

I didn't try it yet because the lack of time I had.

Well, my problem is, that I am afraid to face some problems  like this and I'd like to ask some several questions:
- Does Ubuntu 13.04 ( 64-Bit ) work with my Samsung Galaxy Ace GT-S5839i ( e.g. would Tethering work without any additional software like it does in Win 8 ).
- Can I install Ubuntu on a Win 7 Partition. ( My Partition plan looks like this:
    1 Hard Drvier, 1 TB.
    64 GB Win 7
    64 GB Application for Win 7
    64 GB Ubuntu 13 
    64 GB Application for Ubuntu
    256 GB Media 
    128 GB Dev ( I'm developing in C++ and Python, games ect. )
    Rest -> Additional Space
    ). Can  I set the partitions in Windows and install Ubuntu right away in one of these? ( Ubuntu will be installed after Win 7 ! )

- Are there any known hardware issues with my Hardware?
My full hardware specs are:

**[B]AMD FX-Series FX-8320 Prozessor (8 x 3.50 GHz) ** @ up to 8 x 3.9 GHz

[/B]** 8192 MB DDR3 Corsair XMS 3 **[B]

1000 GB HDD  SATA III 

[/B][B][B][B]2048 MB AMD Radeon&#8482; HD 7850 HIS IceQ X Turbo

 
[/B][/B][/B][B][B]Gigabyte GA-970A-UD3 Mainboard

[/B][/B]My this I want to say while the installation process I'll have hardly acces to internet. I can access the internet ( then ) only with my Moms Comp.

I hope you understand what I am about and you can help me with my questions.

Thanks July

---

### Post by rai_shu2 on 2013-08-23
First of all, the Samsung GT thing is an Android device, and getting Ubuntu to work on those things is still in the experimental stage. Plus, with your RAM (384 MB), I highly doubt you'll get Ubuntu working the way you want (though Lubuntu might work out fine in that environment).

Secondly, if you're going to custom partition, don't forget to set up a UEFI partition (at least 200 MBs). Otherwise, GRUB won't work. I would suggest you install Windows, then install Ubuntu and then maybe sort out the issues with your Wifi hardware (probably need a special driver or a configuration to get that to work right).

---

### Post by 3rdalbum on 2013-08-23
1. Yes, file access and tethering should work out-of-the-box.

2. Operating systems must be stored on Primary partitions, not Logical partitions. Put your Windows system and Ubuntu system as the first two partitions.

You can't install programs to a separate partition on Ubuntu. Not sure why you would do this on Windows either. Just like in real life, the more partitions you have, the more space you lose.

You can do your partitioning in Windows or Ubuntu, your choice. The Ubuntu partition needs to be ext4, not NTFS, but the Ubuntu installer can reformat an NTFS partition to ext4. 

3. Basically sounds okay, but you will have to try it to know for sure. Try running Ubuntu from the CD before installing. You can check tethering too.

4. Having no internet connection is not a problem during the installation phase, but it's easier if you do have one. You can click a button during installation to download codecs and media support in the installer, which of course requires an internet connection. These things can be added afterward but you might as well add them in the installer. You can use your phone tethering for this, just don't tick the "Get updates" box because this will download a lot of data!

---

