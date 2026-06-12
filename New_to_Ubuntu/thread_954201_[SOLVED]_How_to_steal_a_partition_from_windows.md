---
title: "[SOLVED] How to steal a partition from windows?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Prabakar on 2008-10-20
Hi everyone,
   I have installed Ubuntu 8.04 few weeks back and I find myself using Ubuntu more than Win XP. So, I want to give one more partition to Linux:) but I don't know how to:( Currently windows has assigned F: to the partition I want to use for Ubuntu. Please tell me, how to get this partition for Ubuntu. I have backed up the data to another partition so, no worries about data loss.

* I don't want to corrupt Windows XP cause I have lots of games that don't work in Linux:biggrin:

---

### Post by bpowell2005 on 2008-10-21
> **Prabakar said:**
> Hi everyone,
   I have installed Ubuntu 8.04 few weeks back and I find myself using Ubuntu more than Win XP. So, I want to give one more partition to Linux:) but I don't know how to:( Currently windows has assigned F: to the partition I want to use for Ubuntu. Please tell me, how to get this partition for Ubuntu. I have backed up the data to another partition so, no worries about data loss.

* I don't want to corrupt Windows XP cause I have lots of games that don't work in Linux:biggrin:

You need to tell us what the topography of your drives looks like. Drive F: is just a partition of your main drive? Can you do a "sudo fdisk -l (that's a lower-case "L")"...this will tell us How Ubuntu sees your drive structured...from there, tell us which device is your F: drive, and we'll be able to tell you how to mount it in Ubuntu. You won't need to "seal" it from Windows, you can mount it, use it, and SHARE it with Windows; even better!

---

### Post by epidemiks on 2008-10-21
Re: How to steal a partition from windows?

Break the Windows, jump in and grab it. Then run!

Sorry, couldn't resist. :)
Follow bpowell2005's advice and we'll be able to help you automatically mount that partition

---

### Post by kansasnoob on 2008-10-21
I'm too tired to give a detailed response, but to begin with you need to know how Linux identifies partitions.

You can forget about partitions being C, F, etc.

This is a great place to expand your knowledge:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I normally run a drive with Windows and two Linux operating systems, but just to give you a sneak peak here's my simple 30 GBG test drive with two linux OS"s:

[ATTACH]89080[/ATTACH]

That's Gparted which you'll need to use to accomplish what you want - not something to go about willy-nilly!

---

### Post by Prabakar on 2008-10-21
Thanks for your reply.

I got this when I used that command.

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x184f184e

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021        4815    30483337+   f  W95 Ext'd (LBA)
/dev/sda4            4816        4870      441787+  82  Linux swap / Solaris
/dev/sda5            1021        2295    10241406    7  HPFS/NTFS
/dev/sda6            2296        3570    10241406    7  HPFS/NTFS
/dev/sda7            3571        4207     5116671    7  HPFS/NTFS
/dev/sda8            4208        4815     4883728+  83  Linux

```
I want to use /dev/sda7. 
And can I add files to the drive while in Ubuntu if I share it with Windows?. If so I like to share all of them. But right now if I try to mount them I get this error

```
Error org.freedesktop.DBus.Error.AccessDenied.
```

And I have just about 1 GB free in sda8. With meger resources I find it hard to get enough space. I am not sure if sharing is the right solution. I want to give 10 GB to Ubuntu then I need not worry about space while Installing new software.

---

### Post by Finalx on 2008-10-21
> **kansasnoob said:**
> I'm too tired to give a detailed response, but to begin with you need to know how Linux identifies partitions.

You can forget about partitions being C, F, etc.

This is a great place to expand your knowledge:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I normally run a drive with Windows and two Linux operating systems, but just to give you a sneak peak here's my simple 30 GBG test drive with two linux OS"s:

[ATTACH]89080[/ATTACH]

That's Gparted which you'll need to use to accomplish what you want - not something to go about willy-nilly!

Is 30GB enough?I give it 80GB because I'm new to ubuntu and I don't know what's the justification size..

here is my partions:Is that proper?

/dev/sda6              24G  2.9G   21G  13% /
varrun                887M  100K  887M   1% /var/run
varlock               887M     0  887M   0% /var/lock
udev                  887M   68K  887M   1% /dev
devshm                887M   12K  887M   1% /dev/shm
lrm                   887M   39M  848M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/sda7             183M   41M  133M  24% /boot
/dev/sda10             51G   15G   34G  31% /home
/dev/sda9             9.3G  617M  8.2G   7% /var
gvfs-fuse-daemon       24G  2.9G   21G  13% /home/finalx/.gvfs

and I don't know what is the last line:confused:

---

### Post by epidemiks on 2008-10-21
> **Finalx said:**
> Is 30GB enough?I give it 80GB because I'm new to ubuntu and I don't know what's the justification size..

here is my partions:Is that proper?

/dev/sda6              24G  2.9G   21G  13% /
varrun                887M  100K  887M   1% /var/run
varlock               887M     0  887M   0% /var/lock
udev                  887M   68K  887M   1% /dev
devshm                887M   12K  887M   1% /dev/shm
lrm                   887M   39M  848M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/sda7             183M   41M  133M  24% /boot
/dev/sda10             51G   15G   34G  31% /home
/dev/sda9             9.3G  617M  8.2G   7% /var
gvfs-fuse-daemon       24G  2.9G   21G  13% /home/finalx/.gvfs

and I don't know what is the last line:confused:

You shouldn't need to resize or change any partitions if you intend on keeping windows while dual booting with ubuntu.
All you need to do is tell ubuntu to mount the drives you want access to.
From a terminal, run ```
sudo apt-get install ntfs-3g
```

This will give you a control panel which will let you automaticall mount (show) your other hard drives, and whatever partitions you already have. These will then show up in you're file managager and give you full access to read and write to those partitions.

---

### Post by Prabakar on 2008-10-21
@kansasnoob

Thanks for your advice. I have downloaded GParted as you said. Now I'll try to add sda7 after backing up the data stored.

---

### Post by hyper_ch on 2008-10-21
when posting file or command output put the text into [noparse]```

```[/noparse] brackets to make it easier to read.

---

### Post by Prabakar on 2008-10-21
I have converted the partition to FAT32. And it is now available for both Windows and Linux. Problem Solved.

---

