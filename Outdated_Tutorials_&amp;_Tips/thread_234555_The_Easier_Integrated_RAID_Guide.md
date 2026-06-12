---
title: "The Easier Integrated RAID Guide"
date: 2006-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Curved on 2006-08-11
If you aren't familiar with RAID, you probably don't know that the majority of motherboards that claim to have a RAID controller onboard dont actually have one. This little gimmick is called fake RAID, and to spare you the details that you can find around the net, it doesnt help a whole lot in controlling RAID. However, it does help us setup a software RAID array in Ubuntu quite easily.

By the way, I called it "Integrated" so more newbies would read it, as "Fake" implies software, and newbies dont think they have software RAID on their motherboards.

Before we begin, there's a whole gaggle of other how-tos on this topic, but they are all rediculously long. I successfully installed Ubuntu on a fake RAID 0 array, and I did it with a much less manual process than the current how-tos discribes.

If you arent a control or security freak, let me tell you how to put a default Ubuntu 6.06 install on fake RAID in say ... 20 minutes?

1 - Configure your BIOS: 
If you arent familiar with how to setup your BIOS for RAID, figure out how to do that before continuing. Its different for different motherboards, so look in your motherboard's documentation for more details. -- and yes, you need at least two identical HDDs.

2 - Launch a 6.06.1 Live CD session

3 - Open Synaptic:
System->Administration->Synaptic Package Manager

4 - Enable all of the repositories
Settings->Repositories
Check all of the boxes

5 - Reload Synaptic

6 - Download dmraid
Search for dmraid and mark it for installation. Then hit apply at the top.

7 - Install Ubuntu
Click the icon on the desktop. Proceed through as usual until you have to select the harddrive to install on. Click the one that does not start with sd or hd. 

MAKE SURE TO WRITE DOWN WHAT THIS DRIVE IS CALLED

If there are no other options than those that start with sd or hd, you have incorrectly setup your BIOS. Go back to playing with the BIOS and try again.

Continue on through the dialogs and install. At the VERY end of the installation, you should recieve an error when installing GRUB. This error is good, even though it will make it seem like the world has ended or something.

8 - Configure the system
Here is the ucky goey part. Just open up a terminal and do it all. Replace <DRIVE> with that drive name you wrote down during the installation. (the 1 after <DRIVE> is purposeful)

```

sudo mkdir /target
sudo mount /dev/mapper/<DRIVE>1 /target
mount --bind /dev /target/dev
mount -t proc proc /target/proc
mount -t sysfs sysfs /target/sys

sudo cp /etc/apt/sources.list /target/etc/apt
sudo cp /etc/resolv.conf /target/etc

sudo chroot /target

apt-get update
apt-get install dmraid

cp /lib/grub/i386-pc/stage1 /boot/grub/
cp /lib/grub/i386-pc/stage2 /boot/grub/

grub

device (hd0) /dev/mapper/<DRIVE>
root (hd0,0)
setup (hd0)
quit

update-grub

```

9 - Restart (do take out the Live CD while you are at it)

10 - done :)

---

