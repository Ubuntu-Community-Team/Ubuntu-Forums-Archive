---
title: "Device for bootloader installation?"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by Sly14Cat on 2012-08-20
I'm in the middle of installing Ubuntu and I need a fast answer.
I choose "something else" for installing Ubuntu then choose the empty space I created in Ubuntu. I format it as ext4 and I'm installing the bootloader to /dev/sda. So to fix it I'm setting the mount point to /. So will I need to create a swap space by shrinking the Ubuntu partition by 8gb (my ram)and create a logical partition and make it /swap?

---

### Post by Sly14Cat on 2012-08-20
I'm in the middle of installing Ubuntu and I need a fast answer.
I choose "something else" for installing Ubuntu then choose the empty space I created in Ubuntu. I format it as ext4 and I'm installing the bootloader to /dev/sda. So to fix it I'm setting the mount point to /. So will I need to create a swap space by shrinking the Ubuntu partition by 8gb (my ram)and create a logical partition and make it /swap?

---

### Post by darkod on 2012-08-20
The swap partition is usually created but it can work without it too. It will only ask you if you are sure you want to continue without swap.

But why don't you do this: Delete the single ext4 partition you created (you can do it in the manual partitioning step of the installer if you still have it open), and after that create the root partition 8GB smaller. Then create swap partition from those 8GB.

Also, when swap is created the Use As field is 'swap area' and it doesn't have a mount point.

---

### Post by Bashing-om on 2012-08-20
sly;
 Somewhat unclear as to your quest;
 Grub ie bootloader ....  if you only have the one disk: Install grub to sda .
swap: if you do not intend to hibernate or suspend .. and you have 2 megs or more of ram .....you can do without a swap (but it is not advised) .
boot: are you installing to a separate partition? I set the boot FLAG in Gparted.
  the final screen in the installer has an advanced option ..click on it and insure grub is going to be installed where you want it to install.

[INDENT]does this help <==BDQ

[/INDENT]

---

### Post by Sly14Cat on 2012-08-20
How would you flag the boot?
Thanks for clarifying the sda thing.
Yes, I do use hibernate a lot so was my method correct for creating a swap space?

---

### Post by oldfred on 2012-08-20
Grub does not use the boot flag, Windows has to have a boot flag on a primary partition to boot or repair its partition. But a few BIOS require a boot flag or they will not let you even start to boot.  So you may not need it on the Linux partition but you should have one on a primary partition. 

You can use gparted when creating partitions or anytime. Select partition and right click set flags. You can also use Disk Utility or command line.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by oldfred on 2012-08-20
@   	Sly14Cat
Please do not create duplicate threads on the same topic. We are all volunteers here and need to see if question has already been answered or if we can add to the previous answers.

---

### Post by Sly14Cat on 2012-08-20
Sorry about duplicating the threads I knew I'd get caught eventually. I just needed a quick answer because I was half way though the installation and I was not sure how long I had left until I had to power down and attend to other things.

I jut had a quick question that may make this a lot simpler, could I just give Ubuntu the minimum amount of space possible (using the dual boot slider) and just repair windows if any problems arise. The minimum I can give is 69gb and the windows disk is at 0 percent fragmentation. If not how would I flag a bootloader? Why would I need to do this?

Edit: Sorry I just reread how to set a boot flag I also only have 1 important file and it is/will be backed up.

---

### Post by Bashing-om on 2012-08-20
sly14cat;

  Your anxiety is making this much more difficult than it is (believe me!).
If you used windows disk manager to resize (shrink) windows; used the ubuntu installer to format the leftover - from - windows- free space as a primary partition (can only have 4 partitions to the disk), formated to ext4----
until you get exotic ...let the installer install / (root) and swap and you are good to go ...as darko advises ... 8 megs for swap all else for the operating system(/)..
at the final screen check on what the advanced option sets grub to install to (sda)...grub will install and pick up your windows to chainload it ... ubuntu is very smart(generations of great programmers); as time goes by you will be muchly impressed!  

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Sly14Cat on 2012-08-21
So I did everything and at the install it stalled at around 57 out of 129 files. I didn't tick updates or 3rd party software. But even though it says I'm connected to the internet, when I got to a website in Firefox I can't get any pages. Could I get any help please?

---

### Post by oldfred on 2012-08-21
When you say Firefox, are you still in LIveCD or your install? It may have been updating so did install complete? Did Internet go down for a minute?

Can you boot or boot in recovery mode.

Then see if you can complete updates.

From Terminal:

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop


If you get any error messages post those.

---

### Post by Sly14Cat on 2012-08-21
I tried Firefox in the LiveCD and during the install. I'll try doing the install wired to the router instead of wireless and see how that goes tomorrow.

But during the install freeze I clicked shutdown and everything returned to normal and booted into windows. Like I said I'll try again tomorrow and see if wiring to the internet will work. I'll also tick install 3rd party software and updates.

---

### Post by oldfred on 2012-08-21
It wants to download updates, and it often is best to let it also install all the third party drivers right away. But if you do not have have hard wired Ethernet then it can be an issue if wireless driver is not part of the standard install and many wireless are not part of standard install.  Or use wired install at least for initial install.

See also this thread, which happened to be next.
[http://ubuntuforums.org/showthread.php?t=2045654](http://ubuntuforums.org/showthread.php?t=2045654)

---

### Post by Sly14Cat on 2012-08-21
Alright then I'll tick both options and wire the Ethernet and see how it works and tell the forums tomorrow and hopefully I'll be able to mark this SOLVED.

By the way I wanted to say that I didn't make a swap because it when I make the swap then the Ubuntu partition, the Ubuntu partition doesn't ask me if I want it to be logical or primary. But if I make the Ubuntu and leave 8gb. It calls the remaining 8gb (unusable). Could I make a swap after the install? I always use hibernate.

---

### Post by oldfred on 2012-08-21
If you have used all 4 primary partitions you will not be able to make a swap partition. You have to have the extended partition so you can add logical partitions. Often difficult to move things around with data in them.

I use a swap partition, never hibernate as it boots fast enough for me and then I avoid all the hibernation issues. 

HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)
I prefer sleep and shutdown to hibernate.
'Dynamic Swap Space Manager' from the Ubuntu Software Center

---

### Post by Sly14Cat on 2012-08-21
Now that I think about it, it does boot fast enough that I wouldn't worry about hibernation.

Could after the install if I wanted more room for Ubuntu, shrink the windows partition in windows and use gparted to extend the Ubuntu partition?

---

### Post by oldfred on 2012-08-21
I always prefer smaller system partitions for the operating system for both Windows and Linux. Then you use a data partition. If dual booting with Windows you make the data partition NTFS and can read and write from both systems into the shared data partition. Windows does not like too many writes from foreign systems, so you then can set Windows as read-only.

You can move partitions around. But the more data your have and the more you move the higher risk. You must have good backups. And power failure or interruption to the partition move corrupts the system and a reinstall is about the only solution. But many of us have moved partitions without issues. And other come in asking for help without backups and the "cat"'/"dog"/"kid" etc pulled the power cord.

---

