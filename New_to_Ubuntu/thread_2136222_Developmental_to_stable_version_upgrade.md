---
title: "Developmental to stable version upgrade"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Leslie Dorner on 2013-04-16
I'm using Ubuntu 13.04 64 bit Beta 2. I do sudo apt-get update, sudo apt-get upgrade, and sudo apt-get dist-upgrade commands in the terminal daily to stay up to date. Do I have to do a update-manager -d command using the ALT + F2 key combination to get the release candidate version this Thursday at 10 AM? Or, do I keep doing my apt-get updates and upgrades and dist-upgrades on a daily basis to get the final shipping version on April 25th?

Is there any way to tell if the following PPAs are going to support Ubuntu 13.04:

1. Ubuntu Tweak
2. Last.FM
3. HandBrake [daily snapshots]
4. ZRAM

They all supported Ubuntu 12.10 and earlier versions in the past so I'm hoping that they'll support 13.04 and future versions for quite some time. I'm not sure if Ubuntu Tweak will continue to be available for newer interim or LTS releases due to the developer's feelings toward Canonical and the future direction of Ubuntu though. We shall see.

Do I have to wait until April 25th to add these PPAs and do a sudo apt-get update, sudo apt-get upgrade, and sudo dist-upgrade to get the latest packages for Ubuntu Tweak, HandBrake, Last.FM, and ZRAM? Is there any way to tell if they'll be available for the release candidate?

---

### Post by fantab on 2013-04-17
> **Leslie Dorner said:**
> I'm using Ubuntu 13.04 64 bit Beta 2. I do sudo apt-get update, sudo apt-get upgrade, and sudo apt-get dist-upgrade commands in the terminal daily to stay up to date. Do I have to do a update-manager -d command using the ALT + F2 key combination to get the release candidate version this Thursday at 10 AM? Or, do I keep doing my apt-get updates and upgrades and dist-upgrades on a daily basis to get the final shipping version on April 25th?

Is there any way to tell if the following PPAs are going to support Ubuntu 13.04:

1. Ubuntu Tweak
2. Last.FM
3. HandBrake [daily snapshots]
4. ZRAM

They all supported Ubuntu 12.10 and earlier versions in the past so I'm hoping that they'll support 13.04 and future versions for quite some time. I'm not sure if Ubuntu Tweak will continue to be available for newer interim or LTS releases due to the developer's feelings toward Canonical and the future direction of Ubuntu though. We shall see.

Do I have to wait until April 25th to add these PPAs and do a sudo apt-get update, sudo apt-get upgrade, and sudo dist-upgrade to get the latest packages for Ubuntu Tweak, HandBrake, Last.FM, and ZRAM? Is there any way to tell if they'll be available for the release candidate?

Your apt-get update and apt-get upgrade will keep you updated. No need to do anything else.
Ubuntu is not 'Officially" Released yet. So the ppa's will not be updated until it is released. Search launchpad to see if you have 'em for 13.04.

I don't know about other applications but for Ubuntu-tweak stable you can add the following ppa:

```
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) raring main  
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) raring main 
```.

But seriously, you don't need Ubuntu-Tweak. We can do all those tweaks with 'dconf-editor' and 'compizconfig-settings-manager'. If you are looking for some specific tweaks, then we can help.

---

### Post by Leslie Dorner on 2013-04-20
I noticed that there were some core Ubuntu updates available this morning from the Release Candidate version that I have now. I'm wondering if that's normal or not. I'm waiting for a System76 device driver update to Ubuntu 13.04 and I am hoping it will fix my problem with a 128 GB Class 10 UHS-1 SDXC card that I have or not. I might get a second RMA request for this defective SDXC card from PNY.

---

### Post by deadflowr on 2013-04-20
It's normal to see a few updates to core features in the waning days of the development cycle.
These are for bugs, and such. A little polishing, if you will.

Doubt your device driver will get a fix, unless the bug you have has been reported.

---

### Post by Leslie Dorner on 2013-04-20
The System76 device driver will be updated to Ubuntu 13.04 64 bit this upcoming Thursday, but they told me that might not solve the problem with the PNY 128 GB Class 10 UHS-1 SDXC card. It may be the case that I have a defective SDXC card which would mark the second time in a row. I will request a second RMA to get a replacement sent to my home and PNY told me that would be my last RMA request that they would honor. I already got a full refund for my purchase from Amazon. I'm thinking that I'll have to wait until this upcoming Thursday to get the official Ubuntu 13.04 64 bit interim release version and the official System76 device driver to see if that will fix my problem with formatting the PNY card or not.

Ubuntu 13.04 64 bit Release Candidate is pretty solid, but I keep getting missing password authentication errors with Mozilla Thunderbird and Evolution regarding my Google Gmail account. I got an update for most of the online accounts features today, but I'm missing the Google online accounts patch. I think that Ubuntu 13.04 is faster than Ubuntu 12.04.2 64 bit LTS. Linux kernel 3.8.0.x.y has a lot more new features and it seems to be more stable with fewer bugs.

I created another thread about the PNY issue. I'm hoping someone else will be able to tell me why I keep getting an unrecognized disk label error in GParted when I try to format it to NTFS or /ext4 file system. Otherwise, I now understand that Release Candidate will have a couple of updates in the next five days and that should be normal. Thanks.

---

### Post by deadflowr on 2013-04-20
Once in a blue moon, I get password errors in thunderbird for a gmail account. Normally I just push cancel, and yet still get that accounts mail.

I am curious as to how system76 updates work. Do they have an added PPA/special repository, or do they email you about updates you can get?

And updates will continue for bugs through out the life cycle of the release, with a glut of updates usually coming within the first month as bugs previously not found by the few testers out there/here are found by the larger majority of users who venture into the new release.

---

### Post by Leslie Dorner on 2013-04-20
System76 has its own special PPA that pushes out updates for official LTS and interim release versions on the same date that they become available in April and October each year. They told me that Ubuntu 13.04 included the upstream patches for their Realtek RTL8411 SD card reader and the forthcoming System76 device driver will not fix my problem with my PNY SDXC card. So, it's up to PNY to send me a second RMA to get this fixed and it's up to Canonical to fix the GParted and u-disks format errors.

---

### Post by clearski on 2013-04-20
I am going to wait until Raring will be officially published on ubuntu.com, because what I got now is a stable system and don't want to risk anything.

I upgraded a day or two ago and I ended up with a desktop-picture-only screen after providing the credentials, couldn't access anything, so I had to reinstall. Then I read on the forum that it was something with compiz and others had the same problem, but I just couldn't access the web to read about the solution.

Software Update just notified me that there's a 6Mb update, but nothing seems crucial, so I'll take no risks now, I'll be just waiting a few days for the official launch. Meanwhile I'll keep an eye on the champaigne...

---

### Post by grahammechanical on 2013-04-20
> [COLOR=#000000]Is there any way to tell if the following PPAs are going to support Ubuntu 13.04:[/COLOR]

Yes. Install 13.04 and then install the PPAs and see what happens. I would not upgrade to a new Ubuntu release without first installing it in another partition and testing it to see if I could set the OS up in exactly the way I like it. Only then would I upgrade my base OS. I think that this is sensible way of doing things. Really, the best person to ask if this or that will work is ourselves by trying things out.

By the way, there is a Ubuntu Unity Tweak tool in the 13.04 Software Centre. But Ubuntu Tweak is not there. Also in the Software Centre is Last.FM but not HandBreak or ZRAM, whatever they are when they are at home.

Regards.

---

