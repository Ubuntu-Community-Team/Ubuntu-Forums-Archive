---
title: "a quick simple question"
date: 2007-08-23
forum: Other OS Talk
---

### Post by Aesir09 on 2007-08-23
say i have ubuntu already so i have grub

what if i want to install a different distro such as arch, SUSE, etc. if i do install it 
how would my comp boot???

:lolflag:

---

### Post by aysiu on 2007-08-24
I would install the new distro's Grub to the MBR (overwriting Ubuntu's Grub). The new Grub should detect all the existing OSes (including Ubuntu) and add them to the boot menu. If not, you can manually add them later.

---

### Post by Aesir09 on 2007-08-24
k thanks

---

### Post by kellemes on 2007-08-25
Most dists use Grub, and as aysiu said.. simply let the new distro install Grub. In a lot of cases Windows will be recognized (sometimes commented out so you have to edit menu.lst or grub.conf) but other distro's often will not be recognized (add by hand).

---

### Post by ArtF10 on 2007-08-25
> **Aesir09 said:**
> say i have ubuntu already so i have grub

what if i want to install a different distro such as arch, SUSE, etc. if i do install it 
how would my comp boot???

:lolflag:

How have you partitioned the hard drive?

---

### Post by init1 on 2007-08-26
it would boot with grub, unless the distro replaced it. Either way, you can make grub or lilo boot anything.

---

### Post by Tux Aubrey on 2007-08-26
Unless someone here knows a work-around, you will also need to remember to update the active version of menu.lst everytime one of the "non dominant" distros gets a kernel update or version upgrade.

---

### Post by ArtF10 on 2007-08-26
OP, do post if you manage to get dual boot working as I tried win XUbuntu and Ubuntu and absolutely butchered it.  Gave up after around 8 days of trying.  So if you solve it, it would really help out if you could post.

---

### Post by kellemes on 2007-08-27
> **ArtF10 said:**
> OP, do post if you manage to get dual boot working as I tried win XUbuntu and Ubuntu and absolutely butchered it.  Gave up after around 8 days of trying.  So if you solve it, it would really help out if you could post.

What happened then? It is quit easy to get a tuxtux-dualboot.

---

### Post by ArtF10 on 2007-08-27
I created an extended partition over the entire HD, then created /home, swap and / for Ubuntu in that order, then created /home and / for XUbuntu.  All I specified at the time of install was the /home and / partitions for both distros and for some reason on restart Ubuntu(which I installed first) said that my /home folder was missing?  The 2 distros showed up on restart, as they were supposed to, in the GRUB menu but I couldn't do anything with this /home error.

I don't know if the OP was planning on doing the same but even if he isn't, it would still help if he gets it working.

EDIT:  I had originally managed to get it working with both distros installed on Primary partitions of the same HD and 2 swap partitions.  I was new and this probably happened by pure luck.

---

### Post by Laplace's Daemon on 2007-08-27
> **Tux Aubrey said:**
> Unless someone here knows a work-around, you will also need to remember to update the active version of menu.lst everytime one of the "non dominant" distros gets a kernel update or version upgrade.
I started a thread asking this question about a month ago, and got [this](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile) website as a responce.  I only have two distributions on here at the moment (Ubuntu and Arch), though I have partitioned room for 2-4 more (which I plan on using at some point).  I use the chainloader method, which means that I have to go through two grub screens to get to my Arch setup, but that doesn't bother me too much.

---

### Post by WishingWell on 2007-08-27
> **ArtF10 said:**
> I created an extended partition over the entire HD, then created /home, swap and / for Ubuntu in that order, then created /home and / for XUbuntu.  All I specified at the time of install was the /home and / partitions for both distros and for some reason on restart Ubuntu(which I installed first) said that my /home folder was missing?  The 2 distros showed up on restart, as they were supposed to, in the GRUB menu but I couldn't do anything with this /home error.

I don't know if the OP was planning on doing the same but even if he isn't, it would still help if he gets it working.

EDIT:  I had originally managed to get it working with both distros installed on Primary partitions of the same HD and 2 swap partitions.  I was new and this probably happened by pure luck.

Well, if you were creating one /home partition in the first distro install (as a logical partition within an extended partition) and then recreated that same partition with the second distro install it would change partition number and so you'd lose all your data on your home partition and you'd need to enter the new partition number in your fstab to get it seeen.

It's not a good thing to share partitions that have user directories on them between different distro installs, if you want to share something, just put it on a different partition and mount it the same way in both distros.

Primary partitions do not swap partition numbers when recreated while logical partitions in an extended partition do, that's why you got it working the first time but not when you used logical partitions.

As someone mentioned earlier, you will either have to edit your /boot/grub/menu.lst in one of your installs and make sure that other installs don't overwrite the boot sector or just install it to the partition and use chainloader for every distro you install after the first one.

If you do mess up just boot off of a live cd, mount whaterver distro that has the /boot/grub/menu.lst to somewhere and point grub-install to that directory.

---

### Post by ArtF10 on 2007-08-28
Ah, that helps a great deal.  Thank you very very much.

One more question..related to this:

If I dual boot Fluxbuntu and Ubuntu, would I be able to install Flux on primary 1, Ubuntu on primary 2 and have 1 swap on a single extended partition?  ALL within the same hard drive?

---

### Post by rsambuca on 2007-08-28
Short answer - yes.  I have five different distros on one hard drive, and they all share a common swap.

---

### Post by ArtF10 on 2007-08-28
Here's what I did:

I did not create any /home partitions rather just hda1 = Xubuntu ext3 /, hda2 Ubuntu ext 3 / and an extended swap partition.  I installed XUbuntu and then installed Ubuntu.  I selected primary ext3 partitions for both so that there was only one SWAP and it was an extended partition.  Right after installing Ubuntu, I rebooted and tried to log into XUbuntu.  

Here's wat I got:
1.  [http://img267.imageshack.us/img267/7945/0000028wu4.jpg](http://img267.imageshack.us/img267/7945/0000028wu4.jpg)
2.  [http://img267.imageshack.us/img267/7959/0000029ox2.jpg](http://img267.imageshack.us/img267/7959/0000029ox2.jpg)
2a.  [http://img248.imageshack.us/img248/1091/0000030cg2.jpg](http://img248.imageshack.us/img248/1091/0000030cg2.jpg)

After 2 or 2a, I pressed Ctrl+Alt+Del and XUbuntu loaded and APPEARS to be working fine.  But what is that error message and how do I eliminate it?

EDIT:  With ONLY Ubuntu installed on the ENTIRE hard drive, fsck ran automatically after 24 bots and the scan went fine.  Nothing was wrong so it can;t be the hard drive which BTW is 8 months old.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a8dc7c26-af7a-4480-a8d1-30afdda0e9d0 /               ext3    defaults,erro$
# /dev/hda2
UUID=50d4e71c-0fd9-4e54-9d29-49235e13be1f /media/hda2     ext3    defaults     $
# /dev/hda5
UUID=8c01a5fa-a7ff-4a05-938c-03c85b2973b9 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by rsambuca on 2007-08-28
I am pretty sure that this error is because your UUID's changed when you formatted and installed ubuntu.  This should be an easy fix.

When in xubuntu, open a terminal and enter```
ls /dev/disk/by-uuid/ -alh
```This will list all of your partitions and drives by UUID.

Then open your fstab file and correct the UUID that has changed.```
gksudo gedit /etc/fstab
```

In your fstab, you will see one of the UUID's doesn't match the ID's from the prior command.  Just cut and paste the correct ID back into the fstab file, save it, and you should be good to go.

---

### Post by ArtF10 on 2007-08-28
ok, I;m a bit lost here:

drwxr-xr-x 2 root root 100 2007-08-28 21:27 .
drwxr-xr-x 5 root root 100 2007-08-28 21:27 ..
lrwxrwxrwx 1 root root  10 2007-08-28 21:27 [COLOR="Red"]8c01a5fa-a7ff-4a05-938c-03c85b2973b9[/COLOR] -> ../../hda5
lrwxrwxrwx 1 root root  10 2007-08-28 21:27 [COLOR="Blue"]a8dc7c26-af7a-4480-a8d1-30afdda0e9d0[/COLOR] -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-08-28 21:27 afa3be73-e851-4336-87c5-b27e50dfe9ea -> ../../hda2

**OLD**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=[COLOR="Blue"]a8dc7c26-af7a-4480-a8d1-30afdda0e9d0 /[/COLOR]               ext3    defaults,erro$
# /dev/hda2
UUID=**50d4e71c-0fd9-4e54-9d29-49235e13be1f /media/hda2**     ext3    defaults     $
# /dev/hda5
UUID=[COLOR="Red"]8c01a5fa-a7ff-4a05-938c-03c85b2973b9[/COLOR] none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

**Here's what my change looks like:**
# /dev/hda2
UUID=**afa3be73-e851-4336-87c5-b27e50dfe9ea /**     ext3    defaults    

where the lines in red and blue remian as is.  Is this correct?  I also changed /media/hda2 to / because I specified / as far as I can remember.  Should this be done or should I leave /media/hda2 ?

Weird that /hda2 is wrong and not hda1...hda1 is the XUbuntu install which gives problems while /hda2 which is the Ubuntu install does NOT and yet is different.

---

### Post by rsambuca on 2007-08-28
If you are in the fstab in your xubuntu partition, then definitely leave the mount point as /media/hda2.  You already have your root directory defined as /dev/hda1.  You don't want two roots!!!

---

### Post by rsambuca on 2007-08-28
Also keep in mind that the old conventions still work.  You can remove the UUID's from your fstab completely and replace them with /dev/hda1, etc.

---

### Post by ArtF10 on 2007-08-28
IT w o r k e d !!!!!!! It's been a long two weeks.  Thanks for all your help.  I really appreciate it.  OH CANADA!!!  I don't quite understand that last comment though.


---X---


Also, one more question if I may:  If I choose to install a 3rd distro..Mint Linux Xfce, will GRUB still work or will I require some more fanciness there?
EDIT:  Google turned up this regarding a Mint Linux installation:
[http://simplyjat.blogspot.com/2007/08/linux-mint-30-xfce-review.html](http://simplyjat.blogspot.com/2007/08/linux-mint-30-xfce-review.html)

So I guess I'll have to do the procedure you described above?  Will it have to be done from XUbuntu again or will I have to do it FROM both Xubuntu and Ubuntu?

---

### Post by rsambuca on 2007-08-29
If you think you are going to be continually testing out new distros, I recommend that you set up your hard drive in advance so you don't have to fiddle around with it every time.  I have attached a pic of how mine is set up just as an example.

As you will see, I have created five logical partitions (sda5-sda9) for different distros, and a small swap (sda10).  I have put these all inside of one large extended partition (sda1).  I also have another partition (sda2) that I use for all of my shared music, data, documents, etc.

Then, whenever I install a new distro, I make sure that I have its grub install to the new partition.  This way, I can chainload from the original grub that is on the mbr.

---

### Post by ArtF10 on 2007-08-29
OK, just to let you know it worked with Linux Mint which is basically Ubuntu.  the installation steps were identical and it automatically added the appropriate GRUB entries without any further tinkering.  Thanks for your assistance....this is what I was looking to accomplish for a while and it finally worked.

Hope this helps some other user trying to do something comparable.

PS:  I didn't like Linux Mint XFCE version so I ended up removing it.

---

