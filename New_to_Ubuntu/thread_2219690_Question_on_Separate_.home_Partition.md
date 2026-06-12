---
title: "Question on Separate ./home Partition"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-04-25
I understand when upgrading you select Maunal and point the new install to the **./** partition for the new OS and to preserve the old **home** set up/config you point to the **./home** partition and select not to format.  I haven't done this (yet) but can you confirm that by not selecting to format the install will not install any home folders (Desktop, Documents, Downloads, etc) in either the **./** partition or **./home** partition.  As a side note - if you do a normal install (no separate **./home** partiton) and choose not to format I assume the install will take place - this means that when you have separate partitions the format option (for the **./home** partition) takes on a whole different meaning.  The install will install **./** but not **./home** - clever if this is how it works.

---

### Post by sudodus on 2014-04-25
There should be absolute paths, not relative to the current directory, so the dots should ***not*** be there in

/ for root partition

and

/home for home partition

(I will not reply to the general question here, because you need unbiased input from other persons.)

---

### Post by Lars Noodén on 2014-04-25
Having a separate /home partition will allow you to format the system (/) yet leave you user files as they are.  I have used that method for upgrades (actually fresh installs) almost since I started with Ubuntu, and recommend it highly.  Just make sure you are pointing to the right partitions.  You can see what you currently have using the [mount](http://manpages.ubuntu.com/manpages/trusty/en/man8/mount.8.html) utility with no options.  That will give you a list of everything mounted and then you can write down which partitions are used for root and /home.  

However, please do a proper backup anyway before trying any installation or upgrade.  Accidents do happen and it's better to have a good backup and not need it than the other way around.

---

### Post by sudodus on 2014-04-25
[http://askubuntu.com/questions/278160/use-existing-home-not-encrypted-when-installing-ubuntu](http://askubuntu.com/questions/278160/use-existing-home-not-encrypted-when-installing-ubuntu)

[http://askubuntu.com/questions/56051/reinstalling-ubuntu-without-formating-home-as-well-as-without-any-old-config-f](http://askubuntu.com/questions/56051/reinstalling-ubuntu-without-formating-home-as-well-as-without-any-old-config-f)

[URL="http://ubuntuforums.org/showthread.php?t=2136407"]Reinstall Ubuntu with **Existing Home Partition**?
[/URL][[SOLVED] Re install Ubuntu but keep /home]("http://ubuntuforums.org/showthread.php?t=1569675")[URL="http://ubuntuforums.org/showthread.php?t=2136407"]
[/URL]

---

### Post by 3rdalbum on 2014-04-25
> **Quarkrad said:**
> I understand when upgrading you select Maunal and point the new install to the **./** partition for the new OS and to preserve the old **home** set up/config you point to the **./home** partition and select not to format.  I haven't done this (yet) but can you confirm that by not selecting to format the install will not install any home folders (Desktop, Documents, Downloads, etc) in either the **./** partition or **./home** partition.

That's correct, it won't touch your /home at all. I literally did this today!

> As a side note - if you do a normal install (no separate **./home** partiton) and choose not to format I assume the install will take place - this means that when you have separate partitions the format option (for the **./home** partition) takes on a whole different meaning.  The install will install **./** but not **./home** - clever if this is how it works.

Yes, the install takes place, and it preserves your /home as long as you don't format /. It also makes note of what software you have and then reinstalls that software from the new repositories. Pretty clever, but surprisingly few people know about it.

---

### Post by cwmoser on 2014-04-25
Something you might want to know is you can move your /home to another partition on your hard drive
after you have Ubuntu installed.

On boot up, Ubuntu uses **/etc/fstab** to locate where /home is on the hard drive.
My /etc/fstab file has this entry for /home:
[B]# Use /dev/sda3 as /home ...
UUID=006fba9b-f027-48b7-96ec-832d93ac9711 /home          ext4    defaults           0       2[/B]

When I was configuring Ubuntu 14.04, I moved my /home to another partition simply by editing that
file, changing the UUID, and copying the /home data to the new partition.

You can enter  **sudo  blkid  -o  list ** to find the association of UUID and /dev/sdxx associations.

---

### Post by Quarkrad on 2014-04-25
Thank you all - this beast (ubuntu) is more clever than I thought (in terms of installing).

---

