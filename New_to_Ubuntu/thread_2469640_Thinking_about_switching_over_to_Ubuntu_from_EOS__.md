---
title: "Thinking about switching over to Ubuntu from EOS  -- minimum size for root partition"
date: 2021-12-04
forum: New to Ubuntu
---

### Post by straitsfan on 2021-12-04
Hello.   Thinking about switching over to Ubuntu.  Have EOS, and generally new to Linux.  Was wondering how big the root partition should be, as well as the home partition.   Can I use Gparted to do this?  I assume I can, since I did it with EOS.  But I don't have a home partition with EOS.  Just the swap file and root partition.   

What are the advantages if any over EOS, etc?  Is it just preference?

By the way, is there any sort of tutorial to introduce me to Linux in general?  I want to learn the command line as well, as what commands to use to upgrade, update, install, etc, apps.

Please ask for more info if you need it.   These are just the questions that I can think of right now.

My apologies if any of these questions are redundant or stupid.  Used to MacOS, and want to expand my knowledge and experience.

One more question -- is there any way to be notified of a reply to my messages?   Can't seem to find it anywhere.

---

### Post by grahammechanical on 2021-12-04
It would help if you told us the hardware specification of your machine. The minimum specification for Ubuntu 20.04 LTS is:

2GHz dual core CPU; 4 GB Ram; 25 GB hard disk space; VGA capable of 1024 x 768 screen resolution; DVD drive or USB port.

If  you let the installer do the work it will create an EFI boot partition  and use the rest of the space as a root partition with Home as a folder.  Ubuntu uses a Swap file so you will not need a swap partition.

My  personal choice for a root partition is between 20GB to 25GB. And a  Home partition of about 20Gb to 30 GB. I also have a large Data  partition where I transfer all my data.

Regards

---

### Post by ActionParsnip on 2021-12-05
For the root partition I suggest 40Gb to be comfortable. The rest can be for whatever you need. If you are dual booting then make a large NTFS partition for casual data that both OSes can access, probably mounted in Ubuntu as /data and a separate partition for /home
This makes backups super easy.
If you aren't dual booting and it's a standard desktop setup then just use the rest as /home and you'll be OK.
If you want to learn how to use Linux then learn the same way you learned how to use Macos. By using it.

---

### Post by yancek on 2021-12-05
Doing an online search should give you any number of sites to use to learn.  Linux commands at the link below:

 [https://www.hostinger.com/tutorials/linux-commands](https://www.hostinger.com/tutorials/linux-commands)

Another link below with a basic tutorial on using Linux.

[https://www.tutorialspoint.com/unix/index.htm](https://www.tutorialspoint.com/unix/index.htm)

---

### Post by VMC on 2021-12-05
"What are the advantages if any over EOS, etc?  Is it just preference?"
Ubuntu is more complete. You need, to add CUPS for printing, scanning program an much more, to get EOS more up to date. I have both installed for different reasons.

---

### Post by straitsfan on 2021-12-05
Sorry -- don't know how that link got in there.   I really don't.   Anyway, if I could try again -- intel Dual core I7 core processor  2.67 Ghz, 8 GB RAM, Screen res 1336x768.  I think that should work, yes?

---

### Post by straitsfan on 2021-12-05
Sorry -- don't know how that link got in there. I really don't. Anyway, if I could try again -- intel Dual core I7 core processor 2.67 Ghz, 8 GB RAM, Screen res 1336x768. I think that should work, yes?

---

### Post by straitsfan on 2021-12-05
And my apologies for accidentally posting my latest reply twice.

---

### Post by guiverc on 2021-12-05
I'll provide my 2c; but sorry no real solutions.

My root is 27GB, but I wish it was 32GB (*I spend too much time each year having to clear space on it because I can't apply upgrades as there is insufficient space present*).   I noted 40GB recommended; if I had a larger disk; I'd have allocated that.  My `df -h` shows

```
/dev/sda1                27G   24G  2.0G  93% /
```

My drive is only 160GB, so I divided it up into two (it's dual boot, Ubuntu 20.04 LTS & Ubuntu *jammy*), also note I use swap partition (*both OSes can share the same swap space** as long as one isn't hibernated*); if you're using *swapfile* I'd suggest adding that [*required*] size to your root partition as that's I bet where it'll be stored.

The amount of space required depends on how much software you'll add, the more packages/apps you'll install - the more space is required there. Only you can decide that, as you'll know if all you need is a browser (or two) instead of locally installed packages/applications.

You need space for upgrades; esp. *release-upgrades* (ie. to *jump* to the next release) and applications you'll install I already mentioned (*the more installed also means the more upgrade space required*). Package types also have a part; *snaps* can use more space than *debs* for example, as *debs* are '*better at sharing*' (snaps don't share for security reasons).

The correct space for your systems depends on what you'll install & how you'll use it.

---

### Post by TheFu on 2021-12-05
> **VMC said:**
> "What are the advantages if any over EOS, etc?  Is it just preference?"
Ubuntu is more complete. You need, to add CUPS for printing, scanning program an much more, to get EOS more up to date. I have both installed for different reasons.

**Yeah - what's EOS?  **   Is that like the difference between IOS and iOS?

Ubuntu has many advantages and some disadvantages, which feature belongs in which column is really a personal thing.
A minimum root partition would depend on many things.  I have 1 Ubuntu that uses under 1GB, but it is VERY specific and doesn't have any GUI.  Most desktops that you plan to run for years should start with 35G of storage. Initially, less than 10G will be used, but applications and swap size can make that grow.  If you move the swap outside that root partition, that frees that up.

If you use LVM for storage management, then you can start with a minimal LV sizes and grow when and where needed. That isn't a beginner thing, though it is just 1 checkbox during the installation for most flavors of Ubuntu.

---

