---
title: "Help with removing 7.10 and using a PCI card."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by SilverGoldBronze on 2008-04-27
i just made a CD to install Ubuntu 8.04 LTS on my computer. This isn't the first time I've installed Ubuntu, as I have 7.10 as well. The install went smoothly, but that's as far as I got. First of all, installing 8.04 did not remove 7.10, and now I have two Ubuntu operating systems. Secondly, I cannot use my Belkin wireless G desktop card, so I went to Synaptic Package Manager to download Ndiswrapper, or ndisgtk. Neither of the two exist, even though Ubuntu says they should, so I wonder what I am supposed to do to connect my Ubuntu desktop to the internet. As of now I am using XP, but I want to switch fully to Ubuntu, though I installed both 8.04 and 7.10 on a second and third partition so that I could make sure they would work. Please help me figure out how to remove 7.10 and also use my windows wireless Belkin driver on Ubuntu.

SilverGoldBronze

---

### Post by Hospadar on 2008-04-27
Due to their licensing issues (since they load non-open source drivers into the kernel) ndiswrapper and ndisgtk are located in the multiverse or universe repos (I believe).  If you go to System->Administration->Software Sources and check the "universe" and "multiverse" repos, then you should be able to get these through synaptic.

This would of course require you to have an internet connection, so either: use an ethernet cable temporarily or, download the packages manually from the package website: [http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages) (it's a big page, so get ready for load time).  Also, I don't think ndiswrapper really has any non-standard dependancies, so you shouldn't have to download anything else, but pay attention while you are installing ndiswrapper, if it complains about dependancies, then go back to the package site and grab whatever it asks for.

You'll be downloading .deb files, you can double click them to install, or use the terminal ```
sudo dpkg -i ThePackageYouDownloaded.deb
``` where ThePackageYouDownloaded.deb is the filename of the deb you downloaded

---

