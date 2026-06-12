---
title: "Ubuntu's Great but grubenv environment block is too small"
date: 2014-09-09
forum: New to Ubuntu
---

### Post by wxtz.1a3c2b on 2014-09-09
Been working out a remote pc for a ssh server.
Everything was going great but then,,,
I was alternately booting from SD card and from SSD (Ubuntu 14.04 little Tahr baby )
I was booted into the SD card and thought how I would boot 
into the SSD (since I had default boot pointed to the SD card).
Guess I could just mount the SSD partition and edit the grubenv next_boot
entry to 0 and that would boot the SSD partition.
Worked great!
But then later I tried to set the next_boot to Mint on /dev/sda1 and grub
gave me grubenv environment too small.
Not sure if the editing screwed things up.
I've deleted grubenv and recreated it using 
grub-editenv grubenv create
grub-editenv grubenv set default=0
grub-editenv grubenv list
update-grub
[FONT=arial]But still get get environment too small after booting. (It asks to hit enter and then boots into SDD partition)
I've also reinstalled grub using
sudo mount --bind /dev /mnt/dev &&
sudo mount --bind /dev/pts /mnt/dev/pts &&
sudo mount --bind /proc /mnt/proc &&
sudo mount --bind /sys /mnt/sys
(etc,,,,,,, method)
but it still comes up with the warning of environment too small.

Mint boots great so it must be something like a flag only on the Ubuntu partition.

Could someone please help me on this?
I don't want to have to reinstall, and I'm so curious as to why this is happening.

thanks bunches !!!!!!!
[/FONT]
Reminds me of the time I deleted the swapfile in Windows 3.1
and couldn't boot. A co-worker said I was teasing Windows
and it don't like that !!!!

---

### Post by wxtz.1a3c2b on 2014-09-09
Okay,,,
Just commented out the recordfail in grub.cfg
and now it boots fine but....
I know update-grub will just reset that next time.

Thanks.

---

### Post by wxtz.1a3c2b on 2014-09-09
Issued: sudo grub-reboot 2      and this happened

/usr/bin/grub-editenv: error: environment block too small.

Trying to decipher the shell code but Golly Gee Wiz !!!!!!!!!

Can't get a handle on what flag/file/? is causing this.

---

### Post by wxtz.1a3c2b on 2014-09-09
So now I partcloned my SD card.
Created a new partition on the SSD (sda3).
Restored the partclone img to sda3.
Created 40_custom to point to sda3, and edited the menuentry to TinySD2.
I booted into sda3.
I removed the boot flag in cfdisk and put it on sda3.
Ran grub-install, update-grub, re-edited menuentry to TinySD2.
Reboot now.
Works great !!!!!!
No message for grubenv being too small.
Now to boot the troublesome sda2.

Let's see what happens!!

---

### Post by wxtz.1a3c2b on 2014-09-09
Google !!! Er, I mean Yahoooooooooo !!!
Works ----
No grubenv message.
Now I will mount sda2 and rewrite /boot and every thing beneath it from sda3
and see what that does after making sda2 bootable, grub-install, update grub.

Fingers crossed.

---

### Post by wxtz.1a3c2b on 2014-09-09
So........
I ran a diff to see any files on one partition not on the other. 
diff --brief -r /boot /media/TinySD > compare.txt (after mounting the bad grub partition)

[FONT=arial]Only saw core.img was different, but no files containing any flags for a bad grub condition.

I gave up and found this excellent Ubuntu forum post by   [B]drs305  ( [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) )
[/B][**[COLOR=#DD4814][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=223945")[/FONT]**[FONT=arial][/FONT]**[FONT=arial]explaining how to purge grub and reinstall using apt-get.
First I found the packages installed on my system because I know that I have grub2 installed.
dpkg --get-selections | grep -v deinstall > my_installed_pkgs.txt
[/FONT][FONT=arial]Followed the guide and purged and reinstalled grub2-common and others.

Now my orignal partition boots like it should!!!!!!!!!

Wish I could have fixed another way and found out what happened ?????????

Now I'm going to do the same thing I thought caused the problem to confirm,
now that I know how to fix it.

Marking solved, but not understood..........

thanks bunches.
[/FONT]

---

