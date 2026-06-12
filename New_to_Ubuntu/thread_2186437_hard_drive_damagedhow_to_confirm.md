---
title: "hard drive damaged?/how to confirm?"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by ccdavis77 on 2013-11-07
Hello...new to the forum and Ubuntu.  I recently installed ubuntu as the OS for my media center and was having some operational problems...on another forum, I was advised to type in the code: "dmesg | pastebinit" which yielded:
[http://paste.ubuntu.com/6348221/](http://paste.ubuntu.com/6348221/)

Based on the above output, I was told my hard drive was irreparably damaged and would have to be replaced.    My question is, is this hard drive damaged for certain? If not, how do I confirm that it is or is not via Ubuntu or is there a way to try to repair it?  It was a brand new hard drive never used before and I bought it some time ago so is going to be hard to exchange.  It is a removable 2TB 3.5 inch SATA III hard drive.  I appreciate any help/advice!!!

---

### Post by grahammechanical on 2013-11-07
I am curious. what was there about that printout that indicated that the hard drive was irreparably damaged? What do you have on this hard drive? Is Ubuntu installed on it? Can you load Ubuntu? In other words, what gave you the idea that the drive was not working as it should?

We have in Ubuntu a utility called Disks. If the hard disk has Smart functions, then the Disks utility will read the Smart information on the drive and report back to you. Disks has a function called Smart Data and Self Tests.

Regards.

---

### Post by fantab on 2013-11-07
Boot Ubuntu DVD/USB and 'Try Ubuntu without installing'. Open the utility called 'Disks' and run SMART Tests on it. See what comes up.

Secondly, you can check the HDD manufacturer's website for disk checking utility for their disks. Most of the Utilities will run only in Windows, so you may have to connect the HDD in question to a Windows machine.

---

### Post by dannyboy79 on 2013-11-07
a quick google of the repeating error in yoru dmesg output shows me it's a bug possibly for some hard drive chipsets, is it a SSD drive? i don't think drive is damaged but what are the symptoms that made you think something was wrong to begin with?

---

### Post by ccdavis77 on 2013-11-08
First, thanks for all of the replies. I loaded ubuntu with my media center platform aka "xbmcbuntu" onto a swappable 3.5 inch 2tb hard drive.  After having some problems, the response in response to the above cited paste in output was: 

"Oh no, Your harddisk is broken, have a look here:


Quote:
```
[ 1291.019226] ata7.00: qc timeout (cmd 0x2f)
[ 1291.019249] ata7: failed to read log page 10h (errno=-5)
[ 1291.019253] ata7.00: exception Emask 0x1 SAct 0xf SErr 0x0 action 0x6 frozen
[ 1291.019255] ata7.00: irq_stat 0x40000008
[ 1291.019256] ata7.00: failed command: READ FPDMA QUEUED
[ 1291.019260] ata7.00: cmd 60/00:00:00:93:84/01:00:02:00:00/40 tag 0 ncq 131072 in
[ 1291.019260] res 40/00:0c:00:94:84/00:00:02:00:00/40 Emask 0x1 (device error)
[ 1291.019261] ata7.00: status: { DRDY }
[ 1291.019263] ata7.00: failed command: READ FPDMA QUEUED
[ 1291.019265] ata7.00: cmd 60/00:08:00:94:84/01:00:02:00:00/40 tag 1 ncq 131072 in
[ 1291.019265] res 40/00:0c:00:94:84/00:00:02:00:00/40 Emask 0x1 (device error)
[ 1291.019267] ata7.00: status: { DRDY }
[ 1291.019268] ata7.00: failed command: READ FPDMA QUEUED
[ 1291.019271] ata7.00: cmd 60/18:10:28:ad:04/00:00:ac:00:00/40 tag 2 ncq 12288 in
[ 1291.019271] res 40/00:0c:00:94:84/00:00:02:00:00/40 Emask 0x1 (device error)
[ 1291.019272] ata7.00: status: { DRDY }
[ 1291.019274] ata7.00: failed command: READ FPDMA QUEUED
[ 1291.019276] ata7.00: cmd 60/08:18:98:c4:15/00:00:00:00:00/40 tag 3 ncq 4096 in
[ 1291.019276] res 40/00:0c:00:94:84/00:00:02:00:00/40 Emask 0x1 (device error)
[ 1291.019278] ata7.00: status: { DRDY }
[ 1291.019281] ata7: hard resetting link
[ 1291.511214] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 1291.513216] ata7.00: configured for UDMA/133
[ 1291.513303] ata7: EH complete
[ 1299.371000] ata7.00: qc timeout (cmd 0x2f)
[ 1299.371024] ata7: failed to read log page 10h (errno=-5)
[ 1299.371030] ata7.00: exception Emask 0x1 SAct 0xd SErr 0x0 action 0x6 frozen
[ 1299.371032] ata7.00: irq_stat 0x40000008
[ 1299.371034] ata7.00: failed command: READ FPDMA QUEUED
[ 1299.371040] ata7.00: cmd 60/08:00:98:c4:15/00:00:00:00:00/40 tag 0 ncq 4096 in
[ 1299.371040] res 40/00:2c:f0:1b:04/00:00:74:00:00/40 Emask 0x1 (device error)
[ 1299.371043] ata7.00: status: { DRDY }
[ 1299.371045] ata7.00: failed command: READ FPDMA QUEUED
[ 1299.371050] ata7.00: cmd 60/00:10:00:94:84/01:00:02:00:00/40 tag 2 ncq 131072 in
[ 1299.371050] res 40/00:2c:f0:1b:04/00:00:74:00:00/40 Emask 0x1 (device error)
[ 1299.371053] ata7.00: status: { DRDY }
[ 1299.371055] ata7.00: failed command: READ FPDMA QUEUED
[ 1299.371060] ata7.00: cmd 60/00:18:00:93:84/01:00:02:00:00/40 tag 3 ncq 131072 in
[ 1299.371060] res 40/00:2c:f0:1b:04/00:00:74:00:00/40 Emask 0x1 (device error)
[ 1299.371062] ata7.00: status: { DRDY }
[ 1299.371067] ata7: hard resetting link
[ 1299.863006] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 1299.864300] ata7.00: configured for UDMA/133
[ 1299.864374] ata7: EH complete
[ 1307.706759] ata7.00: qc timeout (cmd 0x2f)
[ 1307.706774] ata7: failed to read log page 10h (errno=-5)
[ 1307.706780] ata7.00: exception Emask 0x1 SAct 0x7 SErr 0x0 action 0x6 frozen
[ 1307.706782] ata7.00: irq_stat 0x40000008
[ 1307.706785] ata7.00: failed command: READ FPDMA QUEUED
[ 1307.706790] ata7.00: cmd 60/00:00:00:93:84/01:00:02:00:00/40 tag 0 ncq 131072 in
[ 1307.706790] res 40/00:14:98:c4:15/00:00:00:00:00/40 Emask 0x1 (device error)
[ 1307.706793] ata7.00: status: { DRDY }
[ 1307.706795] ata7.00: failed command: READ FPDMA QUEUED
[ 1307.706800] ata7.00: cmd 60/00:08:00:94:84/01:00:02:00:00/40 tag 1 ncq 131072 in
[ 1307.706800] res 40/00:14:98:c4:15/00:00:00:00:00/40 Emask 0x1 (device error)
[ 1307.706802] ata7.00: status: { DRDY }
[ 1307.706804] ata7.00: failed command: READ FPDMA QUEUED
[ 1307.706808] ata7.00: cmd 60/08:10:98:c4:15/00:00:00:00:00/40 tag 2 ncq 4096 in
[ 1307.706808] res 40/00:14:98:c4:15/00:00:00:00:00/40 Emask 0x1 (device error)
[ 1307.706811] ata7.00: status: { DRDY }
[ 1307.706815] ata7: hard resetting link
[ 1308.198755] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 1308.200128] ata7.00: configured for UDMA/133
[ 1308.200198] ata7: EH complete
[ 1316.038579] ata7.00: qc timeout (cmd 0x2f)
[ 1316.038593] ata7: failed to read log page 10h (errno=-5)
[ 1316.038595] ata7.00: NCQ disabled due to excessive errors
[ 1316.038598] ata7.00: exception Emask 0x1 SAct 0x7 SErr 0x0 action 0x6 frozen
[ 1316.038599] ata7.00: irq_stat 0x40000008
[ 1316.038601] ata7.00: failed command: READ FPDMA QUEUED
[ 1316.038604] ata7.00: cmd 60/08:00:98:c4:15/00:00:00:00:00/40 tag 0 ncq 4096 in
[ 1316.038604] res 40/00:14:00:93:84/00:00:02:00:00/40 Emask 0x1 (device error)
[ 1316.038605] ata7.00: status: { DRDY }
[ 1316.038607] ata7.00: failed command: READ FPDMA QUEUED
[ 1316.038609] ata7.00: cmd 60/00:08:00:94:84/01:00:02:00:00/40 tag 1 ncq 131072 in
[ 1316.038609] res 40/00:14:00:93:84/00:00:02:00:00/40 Emask 0x1 (device error)
[ 1316.038611] ata7.00: status: { DRDY }
[ 1316.038612] ata7.00: failed command: READ FPDMA QUEUED
[ 1316.038614] ata7.00: cmd 60/00:10:00:93:84/01:00:02:00:00/40 tag 2 ncq 131072 in
[ 1316.038614] res 40/00:14:00:93:84/00:00:02:00:00/40 Emask 0x1 (device error)
[ 1316.038616] ata7.00: status: { DRDY }
[ 1316.038619] ata7: hard resetting link"
...
```


...told me the hard disk is damaged and not to use it. Overall, at this point though, it seems to mostly be working fine. However, every little glitch has made me wonder if I need to replace it...

---

### Post by fantab on 2013-11-08
Download the latest version of Ubuntu, which is 13.10 and run the SMART tests on it as suggested earlier. Some issue could be with the Kernel xmbcbuntu has in there.

Post details of you computer. Check your BIOS to see what SATA mode its running in, AHCI or IDE? 
What mobo do you have, consider BIOS Update.
Plug the HDD in another computer with a different OS and run the tests as suggested.

---

### Post by ccdavis77 on 2013-11-09
I won't be able to plug the hd into another computer since I only have a couple of laptops running windows here.  Will going into ubuntu and downloading 13.10 possibly affect the function of xbmc (I generally boot right into the media center interface).  My computer has an intel i3-3225 processor with 4gb of RAM and an ASRock B75 Pro3-M micro-ATX motherboard.  Not sure about the BIOS info or how to access that via ubuntu yet ...

---

### Post by fantab on 2013-11-09
YOu enter BIOS menu directly, and not via any OS. There will be some key like F2, ESC, or TAB etc to enter the BIOS just before it loads any OS.

---

### Post by ccdavis77 on 2013-11-10
Ok, SATA mode is AHCI. Running version 1.70 on my B75 Pro3-M motherboard, update version only adds "Change Internet Flash server" ([http://www.asrock.com/mb/Intel/B75%20Pro3-M/?cat=Download&os=BIOS](http://www.asrock.com/mb/Intel/B75%20Pro3-M/?cat=Download&os=BIOS)).

---

### Post by fantab on 2013-11-10
> **fantab said:**
> Boot Ubuntu DVD/USB and 'Try Ubuntu without installing'. Open the utility called 'Disks' and run SMART Tests on it. See what comes up.

Secondly, you can check the HDD manufacturer's website for disk checking utility for their disks. Most of the Utilities will run only in Windows, so you may have to connect the HDD in question to a Windows machine.

Booting from Ubuntu Live DVD/USB run the SMART TESTS using 'Disks' utility. Live DVD/USB Ubuntu runs from RAM and does not need HDD so its ideal to check for HDD problems.

---

### Post by ccdavis77 on 2013-11-11
So I need to create a Ubuntu Live USB correct? Probably silly question, but do I need to match it to the version of Ubuntu I am running that was packaged with the xbmc application?

---

### Post by fantab on 2013-11-11
Yes, create a Live Ubuntu USB.
No, you don't have match the versions, just use the 'supported' version, like 12.04 or 13.10.

---

### Post by ccdavis77 on 2013-11-22
ok, created the live USB.  overall assessment of the hard drive= "disk failure is imminent, backup all data and replace the disk" ...read error rate=failing. whenever I try to run the self-test just gives me the disk utility "hard disk problems detected, a hard disk is reporting health problems" and doesn't seem to let me try to fix the disk.

---

### Post by fantab on 2013-11-22
That is indeed a bad report. 

Check again with manufacturer for Warranty, some manufacturers give a full 5 yr. warranty and some 3yrs. If the HDD is in warranty you CAN get it exchanged. Also check the manufacturer's website for some kind of 'utility' to fix errors if they can be fixed. 
Seagate and Western Digital, I know offer utilities and fixes.

Good Luck...

---

### Post by ccdavis77 on 2013-11-22
hey fantab...thanks again for all of your help! good news, went to WD and appears drive is still in warranty so set up for advance replacement...so will get a new one and start from scratch with Ubuntu...may start with the latest version this time and install XBMC from within the OS if I can find out easily how to get the system to boot directly into the media center interface that is...

---

### Post by fantab on 2013-11-22
> **ccdavis77 said:**
> hey fantab...thanks again for all of your help! good news, went to WD and appears drive is still in warranty so set up for advance replacement...so will get a new one and start from scratch with Ubuntu...may start with the latest version this time and install XBMC from within the OS if I can find out easily how to get the system to boot directly into the media center interface that is...

That's good news indeed.

You know some of us here have two installs of Ubuntu on our HDD, on separate partitions. One entirely dedicated to a more stable LTS version and another the Latest non-LTS version. I upgrade my LTS every two years, and the other non-LTS every six months. You can consider this set up.

Also you might find [**this info**]("http://www.noobslab.com/2013/01/install-xbmc-120-frodo-in-ubuntu.html") useful when installing XMBC in Ubuntu.

---

### Post by ccdavis77 on 2013-12-04
Thanks for all of the help, replaced the hard drive and working great! One last problem: I have to send the defective drive back to WD and want to wipe it first. I can't seem to do it though; via the disk utility, disk assessment remains "disk likely to fail soon" and all attempts at formatting/wiping content are met with "error formatting disk'...error synchronizing after initial wipe: Timed out waiting for object (iDisks-error-quark,0)".  How can I get my personal data off this and not accessible before I send it back??!! Thanks for any help!!!

---

### Post by fantab on 2013-12-04
You can try '**dd**' to wipe the HDD clean, but not sure how successful it will be on a failing or failed Disk.

Boot with Ubuntu DVD/USB and 'Try Ubuntu without installing"... Open Terminal [Ctrl+Alt+T]:

```
sudo swapoff
sudo dd if=/dev/zero of=/dev/sd[COLOR=#b22222]**x**[/COLOR]
```

Replace '**[COLOR=#b22222]x[/COLOR]**' with appropriate letter for you HDD (like, /dev/sd**[COLOR=#b22222]a[/COLOR]** or /dev/sd**[COLOR=#b22222]b[/COLOR]**). Be careful and use the correct letter, if you end up using some other HDD's letter then that HDD will be wiped clean. Better to remove all other HDDs and other storage media.
You can find out the correct letter of the disk with:
```
sudo parted -l
```

It will take time to wipe it clean, depending on the Size of the HDD and DATA present. Be patient.
If it works then great, if not.....

Good Luck.

---

