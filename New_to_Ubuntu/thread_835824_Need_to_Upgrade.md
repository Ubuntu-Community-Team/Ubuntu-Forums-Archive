---
title: "Need to Upgrade"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-06-20
What are the different ways I can upgrade from 6.10 to 8.04?

---

### Post by Bigtime_Scrub on 2008-06-20
From what I understand you should be able to upgrade via Synaptic Package Manager or you can download a copy of 8.04 off a torrent site, burn it, and start clean.

---

### Post by sharks on 2008-06-20
if u want to upgrade ur 6.10 upgrade via synaptic or type in terminal:

sudo apt-get dist-upgrade

---

### Post by Hospadar on 2008-06-20
You can:
Install fresh off a cd-
If you go this route, you can either: forget about any data you have saved on the machine, or backup any data you want.  If you want to keep all your settings and data, back up the entire /home directory.  If you have your machine set up with a seperate /home partition, you can just install, choose custom partitioning, mount your drives where they should go (probably meaning set the mount points for / and /home) and only format the / (not the /home) partition.

Use the update manager with an internet connection-
Take a look here: [http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html](http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html)
I'm not totally sure that dist-upgrade is still available for 6.10, but I don't really see a reason it wouldn't be, so you should be fine.

Either route you take, be sure to back up any and all important data before upgrading.  Often the net upgrade can fail, leaving you with an inoperable installation (requiring a complete re-install from livecd) or you can make mistakes with a manual install from a cd and wipe some part of a drive you didn't mean to.  That said, the net upgrade will probably work just fine, but sometimes it doesn't, and if not, be prepared to do an installation from cd.  The newer net upgrades tend to work better, so don't be afraid of them alltogether, but sometimes they cause problems.

---

### Post by sharks on 2008-06-20
I think fresh install should be a good option. dont forget to back up ur important files.

---

### Post by oilchangeguy on 2008-06-20
> **Andrew79 said:**
> What are the different ways I can upgrade from 6.10 to 8.04?

back up your data. burn or order an 8.04 cd. and do a fresh install. i don't think you can go from 6.10 to 8.04 unless you upgrade to 7.04 and 7.10 first. and doing that is a waste of time.

---

### Post by mivo on 2008-06-20
I agree with the recommendation of a fresh install. It's likely to be less troublesome, and if you haven't already, a good opportunity to make a separate /home partition (which makes future fresh installs even more convenient). But yes, do backup important files.

Try the Live CD first to see if everything us working.

---

### Post by Andrew79 on 2008-06-20
> **sharks said:**
> if u want to upgrade ur 6.10 upgrade via synaptic or type in terminal:

sudo apt-get dist-upgrade

this told me command not found, i ordered a new disk to be sent in a couple of days. Thanks everyone though, apperciate the time

---

### Post by friendofpugs on 2008-06-20
Downloading and burning an iso image yourself is much faster. Just make sure you have the disk do a self check to make sure everything is okay. I have a cable ISP and Hardy downloaded in about 30 minutes.

---

### Post by Andrew79 on 2008-06-21
See, I don't think that works for some reason either. I tried that, but for whatever reason, it just kinda sits there and stares at me??? I am giving up, I already went ahead and paid a couple of bucks on Amazon had it rush delivered, I should have it at the beginging of the week, no biggie. At least I won't have to sweat much longer, and don't have to worry about really boogering anything else up, nice clean install

---

