---
title: "Question on External HDD"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by ssanjaychandra on 2013-12-21
Hi guys ,

I want to migrate to Linux from Windows.I am planning to install Linux 12.xx LTS.


1.I have two external HDDs in NTFS format , Will they work with Ubuntu ? Are there any new specific formats for linux ? I generally use them for Media purposes connecting them to my TV or PC.
2.Will my Galaxy Phone be recognized and can be used for read/write just like in Windows ? (i.e MTP and PTP)

After searching in google and some forums , I find myself in confusion with no clear answer.

Can someone please guide me ? 

Don't know if this is the right forum to ask this question.

Thanks

---

### Post by sudodus on 2013-12-21
Welcome to the Ubuntu Forums :-)

0.1 Please specify your computer! It makes it easier to give relevant advice.

- Brand name and model
- CPU
- RAM (size)
- Graphics card/chip
- Wifi card/chip

0.2 Please ***backup*** the system you have now or at least all you personal data, because editing partitions and installing operating systems is risky. If something goes wrong, you might destroy your data. Back it up to an external drive that you disconnect afterwards, or backup to a cloud service.

1. The HDDs will probably work. How are they connected?

- USB 2, USB 3 or eSATA

But you cannot run Ubuntu from NTFS (unless you make some special installation), so you need to edit the partitions (erase or shrink the NTFS partition) and create

- a partition with ext4 (the root partition) of at least 8 GB, but at least 20 GB is recommended.
- a swap partition with at least the same size as the RAM (in GiBibytes) if you want to hibernate. Otherwise it is enough with 1 GB.

Run gparted from another device (typically a CD/DVD/USB drive with a live Ubuntu system, the install drive).

[COLOR=#696969]2. I don't know. Let us wait for a reply about the Galaxy phone from someone else.[/COLOR]

---

### Post by 3rdalbum on 2013-12-21
> **ssanjaychandra said:**
> 
1.I have two external HDDs in NTFS format , Will they work with Ubuntu ? Are there any new specific formats for linux ? I generally use them for Media purposes connecting them to my TV or PC.

Your external NTFS hard disks will be able to be used in Ubuntu. Writing data to them will be a bit slower than Windows because of the NTFS filesystem. I don't know exactly what you mean by "new specific formats for Linux" - Linux installs to an Ext4 filesystem (it can create this when it installs) but you can work with disks formatted as NTFS, Ext3, Ext4, btfs, Fat32, or even exFAT.

> 2.Will my Galaxy Phone be recognized and can be used for read/write just like in Windows ? (i.e MTP and PTP)

It depends which Galaxy it is. If it runs Android 2.3 or below, it will work with any version of Ubuntu. If it runs Android 4 or above, it will only be directly readable and writable on Ubuntu 13.04 or above; I suggest you should install Ubuntu 13.10 now so you'll have access to your phone, and then upgrade to 14.04 LTS when it comes out.

I know some people tell newcomers not to use non-LTS versions, describing them as "beta", but it's not true. I'm on 13.04 right now and it's rock solid; my father's on 13.10 and he finds it very stable too. LTS just means "it will get bugfixes for years".

Ubuntu 12.04 was a good release but it's getting a bit long-in-the-tooth, since it came out halfway through last year. With Linux, unlike Windows, the pace of development is very fast and it's a much better idea to keep fairly recent in terms of distro version. At least when you're looking at ordinary desktop or laptop use.

---

### Post by ssanjaychandra on 2013-12-21
Thanks for the replies.

I will go with 13.10 (because phone runs on 4.3)

---

### Post by Topsiho on 2013-12-21
13.10 will only be supported for 9 months, from October this year.
12.04 will be supported until April 2015 (3 years, from April 2012)

The next LTS version (14.04) will be supported for 5 years, but of course is not released yet.

The choice is up to you :)

Topsiho

---

### Post by walterorlin on 2013-12-21
12.04 was not a long term support relase and 14.04 relased next April will be as well. If you wnated to install to the external hard drives for some reason they you would have to format them as ext4.

---

### Post by ssanjaychandra on 2013-12-21
Nah , external hard drives are only for files.

OS will be installed in my PC hard drive.

---

### Post by Topsiho on 2013-12-22
"12.04 was not a long term support relase":

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

It appears even to be supported until 2017

Topsiho

---

### Post by efflandt on 2013-12-22
I have not gotten MTP or PTP to work properly in 12.04. It does work in 13.10 with my S3, although, I cannot open files on the phone, I have to copy them over to my computer first.

For 12.04 I use ConnectBot, or SSHServer, or AndFTP (which can do sftp) phone apps to sftp or scp files over WiFi either way.

---

### Post by ssanjaychandra on 2013-12-22
I finally installed Ubuntu (64-bit) and got everything working.As of Now , I am using Dual boot alongside Windows 8.0.

Had some problem with Audio Drivers , I was able to solve them after hunting through some forums.Looks like Ubuntu has its own share of issues with HDMI audio and ATI out-of-the-box.

Only disappoint I have is the lack of iTunes because I don't rely much on cloud , So I maintain a local iTunes library on my PC for my iPad.

I have no choice but to keep Windows alongside for the sake of iTunes.

EDIT : I will get a new PC maybe next year or 2015 , Performance with Ubuntu is decent with my current PC.
Its Core 2 Quad + 4GB DDR3 RAM + ATI HD 4670 512MB

I am thinking of adding 2GB RAM , Is it benefitial ?

---

### Post by sudodus on 2013-12-22
I'm glad most things work for you now :-)

I'm happy with 4 GB, but it depends what programs you want to run and how you run them. You can check with ***System Monitor*** or ***htop*** (in a terminal window) how much memory is used, and if the computer starts swapping. If there is very little swapping, and there is usually free memory, you need not increase the RAM.

```
sudo apt-get install htop
``` to install it and ```
htop
``` to run it.

Finally, when you feel satisfied with this thread, please click on **Thread Tools** at the top of this window an mark this thread as SOLVED.

---

