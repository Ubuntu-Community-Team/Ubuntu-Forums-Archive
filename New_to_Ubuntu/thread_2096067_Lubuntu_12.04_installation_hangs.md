---
title: "Lubuntu 12.04 installation hangs"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by JHawk56 on 2012-12-18
OK, before anyone asks why I'm using wubi :p, I cant' burn DVDs or boot from a flash drive. Once I've found the flavor I like best and know it works well with my gear, I'll find a way to do a normal install.

Anyway, my wubi install of Lubuntu 12.04 is failing. Since I have successfully installed (and removed) Ubuntu (Unity) 12.10 on the is very PC, I'm surprised.

The part of the installation that takes place in Windows appears to go well. When I reboot to finish the installation, it hangs partway through the "copying files" process, and displays the message, "Stopping CPU interrupts daemon.     [OK]" It hangs there for hours, even overnight.

Athlon XP 2400+, 512MB RAM, Radeon 9550

---

### Post by bcbc on 2012-12-19
Have you tried booting with nomodeset?: [http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by JHawk56 on 2012-12-20
> **bcbc said:**
> Have you tried booting with nomodeset?: [http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)
--------------------------------------------------
Last edited by bcbc; 2 Hours Ago at 01:16 PM.. Reason: askubuntu link was changed - no longer relevant
Thanks! I did get a look at the askubuntu link last night but had no time to deal with it. It did seem somewhat relevant, although the new one is more clear.

In any case, I'm still puzzled that this could be a video card issue, since I've already successfully run Ubuntu 12.10 (albeit in 2D) on this setup. I know 12.10 removed support for some cards, but going backwards should be safe. Unless Lubuntu lacks some drivers present in Ubuntu. On that theory, I might try Ubuntu 12.04 first, then add Lubuntu as an alternative desktop, hoping it would pick up the driver(?). I want Firefox and LibreOffice anyway, which Lubuntu lacks by default, so that would be one way to get them as well.

---

### Post by bcbc on 2012-12-20
Hmm.. yeah I missed that you already installed Ubuntu. So probably my solution is not relevant. (Normally I see Radeon and that's the clue, but some of them are fully supported with the open source driver and I should have checked)

I think your suggestion sounds like the best approach.

---

### Post by JHawk56 on 2012-12-20
Those installation progress screens I saw were in GUI, and were accompanied by some very pretty GUI Lubuntu tour screens to look at during the installation. So at least at that point I had some level of graphics support. It's only after rebooting out of the hang that follows, that I get failure immediately after the 5-second countdown. I've uninstalled and started over at least three times with the same results.

---

### Post by bcbc on 2012-12-20
> **JHawk56 said:**
> Those installation progress screens I saw were in GUI, and were accompanied by some very pretty GUI Lubuntu tour screens to look at during the installation. So at least at that point I had some level of graphics support. It's only after rebooting out of the hang that follows, that I get failure immediately after the 5-second countdown. I've uninstalled and started over at least three times with the same results.

Can you do anything e.g Ctrl+Alt+F1 to get to a terminal. 
```
tail /var/log/syslog
```

See if anything stands out. 

Zip up the log files in C:\ubuntu (assuming C: drive) to attach to a bug report:
```
sudo zip -r /host/ubuntu/failedinstalllogs.zip /var/log
```

Or is it totally frozen?

PS Ctrl+Alt+F7 gets back to the GUI. From the GUI there might  be a More Details button (or an expansion arror) you can click and a SKIP button that appears as well.

Just curious if that will show what the problem might be. If you're connected to the internet (ethernet) then try without doing that. Don't hook up the wireless either. It's not necessary.

---

### Post by Jtricx on 2012-12-20
Try updating your gpu driver.

---

### Post by JHawk56 on 2012-12-20
> **bcbc said:**
> Can you do anything e.g Ctrl+Alt+F1 to get to a terminal. 
```
tail /var/log/syslog
```

See if anything stands out.

Unfortunately, in perparation for  the method I was discussing with forum member bcbc, I've already deleted it, and the lubuntu iso as well. If I run into the same problem with Ubuntu, I'll try as suggested

> **bcbc said:**
> Zip up the log files in C:\ubuntu (assuming C: drive) to attach to a bug report:
```
sudo zip -r /host/ubuntu/failedinstalllogs.zip /var/log
```Any log files in D:\ubuntu (or lubuntu) were deleted with the installation. I do still have my wubi log on my C: drive, but it only covers the portion that takes place in Windows, and it looks fine to me.

I'll report back.

---

### Post by JHawk56 on 2012-12-22
Well, the installation of Ubuntu 12.04 also got hung up. Using nomodeset allowed me to get farther, but then I ran into an unrecoverable error and had to reboot. That led to errors messages about my partitions already being set up and it told me to remove them. The only way I knew to do that was to uninstall and start all over, and everything went just the same on the second try.

I was wanting to try 11.10 anyway, based on the experiences of others with Radeon 9550s, so I gave up on 12.04. I started with Ubuntu since wubu did not support Lubuntu on 11.04. That went smoothly, so I added Lubuntu as an alternative desktop. All is well.

I am still puzzled by not being able to install 12.04 smoothly, since 12.10 and  11.10 were no problem at all.

---

