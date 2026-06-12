---
title: "edit partiton size of Ubuntu 12.04"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by w0lf215 on 2012-09-24
I used the Windows Installer and installed Ubuntu 12.04 and it only allowed 30 gig max, so its a 30 gig partition and have a C: partition of 128 gig and a D: partition of 135 gig. I installed it on the D: partition. (it came in those amounts from factory). So i have a 135 gig available on that D partition but apparently ubuntu is currently only using 30 of them.. How can I increase this so that it can use atleast 50-60 gigs out of that D: partition? Ive tried gparted but don't know for sure what to edit and can't risk losing my main partition right now. (Win7 is on C:). Is there a simple tool to do this with other than gparted? Or can someone walk me through using gparted and which partitions to edit?
Thanks

---

### Post by cortman on 2012-09-24
Wubi is a bit different as it is a virtual machine. See [here]("https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F") for info on how to resize.

---

### Post by oldfred on 2012-09-24
Wubi is to see if you like Ubuntu. Like an extended test rather than just the liveCD.

From the developer:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

If you want larger partitions then it may be time to repartition and then you can create any size you like. Although I generally suggest only 25GB for / (root) and use shared NTFS data partition if dual booting with Windows or separate /home and/or separate data partitions if dual booting other systems.

With Windows pre-installed it is often an issue as the Vendor & Microsoft usually use all 4 primary partitions. If d: is just data you may be able to delete it, create a new extended partition and then you can create many logical partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by funicorn on 2012-09-25
my suggestion: do not waste too much time on a wubi installation. It's more like a tutorial system for u to experience and get familiar with ubuntu.  you can use it, work on it, but do not change too much of it. it has a tendency to break down.

---

### Post by Lyfang on 2012-10-20
> **funicorn said:**
> my suggestion: do not waste too much time on a wubi installation. It's more like a tutorial system for u to experience and get familiar with ubuntu.  you can use it, work on it, but do not change too much of it. it has a tendency to break down.

[Wubi Windows installer]("http://www.ubuntu.com/download/desktop/windows-installer") is a very easy way to try to install and uninstall *buntu. I would choose Lubuntu. Some consider Wubi to be buggy, since installed on a virtual disk on the NTFS filesystem, which makes it more sensitive. Backup and copy over all of your personal files regularly. But I'm using Wubi Lubuntu 12.04 without any problems, beyond a fresh normal *buntu installation. I suggest to install Wubi since Wubi is easy to uninstall. See also: [Wubi Uninstallation]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

Wubi Performance Difference "Disk performance is slightly slower. You should not be able to notice any difference under normal circumstances." - [http://askubuntu.com/questions/8159/what-performance-differences-are-there-when-installing-with-wubi](http://askubuntu.com/questions/8159/what-performance-differences-are-there-when-installing-with-wubi)

I have been using Wubi Lubuntu 12.04 about 5 months without any problems. Will uninstall Wubi Lubuntu 12.04 32-bit and install Wubi Lubuntu 12.10 64-bit ([lubuntu-12.10-desktop-amd64.iso]("http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-desktop-amd64.iso.torrent")) today.

---

