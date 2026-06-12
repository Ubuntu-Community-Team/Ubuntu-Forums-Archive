---
title: "How to install and setup Ubuntu 5.04 the fastest way?"
date: 2005-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by jiyuu0 on 2005-05-10
If you are a Linux user, perhaps you've heard of, maybe even tried Ubuntu?

Ubuntu is a great Distro... but did you ever got frustrated by:
* it taking too much time to set up additional applications for Ubuntu
* apt-get is great, but not if your internet connection is slow
* you do not have an internet connection at all
* problems with offline or slow repository servers

For Desktop users, you will definitely need more applications...

Now, there's an [Unofficial Ubuntu Add-On CD](http://www.ubuntuguide.org/add-on-cd) to [Ubuntu 5.04 x86 Install CD (Hoary Hedgehog)](http://www.ubuntulinux.org/download) that will custom install most of the needed applications with a script (and without an internet connection):

[SIZE=4]**_How to install and setup Ubuntu 5.04 the fastest way (offline)?**_[/SIZE]

Ingredients:
-[Ubuntu 5.04 x86 Install CD (Hoary Hedgehog)](http://www.ubuntulinux.org/download)
-[Unofficial Ubuntu Add-On CD](http://www.ubuntuguide.org/add-on-cd) - [Packages List](http://ubuntuguide.org/add-on-cd/add-on-cd-2005-05-08)

Also Read:
[http://ubuntuforums.org/showpost.php?p=150088&postcount=1](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)

1. During the installation of [Ubuntu 5.04 x86 Install CD (Hoary Hedgehog)](http://www.ubuntulinux.org/download), it will try to connect online and download the latest updates. You can always do this later. So, do not configure network/internet connections at this point. If you have a DHCP server in your network, unplug your network cable. When prompted... choose:

**Do not configure the network at this time**

2. Install Ubuntu...

3. Once you have finished installing Ubuntu and is now in GNOME desktop, insert the [Unofficial Ubuntu Add-On CD](http://www.ubuntuguide.org/add-on-cd)

4. Open up Terminal program (Applications -> System Tools -> Terminal) and issue this command:

**sudo sh /media/cdrom0/install.sh**

*This will only copy Snapshots of Ubuntu Updates and Applications into your Hardisk
*Do not "sudo apt-get update" as this might disable offline installation

5. To custom install all the Add-On Applications, issue this command:

**sudo sh $HOME/Downloads/ug-install.sh**

*This is a script where you just need to answer Y/N and it will auto install and setup additional applications without internet connection
*There are additional applications that you can install offline. Read the UbuntuGuide on your Desktop

6. Note: If your Mplayer, XMMS, Audacity, RealPlayer, etc freezes or doesn't load, do read the "How to configure sound to work properly in GNOME?" in the Troubleshooting section of the UbuntuGuide

7. Think you are done setting up? You can now configure your network/internet connections

**System -> Administration -> Networking**

8. Optional: If you have fast internet connection, issue these commands:

[b]sudo apt-get update
sudo apt-get upgrade[/b]

*This will connect online and then update your Ubuntu

9. You are now ready to rock!

---

