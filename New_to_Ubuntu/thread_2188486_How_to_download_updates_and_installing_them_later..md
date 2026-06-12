---
title: "How to download updates and installing them later....."
date: 2013-11-17
forum: New to Ubuntu
---

### Post by Citta on 2013-11-17
....at home, without internet-access?
 Because the installation can be time-consuming, can do this at home, without staring at the monitor. I heard that could be accomplished with Synaptic, but I do not know how to do this.
Thanks for your suggestions!

---

### Post by Impavidus on 2013-11-17
Not sure about synaptic, but it may be possible. At the very least it can create a download script so you can download using a different computer and transfer by flash drive, and nobody stops you from running the script on your own computer. However, there should be an easier way.

Using the command line it's easy:```
sudo apt-get update
sudo apt-get **-d** upgrade
```
This will download the upgrades, but not install them. Later you can run```
sudo apt-get upgrade
```and the downloaded packages will be installed.

Instead of **apt-get upgrade** you'll sometimes need **apt-get dist-upgrade**, both in the download and install commands. This happens if there are new packages, usually kernel updates.

---

### Post by ian-weisser on 2013-11-17
Look in Synaptic's File menu - you will see the options for *Generate package download script* and *Add downloaded packages*.

For command line usage, look into the apt-zip and apt-offline packages. Both are intended to make offline package management easy.

And, of course, the Ubuntu Wiki has an entire page of helpful advice: [https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

### Post by Citta on 2013-11-18
Hm, I did not explain it good enough, sorry, I have a netbook and I want do the update/download when internetaccess is available and install it later without internetaccess.

---

### Post by The Cog on 2013-11-18
I think Impavidus gave you the answer you are looking for, although it is command-line and not synaptic. 
I don't think it is directly possible with synaptic although the scripts that  ian-weisser refers to will get you there in a rather more complicated way.

---

