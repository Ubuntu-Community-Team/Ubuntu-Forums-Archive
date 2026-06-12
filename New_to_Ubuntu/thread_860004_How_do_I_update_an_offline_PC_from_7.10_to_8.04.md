---
title: "How do I update an offline PC from 7.10 to 8.04?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by mb-editor on 2008-07-15
Hi,

I have an off-line PC on which I'd installed 7.10.  I now want to upgrade it to 8.04; have even got the CD from Canonical, but when I put it in, the CD reads, but nothing happens.

I tried using the command gksu "sh /cdrom/cdromupgrade" in the terminal, but got the response "Cant open /cdrom/cdromupgrade".  I'm now confused: am I running the wrong CD? (the tutorial said use 'alternate' CD - wonder what that means).

Incidentally, I tried the same CD on a PC that was net-enabled; same thing happened, but when I selected 'upgrade' from the software update manager, it asked for the CD to be put in the tray.  I did, and Ubuntu upgraded to 8.04 thereafter.  I'm not sure now whether the packages were downloaded from the net or taken from the CD.

Help, please!

---

### Post by hyper_ch on 2008-07-15
do you have the alternate cd?
did you enable cd-rom as source?

---

### Post by mb-editor on 2008-07-15
I've enabled the cd-rom as source, but am getting the same results.

As for the alternate CD, I'm confused: isn't it the same CD that I got from Canonical?  Bcoz when I look at the upgrade page on Ubuntu.com, I get the instruction "Download and burn the alternate installation CD." but that's not a hyperlink, so I'm assuming its the same.

Am I wrong?

---

### Post by roachk71 on 2008-07-15
Many distributions use /cdrom as the node for a CD-ROM drive, but that's been shifted to the /media hierarchy in Ubuntu. You should find either cdrom/ or cdrom0/ in this directory; at least one should point you in the right direction.

This assumes, of course, that the drive is recognized by the kernel and registered in /etc/fstab.

---

### Post by Ryadt on 2008-07-15
You can download the alternate cd from the ubuntu homepage. Just make sure you check the box where it says "check if you need alternate cd.."

---

### Post by kunixos on 2008-07-15
You should have the Alternate Installation CD from your description.

As far as enabling the CDROM as the source, did you do this:
```
sudo apt-cdrom add
```
If you did, then you should (after ensuring that every other source in /etc/apt/sources.list is commented (#) out) be able to do a:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Does this help?

Also, check out [this]("https://help.ubuntu.com/community/AptCdrom") and [this]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion") for more information on upgrading your system to the latest version with the CDROM source.

Hope it works!

---

### Post by Troll_the_Great on 2008-07-15
The alternate CD is not the same as the live CD you got.You have to download it, burn it to a CD and then perform the upgrade.If you don't have an internet connection download it from a friend or form an internet cafe and try again the upgrade.
But my advice is to back up all your important data, make a list with your installed programs and settings and do a clean install.It is always better to make a clean install then an upgrade.You will have less problems and head aches :).
Cheers!

---

### Post by kahlil88 on 2008-07-15
If you got the CD from Canonical, then it's probably the regular install disc (as opposed to the "alternate" one, which you need for upgrading). But fear not, I made the same mistake you did, and I have a clever solution! Boot from the install CD and create a folder called "backup" in the TOP directory (**mkdir /backup**), then move everything you care about into there (probably just your Home folder), go ahead with the install and then move everything back when it's done.
I'm kinda glad I did it this way, because I heard that a lot of people were having problems upgrading from Gutsy to Hardy.

**[COLOR="Red"]Keep in mind, this is a potentially risky method - everything that isn't in the /backup folder will be erased. So be very careful not to forget any important files and double-check that your data is in the /backup folder. If you have any questions, check back here before trying anything.[/COLOR]**

---

### Post by mb-editor on 2008-07-15
Yup; both cdrom/ and cdrom0/ are there.  Thanks for the great help people - will check it out tomorrow when back in office.

I think I'll have to eventually download the alternate - thanks for the tip Ryadt; I didn't notice the check box till you pointed it out.  As for the mkdir /backup option, I'm too scared!  Too many locations on the PC, actually.  I think I'll try *that* on a junk PC lying around, just to see how that goes :)

---

