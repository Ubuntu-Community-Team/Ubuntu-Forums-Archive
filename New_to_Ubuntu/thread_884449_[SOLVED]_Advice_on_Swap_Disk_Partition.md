---
title: "[SOLVED] Advice on Swap Disk Partition"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Ralph L on 2008-08-09
I am repartitioning my 100G disk to allow maximum flexibility and need some advice.  I plan on having the following 6 partitions:
1.  Windows
2.  Shared--Linux user data accessible to all operating system partitions.
3.  Ubuntu A--Latest Ubuntu OS
4.  Ubuntu B--One generation old Ubuntu
5.  Kubuntu A--Latest Kubuntu
6.  Kubuntu B--One generation old Kubuntu.

Questions:
1.  Do I need even more partitions?  Do I need separate swap partitions for each OS?  Is there any performance advantage to having separate swap partitions?
2.  Does it matter whether certain partitions are primary or part of the extended partition?  Is there any performance advantage to having an OS (or maybe a swap) partition be primary?
3.  Does Windows need to be in the first primary partition?
4.  Is there any inherent flaw in the partitions I have outlined?

Thank you for your help.

Ralph

---

### Post by sandysandy on 2008-08-09
if i may ask why do u want both ubuntu and kubuntu and two versions of same OS.

one SWAP is OK. 

regards

---

### Post by mcduck on 2008-08-09
As long as you don't hibernate (suspend to disk) the systems the same swap partition can be shared between all Linux installs on the same machine. HIbernating and then booting to another Linux install would be a problem because the suspend data is written to swap partition, and then booting the other install would overwrite it. 

I agree with sandysandy that you probably could reduce the amount of partitions to half as Ubuntu & Kubunbtu are the same distro, only difference being the default desktop environment. You can have both Ubuntu & Kubuntu desktops on the same install and then just chose which DE you want from the login screen. This way you'd only need half the disk space, and half the updating & administration time to maintain both desktops..

So this is how I'd do it:

1. Windows
2. Shared (I'd use Ext3 and the Ext driver for Windows..)
3. Ubuntu 8.04 (with KDE & Gnome)
4. Ubuntu 7.10 (With KDE & Gnome)
5. swap

 (of course you'll end up with 6 partitions, one of them being the extended partition as that makes 5 partitions you can only have 4 primary partitions..)

---

### Post by Ralph L on 2008-08-10
I want to thank you both for the quick response and advice.  I still have some concerns:

1.  How do I install both Gnome and kde on the same OS?  I would like to get all the applications and utilities that come with each Gnome and Kde loaded with the appropriate desktop.  For example, Brasero (cd burner) with Gnome and k3b with Kde.  The way I originally installed Ubuntu was to download it, burn an image file on a CD and then install it.  The Gnome utilities were there automatically.  I don't know how I would add the Kde desktop and Kde utilities (I don't want to do them one at a time and I don't even know what I should load).  Or is there a better way to do the entire installation?

2.  How do I switch between a Gnome desktop and a Kde desktop?

2.  I do want to use the hibernate feature.  What I don't understand is why I need a swap partition at all.  Why can't the swap information be just another file in the OS partition?

3.  Also I still don't understand what should be put on primary partitions and what should be on the extended logical partitions.  Is there a best way to do things, or doesn't it matter.

Thanks for the attention

Ralph

---

### Post by mcduck on 2008-08-10
1. To install the different desktop environments, with all the applications Ubuntu includes with them, just ise the package managet to install "ubuntu-desktop"-package for Gnome, "kubuntu-desktop" for KDE and "xubuntu-desktop" for XFCE4.

By default, all the programs will show in all different desktop environments, alhough if you want, I remember seeing a thread with instructions how to hide Gnome apps in KDE and KDE apps in Gnome.


2. You can select which one you wan to use by clicking the "Session"-button in the login screen.


3. Keeping the swap in a different partition helps to keep disk fragmentation down. Not that the fragmentation really would be much of a problem with Linux file systems. And it also allows sharing the swap between different distributions, reducing the amount of disk space needed for swap on different Linux installs.

Also having swap on a different partition gives you more freedom to choose which hard drive you want to use for swapping, which can be used to increase the performance of the system. Of course with the low price of RAM these days you usually aren't using much swap anyway so on a modern desktop system this doesn't make much difference.

It's possible to set the swap to use a file instead of a partition. Although that would still use the same amount of disk space


4. Windows usually refuses to work on anything else than a primary partition. Actually it can even refuse to work if installed to anything else than the _first_ primary partition..

Apart from that, it doesn't really matter. Everything else can be on logical partitions.

---

### Post by Ralph L on 2008-08-10
Moduck.  Thanks a lot; that was really helpful.  As I have time I will proceed with repartitioning the disk and reinstalling linux.  Some things have not worked correctly, since I originally updated to Gnome Hardy--hibernate when the laptop lid is closed (have to manually hibernate), Open Office Writer aborts on certain files, etc.  Others in the formum have advised me to do a fresh install.  Also, I want to try Kubuntu and Koffice to see if these have features that I perceive as lacking in Gnome. If I get stuck I will be back on the forum asking questions.

Thanks again
Ralph

---

### Post by Ralph L on 2008-08-23
This is further discussed in "Want to Swap to a file on My Ubuntu Partition.

Ralph

---

