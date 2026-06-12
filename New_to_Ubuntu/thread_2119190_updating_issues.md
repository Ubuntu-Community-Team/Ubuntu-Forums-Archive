---
title: "updating issues"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by zdubun on 2013-02-23
Dear ubuntians out there,

I am trying to upgrade my 10.10 to 11.04 and eventually to the latest LTS version. However during the update I get the following error:
W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

What is the solution. 
My system is a dell d630, core 2 duo with windows xp and ubuntu both installed on the hard drive.

Thanks in advance

---

### Post by Sealbhach on 2013-02-23
Those are the restricted extras packages, they are not essential to upgrade and no longer available (it seems) for Natty.

Easiest thing to do is comment them out from your sources.list. Open it up like this

```
gksudo gedit /etc/apt/sources.list
```search for "extras" and put a # at the beginning of that line or lines.

The run sudo apt-get update and then continue the upgrade as normal. You will need to add the extras later as you get nearer to the current release, but cross that bridge when you get to it.

.

---

### Post by plucky on 2013-02-23
> **zdubun said:**
> Dear ubuntians out there,

I am trying to upgrade my 10.10 to 11.04 and eventually to the latest LTS version. However during the update I get the following error:
W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

What is the solution. 
My system is a dell d630, core 2 duo with windows xp and ubuntu both installed on the hard drive.

Thanks in advance

10.10 and 11.04 are no longer supported as they have reached End Of Life and so the repositories are closed.

Your best solution is to download the latest version of [12.04.2 LTS](http://releases.ubuntu.com/precise/) and do a clean install.

Good Luck

---

### Post by zdubun on 2013-03-31
Thank you sealbhach and plucky.
I am thinking of doing a clean install. Sorry but, how would I do that.
Regards

---

### Post by deadflowr on 2013-03-31
> **zdubun said:**
> Thank you sealbhach and plucky.
I am thinking of doing a clean install. Sorry but, how would I do that.
Regards

Go here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

and burn.

Read the full installation instructions link.

Remember to backup the files you want to keep.

If Ubuntu's new style is not for you try out

[xubuntu]("http://xubuntu.org/")

[lubuntu]("http://lubuntu.net/")

[kubuntu]("http://www.kubuntu.org/")

and any number of other distributions that might make the grade for you.

---

### Post by sudodus on 2013-03-31
0. Backup your personal files from the old installation.

A Dell d630, core 2 duo will run standard Ubuntu with Unity, but Lubuntu and Xubuntu will run faster. I suggest that you download desktop versions and try live (booted from CD/DVD/USB) before deciding what to install. If you have more than 2 GB RAM, I suggest that you use the 64 bit version. The 64-bit version will run with less memory, but needs more RAM for the same tasks.

1. Download the iso files you want to try and check with the md5sum.

2. Make CD/DVD/USB boot drive(s) and try Ubuntu, Lubuntu, Xubuntu ...

3. Before you install, while running live from the CD/DVD/USB boot drive, check with ```
gksudo gparted
``` which partitions to use. I suggest that you reuse the previous partition(s) for ubuntu.

4. Still running live from the CD/DVD/USB boot drive, start the installer.

5. When you arrive at the partitioning screen, select ***Something else***
and select the old Ubuntu partition as the new root partition and format it to ext4. Swap should be selected automatically unless you had encrypted home and cryptswap. Then you have to reformat the swap partition too. Check that grub will be installed to the drive (not to a partition). It should normally be installed to the first drive, /dev/sda (no number at the end).

---

### Post by KnownSyntax on 2013-03-31
You should just upgrade rather then do a clean install so that you don't have to re-install everything that you want, and also save and then re-import all of your files and documents that you would have lost doing a clean install. You shouldn't worry about the extras since it isn't anything important at all and isn't a "key" (or really any part) of the upgrading process.

---

### Post by sudodus on 2013-03-31
Upgrading in several steps is almost certainly causing more work than a fresh installation. Particularly from a version that is no longer supported.

---

### Post by deadflowr on 2013-03-31
> **KnownSyntax said:**
> You should just upgrade rather then do a clean install so that you don't have to re-install everything that you want, and also save and then re-import all of your files and documents that you would have lost doing a clean install. You shouldn't worry about the extras since it isn't anything important at all and isn't a "key" (or really any part) of the upgrading process.

To many problems can occur upgrading from natty to oneric to precise, or quantal.
Best to just backup what you want and do a clean install.
Upgrading one release is one thing, but two or three is gonna take a while to do.
The longer it takes the more likely something bad might happen.

---

