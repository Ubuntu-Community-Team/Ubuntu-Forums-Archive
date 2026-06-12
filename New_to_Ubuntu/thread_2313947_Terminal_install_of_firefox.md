---
title: "Terminal install of firefox"
date: 2016-02-17
forum: New to Ubuntu
---

### Post by Thomas_Hillard on 2016-02-17
I have Ubuntu 10.1 and want to install a new version of Firefox. I have downloaded the tar bz2 file from their website. I have it in my Downloads folder along with an extracted file folder Firefox. I guess I can remove the old version in Terminal with: sudo apt-get remove firefox. My question is, what Terminal command string do I use to install the new tar file? I guess it will have to point to the extracted folder or the tar file in my download folder.

I can run the new Firefox from the download firefox folder but it will not save any of my bookmarks when closed.

---

### Post by ajgreeny on 2016-02-17
Ubuntu 10.10 has been out of support for a very long time and the reppositories have been archived, so you will not be able to easily install anything now, and whilst firefox version 44 (I presume?) can be downloaded from mozilla direct, and may run from the firefox executable in the archive without installing, it is not advised and you will get little help here, as forum users no longer run that version of Ubuntu.

Upgrade to a supported version of *Ubuntu and we will try to help as much as possible.

---

### Post by Dennis N on 2016-02-17
You are talking about the Mozilla-direct version (directly downloaded from Mozilla). I have used it several times, and to "install" it, simply move the firefox folder from the archive to it's permanent location and edit or create the launcher. You can just leave the existing Firefox alone, but if you intend to switch between them, they need separate profiles created with the Firefox profile manager.

I always place mine in /opt. Edit the command in the existing launcher to use the new Firefox, or create a new launcher for it. To create a new one in Xubuntu, I use menulibre, the menu editor. It essentially makes the .desktop file for you. 

On first launch, the new Firefox will use your old profile as much as possible, or you can create a new one.

It's all pretty easy to do.

EDIT: Overlooked that you are using 10.10 which is pretty old. As aj suggests, you should update - and with that comes a new version of Firefox. Your choice in the end.

---

### Post by buzzingrobot on 2016-02-17
Mozilla posts instructions for installing Firefox from the archive they release for Linux. 

The release you are using, however, is so outdated that I wouldn't be surprised if you see some support issues with current Firefox releases.

It's beyond time to upgrade.;)

---

### Post by Dennis N on 2016-02-17
Along the same line, you also need to update the flash player - another do-it-yourself install job for you, should you go this route.

---

