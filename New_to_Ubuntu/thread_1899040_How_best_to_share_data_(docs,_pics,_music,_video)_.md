---
title: "How best to share data (docs, pics, music, video) from /home partition with win drive"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by mikodo on 2011-12-22
I  keep my /home in a separate partition, for easy backups and clean installs. I would like to install another drive for XP/win7 and have it share my docs, pics, music and video.

I will be eliciting the help of a professional for this, as I don't trust my casual-newbie skills, with my data. Also, my time is best spent doing, for what I get paid, to do. Soon, I retire... then I can spend more time learning!

Thinking down the road, I might want a home data server to connect with the T.V.'s too; but not now.

Here's my only drive now, with /dev/sda5, being my /home partition.

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       38914   293038081    5  Extended
/dev/sda5            2432       38119   286658067+  83  Linux
/dev/sda6           38184       38914     5859328   82  Linux swap / Solaris

What might, be my options? 

A Vbox install sharing data?

Dual-booting?

Samba sharing between them? 

I will take any and all suggestions to my IT guy.

Thanks.

EDIT:  I am using Ubuntu 10.04 Lucid Lynx. I will be going to Xubuntu after EOL. I keep hitting Lubuntu by mistake.

---

### Post by oldfred on 2011-12-22
Some like virtual installs, but I have not tried it.

I like dual boot as you get full speed, but you do have the hassle of rebooting.

I have shared a NTFS ( was fAT32 originally)  partition with my XP on a separate drive since I built this computer.

I like smaller system partitions and larger data partitions. I have separate data for NTFS and ext3 since I use XP very little now, most data goes into the Linux data partition. But I still have my Firefox & Thunderbird profiles in the NTFS partition and share all data in multiple systems with that NTFS partition.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by mikodo on 2011-12-22
Thank you oldfred:

Reading [this link]("http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/") you provided, shows that I can move my "data" from my /home partition (ext4 FS), into a media HDD/partition that uses  NTFS, that then can be read by both Linux and Windows. I wasn't sure that I could do that. That was what I needed clarification on, along with how to do it; but then, my IT guy will do it for me though.

I will then just have to configure a backup system a little differently. According to the article listed above, I can still have my /home partition, if I want, to use in clean/fresh installs.

All this, and I haven't even read, the rest of the guides/links you provided!

Thanks again!

---

### Post by oldfred on 2011-12-22
You are welcome.

My /home became so small after I moved all my data out, I stopped doing a separate /home. It is small enough to be easily backed up. But I do clean installs into a new 25GB / partition so I can go back and copy something else that I may have missed. My /home has about 250MB of user settings and about 1GB of .wine (Windows version of Picasa). My understanding is that wine is a lot more difficult to move out of /home.

---

