---
title: "Wubi - Upgrade doesn't work."
date: 2011-10-22
forum: New to Ubuntu
---

### Post by anemone42 on 2011-10-22
Upgrading ubuntu led to a new, broken version, but the old one still runs

GRUB now presents 2 x 2 options. Using the older version works fine, using the new one (both regular and fail safe) doesn't work. I'd like to be up to date, with the up to date version actually working, not just sitting there.

Not working = when I choose it, I end up on a black screen, "forever" (more than 1 minute).

Ubuntu installed as wubi, in windows 7.

I recently did a fresh install of what GRUB calls 2.6.38-8, This was my first upgrade after that fresh install, and brought me to 2.6.38-11, or it should have.

---

### Post by philinux on 2011-10-22
I added Wubi to the title of your thread. Cheers.

---

### Post by bcbc on 2011-10-22
Hit 'e' on the grub menu, remove 'quiet splash', Ctrl+X to boot, report where it hangs. Any messages?
Or use the recovery mode. That should output the same info.

What computer brand/model/graphics card?
Did you install any custom graphics drivers while running Natty?

---

### Post by Humber on 2011-10-22
For some reason when using Ubuntu I'm having a hard time downloading updates. I started with 11.04 -- when the upgrade to 11.10 became available I tried to get it. The OS downloaded a bunch of files then suddenly it stopped and made 2 more attempts. Then I was told 4 files didn't come down and to check my internet connection (which works perfectly). After trying it again, and again and again, it got 3 more files but sadly it didn't get the last one no matter how many times I tried.

Since my configuration and data on Ubuntu weren't all that much, I decided to go back into Windows and re-download Wubi plus the ISO for 11.10 (as opposed to the upgrade). It installed flawlessly. However, when I went to install some drivers and other necessities, the same problem cropped up, only worse this time because there were about 6 files that wouldn't come down after no less than 10 tries. I then deleted Ubuntu and came to the forums to see if I could identify and troubleshoot the problem before attempting a reinstall.

Can anyone help?

---

### Post by bcbc on 2011-10-22
Humber,
Please create a new thread for your problem. This sort of issue is unlikely to be fixed by uninstalling/reinstalling. If you want to troubleshoot, reinstall, note the problem details (i.e. what are the drivers you are trying to install), and post a new thread and someone can help you.

---

### Post by LinuxFan999 on 2011-10-22
> **anemone42 said:**
> Upgrading ubuntu led to a new, broken version, but the old one still runs

GRUB now presents 2 x 2 options. Using the older version works fine, using the new one (both regular and fail safe) doesn't work. I'd like to be up to date, with the up to date version actually working, not just sitting there.

Not working = when I choose it, I end up on a black screen, "forever" (more than 1 minute).

Ubuntu installed as wubi, in windows 7.

I recently did a fresh install of what GRUB calls 2.6.38-8, This was my first upgrade after that fresh install, and brought me to 2.6.38-11, or it should have.
Remember that Wubi should not be used as a permanent installation of Ubuntu.

---

### Post by Mark Phelps on 2011-10-23
> **anemone42 said:**
> I recently did a fresh install of what GRUB calls 2.6.38-8, This was my first upgrade after that fresh install, and brought me to 2.6.38-11, or it should have.

Wubi doesn't uses GRUB -- it uses something known as GRUB4DOS.  Messing around with GRUB and Wubi is a surefire way to hose up both your Windows install and Ubuntu install.

---

### Post by bcbc on 2011-10-23
Wubi uses both grub2 and grub4dos.I think the OP means: did a fresh install of [the version of Ubuntu] that grub refers to as kernel 2.6.38-8 (i.e. 11.04).

---

### Post by anemone42 on 2011-10-23
> **LinuxFan999 said:**
> Remember that Wubi should not be used as a permanent installation of Ubuntu.

Is this correct? Because when I was first installing on this computer, and couldn't find a free partition, I was advised, wubi was just as good, and people didn't do the partition anymore anyway.

---

### Post by anemone42 on 2011-10-23
> **bcbc said:**
> Hit 'e' on the grub menu, remove 'quiet splash', Ctrl+X to boot, report where it hangs. Any messages?
Or use the recovery mode. That should output the same info.

I'll try this and get back to you.

---

### Post by anemone42 on 2011-10-23
> **bcbc said:**
> What computer brand/model/graphics card?
Did you install any custom graphics drivers while running Natty?

Computer: HP620.

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

I have not fiddled with the graphics cards, and don't know what Natty is?

---

### Post by philinux on 2011-10-23
> **anemone42 said:**
> Is this correct? Because when I was first installing on this computer, and couldn't find a free partition, I was advised, wubi was just as good, and people didn't do the partition anymore anyway.

This is very true. Wubi was meant as a way to explore ubuntu. It was never intended as a long term install let alone upgrade etc etc.

A proper install would be much better.

---

### Post by anemone42 on 2011-10-23
> **philinux said:**
> This is very true. Wubi was meant as a way to explore ubuntu. It was never intended as a long term install let alone upgrade etc etc.

A proper install would be much better.

Well, in that case, my problem is stated here instead:

[http://ubuntuforums.org/showthread.php?t=1792583](http://ubuntuforums.org/showthread.php?t=1792583)

---

### Post by bcbc on 2011-10-23
You need to delete one of the four partitions to do a direct install as suggested by amjjawad in that thread.

You'll probably still have to deal with this issue though - it's not a wubi type of issue. But it is better (as stated by others) to have a direct install.

When you boot the newest kernels after removing 'quiet splash' do you see a bunch of text and then the screen goes black? or does it freeze somewhere? If you look closely is the screen on but just the backlight is off, or is it completely black?
If you boot in recovery mode, what happens differently if anything?

---

### Post by anemone42 on 2011-10-24
> **bcbc said:**
> You need to delete one of the four partitions to do a direct install as suggested by amjjawad in that thread.

You'll probably still have to deal with this issue though - it's not a wubi type of issue. But it is better (as stated by others) to have a direct install.

When you boot the newest kernels after removing 'quiet splash' do you see a bunch of text and then the screen goes black? or does it freeze somewhere? If you look closely is the screen on but just the backlight is off, or is it completely black?
If you boot in recovery mode, what happens differently if anything?

I haven't done the not-quiet-splash thing yet, as they should produce the same.

In recovery mode, I get a lot of lines, the last few have to do with "... new high speed usb device ...". Then the screen is blanked, so it's showing a lot of black.

Which partition can I safely delete?

---

### Post by bcbc on 2011-10-24
Check this out: [http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning](http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning)

Note [this]("http://members.iinet.net.au/~herman546/p17.html#Partitioning_Laptops"):> Never delete a recovery partition or any other partition unless you're sure you will still be able to re-install your old operating system somehow without it.   

Basically you will have to do the work to figure out what is on your computer, which primary partition you either don't need (backup what's on it and delete/ or merge it with another). I can speculate that /dev/sda4 is a candidate to delete, but from the limited info out there I'd say that likely you'll have to shift some data around between /dev/sda3 and /dev/sda2 as well (maybe resize them as well).

Despite the fact that wubi is not recommended for a permanent install, don't rush into this if you're not ready or you haven't made your backups and know how to recover. A normal install isn't going to rock your Ubuntu world. It's faster and you can do things like hibernate, but at the end of the day it works the same. My only advice when using Wubi is to make sure that any important data is regularly backed up - as the virtual disk wubi uses is a risk (if there is filesystem corruption you can lose the whole install).

Partitioning isn't complex - and generally isn't risky if you know what you're doing - but you need to take the time and prepare properly for it (including a full backup).

---

### Post by anemone42 on 2011-11-01
Okay, I've now installed Ubuntu in a separate partition.

However I end up in exactly the same place. The version, that's the result of an upgrade, doesn't work, but the original one does.

---

### Post by anemone42 on 2011-11-17
I've checked /var/log/syslog, but a boot, that doesn't result in a running system, isn't reflected in the log either.

---

### Post by anemone42 on 2011-11-21
Upgrading to 11.10 seems to have solved the problem.

---

