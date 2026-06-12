---
title: "Ghost-ing Ubuntu To Fresh HDD"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by CrazyCanuck on 2008-05-26
Hello my friends.

I was wondering if it is possible to use Symantec's Ghost utility, to clone an Ubuntu disk which is fully installed, to an empty hard drive.

My idea is rather simple.  I am finalizing my Ubuntu Hardy drive as we speak, and as I am beginning to realize, I am going to need a bigger hdd other than my existing 10 gig hdd I currently have my Ubuntu OS on.  Once the installation process is concluded, I will want to put it on a bigger drive.  I am not considering doing a dual-boot with WinXP at the current time, simply because I am not understanding the dual-boot process fully.  For now, I would like to finish my Hardy install then transfer the data to a new drive.

Anyone here done this already?  Please let me know.  :)

CC

---

### Post by Duck2006 on 2008-05-26
You can use the DD commands to do this.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

or use part image

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by CrazyCanuck on 2008-05-26
Thanks a lot!

CC

---

### Post by bumanie on 2008-05-26
I think if you are relatively new to linux, it would probably be easier to do a fresh install on the larger drive. dd commands and part image aren't programs suitable for the inexperienced, (although they do work well). If you don't understand dual booting, I doubt you will understand how to use those programs.  I know you can copy partitions with gparted live cd and that should not cause problems as ubuntu reads the UUID allocated to the hard drive partition rather than the actual partition drive/number - I would still go for a fresh installation. I would consider dd etc. if I was going to lose heaps of data, but as you said in your post 'once the installation has finished', makes me think you have no data to worry about.

---

### Post by CrazyCanuck on 2008-05-26
I am a computer techie for 20-odd years.  ;)

I fully understand how to dual-boot using non-Linux methods.  I am simply new to Linux and its command structures.  I will tread carefully and do much reading before doing anything concerning dual-booting Ubuntu with a MS product.  In fact, if I am able to do that which is needed to do business work, and some fun on the side, then MS is a thing of the past for me and I will have no need to dual-boot.  As it is, I am looking for replacements for some things I use within WinXP.

Such as, Sound Forge 6.  I LOVE this program for all that it does for me.  I do not know of an equivalent within the Linux universe.  I wish I did.  If I can find replacement packages within Linux, my need to dual-boot simply vanishes.

I have a 10 gig hdd, and a 250 gig hdd.  Now that my install of Ubuntu is complete, I have a 5.5 gig footprint on a 10 gig hdd!  How phenomenal!  My business side of computing is complete, minus the printer and other things I may need to attach to my Linux box.

I will soon be uninstalling MANY applications from WinXP seeing as I have found many replacement packages already.  So as you can see, the need to dual-boot is there only IF I cannot find replacement software for existing things I use within WinXP.  :)

Thanks for the cautious response, I respect that very much.  Have a nice day please.

CC

---

### Post by SlappyPappy on 2008-05-26
I started on a 20GB drive as a test to see if Ubuntu would work for me. It did and I didn't want to have to reinstall everything when going up to a larger HD. Well a bunch of people warned me to not clone as it would leave errors. I said, hey, might as well try, I'll probably learn something along the way.

Well I moved from a 20GB to a 60GB drive and no problems. All I had to fix after cloning was a UUID in fstab which is dead simple to do. Then I cloned a few weeks later from the 60GB to a 120GB drive. Same fix with the UUID and no problems! It works awesome. Let's see you do that in Windows!

Here is the tutorial I found that works a charm:

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

Good luck friend!    :)

---

### Post by cwmoser on 2008-05-26
I used Norton Ghost once and was unsuccessful.  Perhaps, my version of Ghost did not support EXT3 partitions.

I was successful in cloning my Ubuntu partitions to another hard drive using this procedure:

Don't need Norton Ghost use the command cp  -a instead
You need to boot off the CDROM so that neither the source partition nor the target partition is mounted.
Procedure:
Assume in the following example that we are copying /dev/sda6 to /dev/sdb1:

1.Boot Ubuntu CDROM
2.Click on Terminal in order to get command prompt
3.Run fdisk to create partition:
sudo  fdisk  /dev/sdb
p			<- display partition table
n  then  p	<- create a new primary partition
	NOTE:  If you have Windows XP, you can use it to create the partition &#8211; but	don't format it.
4.sudo  mkfs  -t  ext3  /dev/sdb1		<-- make file system, format it
5.sudo fsck /dev/sdb1				<-- check fs
6.mkdir  /tmp/sda6				<-- mount points
7.mkdir  /tmp/sdb1
8.sudo  mount  -t  ext3  /dev/sda6  /tmp/sda6	<-- Source
9.sudo  mount  -t  ext3  /dev/sdb1  /tmp/sdb1	<-- Target
10.cd  /tmp/sda6				<- go here to start copy
11.sudo  cp  -a  *  /tmp/sdb1			<- copy relative to this


Now setup grub and the menu.lst file so you can boot the new partition.


Carl

---

### Post by CrazyCanuck on 2008-05-26
CWMOSER:  hey brother!  Thanks for your alternative suggestion.  I like knowing there are several ways to do a disk clone.  Allow me to quote you then respond:

"Don't need Norton Ghost use the command cp -a instead
You need to boot off the CDROM so that neither the source partition nor the target partition is mounted.
Procedure:
Assume in the following example that we are copying /dev/sda6 to /dev/sdb1:

1.Boot Ubuntu CDROM
2.Click on Terminal in order to get command prompt
3.Run fdisk to create partition:
sudo fdisk /dev/sdb
p <- display partition table
n then p <- create a new primary partition
NOTE: If you have Windows XP, you can use it to create the partition &#8211; but don't format it.
4.sudo mkfs -t ext3 /dev/sdb1 <-- make file system, format it
5.sudo fsck /dev/sdb1 <-- check fs
6.mkdir /tmp/sda6 <-- mount points
7.mkdir /tmp/sdb1
8.sudo mount -t ext3 /dev/sda6 /tmp/sda6 <-- Source
9.sudo mount -t ext3 /dev/sdb1 /tmp/sdb1 <-- Target
10.cd /tmp/sda6 <- go here to start copy
11.sudo cp -a * /tmp/sdb1 <- copy relative to this


Now setup grub and the menu.lst file so you can boot the new partition.


Carl"

Ok, due to my new-ness (YES I love being a noob within the Ubuntu Universe) I suppose I will need to learn all about GRUB and menu.lst; meaning:

1) I understand GRUB is the booter for Ubuntu, but as with all things new to someone, I do not have knowledge on GRUB...so I do not know how to set it up currently.  Shall look at a GRUB tutorial or something, because I want to put GRUB on a memory stick and make my Ubuntu business box rather secure by inserting the mem stick on bootup, then removal of mem stick at days' end.  Voila, instant security from local access.

2) Where is menu.lst located please?

As I look at both examples of disk cloning, I am needing to know both techniques, oddly enough!

Thanks for your input.

CC

---

### Post by lazyart on 2008-05-26
when i moved from a 40 gig to a 120 gig drive I used the Clonezilla live cd.  Done in one try, no menu editing.

---

### Post by CrazyCanuck on 2008-05-26
Lazyart, sorry but could you please elaborate a little more?

Thanks.

CC

---

### Post by cwmoser on 2008-06-11
Last week I completely trashed my Gutsy OS and loaded Hardy in another partition.  I saved my trashed Gutsy and this week went back to look at it.  I used cp -a as above to copy back my partition to my main hard drive from my saved cloned drive.  Still there was no booting this partition because Grub was not set up.  I then took the Hardy Alternate Desktop cdrom and did a "Rescue" and instructed it to put Grub back on and now it will boot all my my instances from the menu.

So, that is one way to get the grub boot menu put back on.  I think a command something like grub-install does the same thing.

Carl

---

