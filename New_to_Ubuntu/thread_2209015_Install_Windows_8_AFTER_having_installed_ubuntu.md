---
title: "Install Windows 8 AFTER having installed ubuntu"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by joel17 on 2014-03-03
Long story short: I bought a computer without an OS. I installed ubuntu. I couldn't access any internet with it, neither ethernet nor wireless. So I bought Windows 8.1, full price, and now I apparently can't install it.

I am asked "Where do you want to install Windows", but I can't go any further because I get the message "Windows must be installed to a partition formatted as NTFS". 

I would really appreciate your help. It would make my day, but please remember that I know very little about computers, so I would do better with a step-by-step approach.

This whole debacle has cost me over a month's salary (yes, I live in a country with very low wages), so this has really been a sobering experience.

---

### Post by zircon_34 on 2014-03-03
Please give more specifications (Ubuntu distro, computer hardware, network card), so people can try to help you fix it. 

If I were you, since the price of Windows 8.1 is worth so much in your country, I would fix Ubuntu and resell windows, to my opinion its not worth it! Especially, that in windows you have to pay for most of the software you are going to use...

---

### Post by joel17 on 2014-03-03
Ubuntu 12.04, computer is a Lenovo G500, not sure what network card

---

### Post by grahammechanical on 2014-03-03
You need to do what it says. Some months ago I a downloaded a free to download, time limited, developer preview version of Windows 8. I have a few installs of Ubuntu on the hard disk.

I use Gparted in a Ubuntu Live session to move things around to create a large enough space at the beginning of the hard disk for a partition to install Windows 8 in. I then created the partiton but did not format it.

I then used the Windows 8 install session to format that partition to NTFS and then the Windows 8 installer had no problems installing Windows 8 into the chosen partition. It will let you chose partitions.

Be aware, the Windows 8 installer will put a Windows boot loader into the MBR. This means that you will lose access to Ubuntu unless you use a Ubuntu live session to run

```
sudo update-grub
sudo grub-install /dev/sda
```

I am assuming that there is only one hard disk in the machine. For your information, the Windows 8 installer will format that disk for you.

As for myself, I first installed Ubuntu on a machine that I built myself back in 2007 and I never had any problem getting Internet access through the ethernet or wireless adapters.

It should also be possible to access the Internet using the Ubuntu live session. I have done this myself when visiting my sister. I was able to use a live session on her laptop to access this web site.

I hope that Windows 8 will give you Internet access.

Regards.

---

### Post by joel17 on 2014-03-03
Windows 8.1 installer does not let me format the partition to NTFS. I wish it did. Is there any other way?

---

### Post by Mark Phelps on 2014-03-03
If you format an existing partition to NTFS you will lose whatever is in that partition.

You need to have an unallocated space such that the Win8 installer will then format that to NTFS and install.

---

### Post by monkeybrain20122 on 2014-03-03
You still haven't told us what your ethernet and wifi cards are.
Open the terminal and type
```
lshw -C network
```
and post the output.

BTW it is a lot cheaper to get a usb wifi card than to buy Windows if you can't get your laptop's internet to work, many cheap ones work very well with Linux. :)

---

### Post by oldfred on 2014-03-03
If it is a new computer, you probably have the UEFI or BIOS choice. 
And both Windows and Ubuntu will install in either mode, but both really should be the same mode.
And how you boot install media is how it installs. But once a drive is partitioned, you then must be consistent in how you boot & install.
Windows only boots from a drive formatted with gpt partitioning in UEFI mode.
Both Windows and Ubuntu only boot from a drive with MBR(msdos) partitioning with BIOS boot mode.

But Windows requires specific partitions depending on boot mode.
In BIOS it has to boot from a primary NTFS formatted partition with the boot flag.
With UEFI it needs to be able or have several partitions. efi, reserved & main install.

Post this from Ubuntu live installer.
sudo parted -l

---

### Post by joel17 on 2014-03-03
I fixed the problem by using GPARTED to switch to NTFS and cleaning the disk.

---

### Post by monkeybrain20122 on 2014-03-03
Well that is not really fixing the problem. I bet your internet would work with a closed source driver and failing that you can get a cheap dongle. I don't know why everyone here just focuses on "how to get Windows running" except for zircon_34 who makes a lot of sense.

---

### Post by newb85 on 2014-03-03
> **monkeybrain20122 said:**
> Well that is not really fixing the problem. I bet your internet would work with a closed source driver and failing that you can get a cheap dongle. I don't know why everyone here just focuses on "how to get Windows running" except for zircon_34 who makes a lot of sense.

While I share your desire to help the OP to get Ubuntu working, there is something to be said for answering the OP's actual request.

---

