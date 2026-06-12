---
title: "Downloading Ubuntu Through Torrents"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by albertbertal8 on 2008-04-24
Which torrent do I download so that I can upgrade my installation of ubuntu to 8.04 without formatting my harddrive?  Also, if I download the torrent, do I have to burn it to a cd or dvd to use it or can I just upgrade it straight from there like it does when you use the update manager?

---

### Post by Fire_Chief on 2008-04-24
Use torrent found here
[http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso.torrent]("http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso.torrent")

You'll need to burn it to a CD and then you can read the CD to perform the upgrade.

Cheers!

---

### Post by ugm6hr on 2008-04-24
I think you need the AlternateCD torrent to do an upgrade.

But you will need to burn a CD.

---

### Post by Calash on 2008-04-24
This may be redundant, but the wording of the question worried me a bit.

A torrent is not an installer.  It is a small file that lets you use a torrent client to download the ISO file.  The ISO is what gets burned to a CD.

What do you currently have on your hard drive?  If it already has a version of Ubuntu it would probably be safer to run the upgrade.

---

### Post by macogw on 2008-04-24
Burning's not really necessary.  You can mount the iso.  [http://www.acc.umu.se/~mighty/ubuntu/ubuntu-8.04-alternate-i386.iso.torrent](http://www.acc.umu.se/~mighty/ubuntu/ubuntu-8.04-alternate-i386.iso.torrent)

---

### Post by Ghostlove on 2008-04-24
Can I please confirm from someone in the know that the following link:

[http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso.torrent](http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso.torrent)

is to the torrent file for downloading the right CD for upgrading rather than a fresh install? The automatic upgrade thing was taking ages so I assume the servers are taking a bit of a battering, so I'd prefer to download it via torrent.

So... have I got it right?

---

### Post by albertbertal8 on 2008-04-24
Wait, you guys gave me two different torrents.  Should I use the alternate one or the other one?

---

### Post by macogw on 2008-04-24
alternate is the one for upgrading

---

### Post by ace007 on 2008-04-24
EDIT: I think I'm confused.

I think you are confused.  By downloading the desktop ISO via the torrent, you will be downloading an installation disc for installing a fresh version of Ubuntu.  If you are looking to just upgrade then use the update manager like you were.  Or, it is possible to use the alternative CD to do an upgrade, I've never done it that way.

---

### Post by macogw on 2008-04-24
> **ace007 said:**
> I think you are confused.  By downloading the ISO via the torrent, you will be downloading an installation disc for installing a fresh version of Ubuntu.  If you are looking to just upgrade then use the update manager like you were.  The ISO is a FRESH install method.

the alternate cd can be used as a local repository for upgrades

---

### Post by Perfect Storm on 2008-04-24
> **albertbertal8 said:**
> Wait, you guys gave me two different torrents.  Should I use the alternate one or the other one?

Depends... The Desktop one is with bling-bling installation guide and LiveCD. The alternate is for if people have trouble with the Desktop/live CD. The alternate comes with an easy-of-use text installer. Alternate can be used to upgrade already existing Ubuntu.

---

### Post by albertbertal8 on 2008-04-24
Alright, thanks guys. :)

---

### Post by ptcbus on 2008-04-24
I upgraded and used alternate setup torrent. I have listed the steps I followed here: [http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/]("http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/")

---

### Post by Endolith on 2008-04-24
> **macogw said:**
> Burning's not really necessary.  You can mount the iso.

You're gonna have to explain how.  Simply saying "you can mount it" doesn't help most people.  Is there an application for this or do you have to dig into virtual file systems?

...

This was not as easy as I thought, but I got the upgrader working:

1. Download the alternate install ISO file through the *.torrent* file on [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
2. mount using a command like ```
sudo mount -o loop ~/Desktop/ubuntu-8.04-alternate-i386.iso /media/cdrom0
```
3. start the upgrader with the command ```
sudo /media/cdrom/cdromupgrade
```

It did **not work** from any location other than the /media/cdrom/ link.

And on release days, you probably want to click "no" when it asks about downloading the latest upgrades from the Internet, since the servers are so bogged down it will have to abort the upgrade process and you'll have to start all over again.  You can always get them later.

---

### Post by -Phi- on 2008-04-25
> **Endolith said:**
> It will **not work** from any location other than the /media/cdrom/ link.
I mounted the .iso using a [Thunar script]("http://ubuntuforums.org/showthread.php?t=380602") and the upgrade worked fine for me from /mnt/xubuntu-8.04-alternate-i386.iso by hitting Alt+F2 and running```
gksu "sh /mnt/xubuntu-8.04-alternate-i386.iso/cdromupgrade"
```Which was a variation on what the [Hardy Upgrade]("https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d") page suggested.

- Phi

---

### Post by d_rwin on 2009-08-29
> **Endolith said:**
> You're gonna have to explain how.  Simply saying "you can mount it" doesn't help most people.  Is there an application for this or do you have to dig into virtual file systems?

...

This was not as easy as I thought, but I got the upgrader working:

1. Download the alternate install ISO file through the *.torrent* file on [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
2. mount using a command like ```
sudo mount -o loop ~/Desktop/ubuntu-8.04-alternate-i386.iso /media/cdrom0
```
3. start the upgrader with the command ```
sudo /media/cdrom/cdromupgrade
```

It did **not work** from any location other than the /media/cdrom/ link.

And on release days, you probably want to click "no" when it asks about downloading the latest upgrades from the Internet, since the servers are so bogged down it will have to abort the upgrade process and you'll have to start all over again.  You can always get them later.

Upgrade from 7.10 to 8.04
Better option with Network Upgrade from terminal, just for slow network connections and torrent limiting ISP :KS

Steps:: 
```
$sudo vim -v /etc/apt/sources.list
```
change non commented lines: ['us'.archive]&[security]->[old-releases].ubuntu.com
```
$sudo apt-get update
```
```
$sudo apt-get dist-upgrade
``` better than upgrade(less bandwith)

Note: revert [old-releases]->[us.archive]&[security].ubuntu.com before do-release-upgrade. check [security] for gutsy-security

now You have a perfect upgraded PC check it::
```
$lsb_release -a
``` you will have 7.10(gutsy)

Now release upgrade::
Note:: do-release upgrade before changing to *original*(us.archive) and allowing it to modify sources.list will corrupt your distro. do-release-upgrade changes the [gutsy] to [hardy]
```
$sudo do-release-upgrade
```

---

### Post by bapoumba on 2009-08-29
this thread is outdated. Closing. Please feel free to PM if you want it reopened.

---

