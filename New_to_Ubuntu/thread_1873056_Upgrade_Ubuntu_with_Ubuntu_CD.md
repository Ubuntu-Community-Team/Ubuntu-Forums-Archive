---
title: "Upgrade Ubuntu with Ubuntu CD"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by hannah187 on 2011-10-31
Hi,

I have multiple computer running Ubuntu 11.04. Now that 11.10 is available, is it possible to download the Desktop CD (or some other version) and upgrade all of these computers to version 11.10. I do not want to upgrade individual computer through internet as it will increase my data usage.

Many thanks

---

### Post by oldfred on 2011-10-31
I have not done it but have these links, others may know details.
aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

### Post by hannah187 on 2011-10-31
thanks a lot.. shall follow.. also appreciate if someone who actually had done this comment..

---

### Post by Miljet on 2011-10-31
I have never used AptonCD and cannot comment on it.

Once I intended to do a fresh install in the same partition as the old version, but I forgot to check the box to reformat the partition. Upon completion, I was pleasantly surprised to find that I had installed the newer version without losing any of my files and settings in my /home folders. It was like doing an upgrade without using the bandwidth. I haven't tried it lately so don't know if it still works that way or not.

---

### Post by wildmanne39 on 2011-10-31
Hi, I would also like to say to backup your important data first and the process of upgrading to 11.10 has not been going very well, I myself tried so I could see if it would be successful but a few things just did not work right and I ended up doing a clean install.
Thank you

---

### Post by hannah187 on 2011-11-01
> **Miljet said:**
> I have never used AptonCD and cannot comment on it.

Once I intended to do a fresh install in the same partition as the old version, but I forgot to check the box to reformat the partition. Upon completion, I was pleasantly surprised to find that I had installed the newer version without losing any of my files and settings in my /home folders. It was like doing an upgrade without using the bandwidth. I haven't tried it lately so don't know if it still works that way or not.

Can someone else comment on this quote? Does it still work, please?

---

### Post by nothingspecial on 2011-11-01
When you boot the cd and choose to install, The installer will offer you the option of upgrading using the cd.

I have not tried this method however.

---

### Post by 3rdalbum on 2011-11-01
> **nothingspecial said:**
> When you boot the cd and choose to install, The installer will offer you the option of upgrading using the cd.

I have not tried this method however.

I have. It's a fresh install, but it keeps your /home and makes a note of what software you have installed previously, then installs new copies over the Internet.

It's probably the best way to upgrade Ubuntu, because it avoids the potential "dist-upgrade" problems.

It's also possible to do an internet-style dist-upgrade using the Alternate CD; you insert the CD and run the "cdromupgrade" program on the root of the CD.

For both methods, it's a good idea to remove whatever packages you don't want FIRST before running the upgrade, otherwise you'll download packages that you are just going to delete anyway.

---

### Post by Jaybyrrd on 2011-11-01
Even then I still would not recommend doing an upgrade. What I would do, (I am assuming you either have a central server, or external) is move all your data that you want to keep like documents, pictures, music, etc to a separate site, then do a clean install, otherwise you will run into major problems. The upgrade is designed on the basis of 11.04 as a clean install updated to 11.10 as a clean install, as soon as you begin using the OS, you start losing the stability of the original clean install, and once you upgrade that compounds that loss. Bad idea, learned from experience.

---

### Post by haqking on 2011-11-01
> **oldfred said:**
> I have not done it but have these links, others may know details.
aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

Isnt APTonCD out of date (like last updated 2007 or something ?

I think [http://keryxproject.org/](http://keryxproject.org/) is more upto date project

---

### Post by hannah187 on 2011-11-03
thanks a lot.. I am not so worried about the data as I can obviously back it up however what about the packages I have installed since installing 11.04..what can I do to keep these packages while upgrading to 11.10
regards

---

### Post by alco75 on 2011-11-03
I went from Ubuntu Natty to Xubuntu Oneiric by 'upgrading' from a Xubuntu Oneiric Live USB. I didn't have any problems.

(I then got rid of old packages by following [this guide]("http://www.psychocats.net/ubuntu/purexfce").)

It's not *really* an upgrade. It'll keep your **/home** directory and reinstall any previously installed packages (which can take *hours*) but any data that's not in **/home** might be lost, so prepare for that.

After I upgraded, I found all my MySQL and Postgres databases were gone! Luckily, it was just my home laptop and not a production machine or anything. ;)

---

### Post by alco75 on 2011-11-03
> **hannah187 said:**
> what can I do to keep these packages while upgrading to 11.10

It'll reinstall them for you, (possibly) losing any package-specific data in the process, see my previous post.

---

### Post by oldfred on 2011-11-03
I create a list of packages and reimport the list. The list is just a text file. A new install will most like get new versions of all the software.


from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Another newer way, I have not used.
[http://stephen.rees-carter.net/2011/09/a-fantastic-new-feature-in-ubuntu-software-center-sync-between-computers/](http://stephen.rees-carter.net/2011/09/a-fantastic-new-feature-in-ubuntu-software-center-sync-between-computers/)
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/)

---

### Post by hannah187 on 2011-11-03
So there is really no quickfire way to just upgrade the Kernel and OS? I somehow thought Linux does everything..

---

### Post by dFlyer on 2011-11-03
To be safe just get a list of the packages you have installed, backup your data and do a clean install. That would be the safest way to upgrade, if your data is not in a separate /home folder.

---

### Post by hannah187 on 2011-11-05
fairly round about way.. what about the Alternate CD..any options there

---

