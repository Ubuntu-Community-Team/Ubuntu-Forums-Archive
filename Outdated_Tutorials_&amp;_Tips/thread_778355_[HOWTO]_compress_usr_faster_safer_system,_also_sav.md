---
title: "[HOWTO] compress /usr: faster safer system, also saves battery life"
date: 2008-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by synss on 2008-05-02
This is not intended for the beginner, it is not difficult to do but **will** result in a **broken install** if done wrong.

The stock ubuntu kernel contains both [squashfs]("http://squashfs.sourceforge.net/") and [aufs]("http://aufs.sourceforge.net/"), the former is support for a compressed (7z-style compression) read-only file system. The latter is a "union filesystem", it allows to stack directories and we will use it to keep our /usr read-write.

The idea comes from [me on the gentoo forums]("http://forums.gentoo.org/viewtopic-t-465367.html"), and [other related]("http://forums.gentoo.org/viewtopic-t-646289.html") forum discussion.

Here is what we will do:
compress /usr with squashfs and mount a read-write union on top of it to keep it writable.
It is safer because you keep a read-only backup of /usr
It is faster because searching through the squashfs image is faster than through the actual file system, see [benchmarks]("http://forums.gentoo.org/viewtopic-t-646289.html")
It saves battery life because it reduces physical head movements of the hard drive.

Now, if you do not feel comfortable with the command line and do not know what a file system is, this tip is not for you. /usr is crucial to your linux and messing with it is risky. It is risky if you do not know what you are doing. And I do not take responsibility if **you** break **your** ubuntu. OK?

Let's go.

Everything is done at the terminal.

Install squashfs-tools and aufs-tools (aufs-tools is not required, though)
```
sudo aptitude install squashfs-tools aufs-tools
```

Compress /usr, as root to avoid permission issue
```
cd ~
sudo mksquashfs /usr /.usr.sqfs -check_data
```
or
```
sudo mksquashfs /usr /.usr.sqfs -check_data -info -no-progress
```
Everything OK?

reboot, when grub starts (a few white lines telling you you can press ESC) press ESC. At the grub prompt, the entry on top should be selected, press e (edit) at the kernel line. Replace "quiet splash" with "S" at the end of the line. Press ENTER and b (boot).
After the kernel has been loaded, it will ask you if you want to "drop to a root shell" and yes, you want, select this option.

The system will finish booting and actually drop you to the root shell.

Move /usr out of the way
```
cd /
mv /usr /usr-old
mkdir /usr
mkdir -p /var/squashed/{ro,rw}
```

and edit /etc/fstab
```
nano -w /etc/fstab
```
add the following lines
```
/.usr.sqfs  /var/squashed/ro  squashfs  loop,ro  0 0
aufs  /usr  aufs  br:/var/squashed/rw=rw:/var/squashed/ro=ro  0 0
```
then you try it
```
mount -a
```
any error? you have made a mistake in /etc/fstab
```
mount | grep /usr
```
and have a look whether the filesystems are mounted correctly (two lines, one for the squashfs filesystem and one for the aufs union.)
```
touch /usr/test
```
if that works too, you should be all set. Reboot. If it does not go till the end, you may want to try to reboot and remove the quiet splash from the grub entry to see what fails.

Once back in gnome or KDE or... if all is working right, you can also remove /usr-old, you should probably make sure everything is mounted correctly again.

You can reconstitute the squashed image from time to time if you install a lot of things and /var/usr becomes big. You need to make it again also when you upgrade to the next version of Ubuntu.

If you are using LVM2, like me, you can even put the squashfs image in its own volume, there is nothing wrong with that. And having root on LVM2 is not a problem for this "how to" either, provided you keep /boot out of LVM.

---

### Post by takmsdsm on 2008-05-02
> reboot, when grub starts (a few white lines telling you you can press ESC) press ESC. At the grub prompt, the entry on top should be selected, press e (edit) at the kernel line. Replace "quiet splash" with "S" at the end of the line. Press ENTER and b (boot).
After the kernel has been loaded, it will ask you if you want to "drop to a root shell" and yes, you want, select this option.

The system will finish booting and actually drop you to the root shell.

Adding replacing quiet splash with S causes my system to restart when i press B to boot, and it defaults back to the quiet splash variables when that happens. 

This is with 8.04

---

### Post by synss on 2008-05-06
> **takmsdsm said:**
> Adding replacing quiet splash with S causes my system to restart when i press B to boot, and it defaults back to the quiet splash variables when that happens. 

This is with 8.04


An alternative way to accomplish that is to edit the line directly in the menu.lst file: mount /boot if it is on another partition ; then edit the file /boot/grub/menu.lst in the same manner (replace quiet splash with S) and reboot, after you are done moving /usr, reboot and revert your changes in menu.lst.

But going into single user mode from grub *should* work...

Also please note that I have changed the mount points in the how to to /var/squashed/rw and /var/squashed/to and that is much better! Please do this change too.

---

### Post by Jayferd on 2009-10-31
I'm running into some weird errors on Karmic UNR.  It seems like aufs now needs /usr to be mounted before it will work.  When I boot, my /.usr.sqfs gets mounted to /var/squashed/ro, but aufs does absolutely nothing.  Same with mount -a.  BUT when I first mount the thing to /usr with
```

mount -o loop /.usr.sqfs /usr

```
and THEN run mount -a, the contents of the rw folder appear in /usr.

So I tried changing the lines in my fstab to this:
```

/.usr.sqfs /usr squashfs loop,ro 0 0
aufs /usr aufs br:/var/squashed/rw=rw:/usr=ro 0 0

```
The idea is that by the time aufs has to do anything, the squashfs stuff is already mounted.

Now mount -a does the trick immediately, but somehow the mount doesn't happen at boot.  init borks itself and drops me to a maintenance terminal, where I discover that not only is /usr empty, but also /var/squashed/ro.  Even weirder is that as soon as I type mount -a, everything is mounted and happy.  Is this specific to Karmic, I wonder, or has there been some change to aufs?

EDIT: I wonder if this has anything to do with [this bug]("https://bugs.launchpad.net/ubuntu/+source/aufs/+bug/431954")?

EDIT EDIT:  Even stranger, when I run mountall -v it shows "mount /usr [1011] exited normally" even though the thing is empty.

---

### Post by Jayferd on 2009-10-31
Okay, now every time I boot it empties my fstab.  Help please?

---

### Post by Jayferd on 2009-11-03
Wow, guys, the silence is deafening. :(

I've reinstalled on my eeepc, and I'm experimenting on a VM on my desktop.  I've done this 3 times from a fresh install now, and basically have gotten nowhere new.

Basically, aufs refuses to combine the branches unless /usr is already there.  Which files does it need?  I've copied over com, paste, tee, and diff, plus the entire src directory.

---

### Post by Labello on 2009-11-04
Hi,

very nice guide! thanks for that! but there are two issues i would like to have resolved:
1. when i boot with the kernel-option "S" instead of "quiet splash" and select the entry "root" I am supposed to enter the root-password but as far as i know ubuntu disables the root-user which disables me to enter any password. the password of the administrator also doesn't work. I just did a normal boot, stopped all running services and used TTY1.

2. how do i update the squashed filesystem? do i have got to redo all steps or is the command that creates the filesystem enough? i mean this one:
```
sudo mksquashfs /usr /.usr.sqfs -check_data
```

but anyway: very nice and as is can confirm effective guide!

---

### Post by Penguin Guy on 2009-11-04
> **synss said:**
> 
Compress /usr, as root to avoid permission issue
```
cd ~
sudo mksquashfs /usr /.usr.sqfs -check_data
```
or
```
sudo mksquashfs /usr /.usr.sqfs -check_data -info -no-progress
```

Why the [COLOR="Green"]cd ~[/COLOR], also when you say do this or do this - it would be nice to know the difference.

Perhaps you should get the reader to backup /usr at the start:
> 
It's a good idea to backup our data unless we mess up:
```

cp /usr /usr~

```

.....


If everything went okay we can delete our backup:
```

rm /usr~

```
If something went wrong we can restore /usr:
```

mv /usr~ /usr

```


Other than that, great tutorial!

---

### Post by Jayferd on 2009-11-05
Hey guys, I'm glad this is working for you.

I've tried this about 6 times in a row in VBox, saving different files from /usr, and it consistently breaks.  I think it's repeatable:

1.  Install a fresh copy of UNR 9.10.
2.  Follow the guide.
3.  Reboot, it breaks.
4.  Or, instead of typing "mount -a", use "mountall", then check out the contents of /usr.  It will be empty.

Since this is repeatable on different hardware, I'm finding it hard to believe that I'm the only one experiencing this.  Is the guide broken, or is there a secret step that I'm not supposed to know about?

At this point, I'm sort of frustrated, because even if you guys can't/won't help me, I'd at least have liked some acknowledgement that I exist; even just to tell me to go away.

Peace,
--Jay

P.S.  I'm also not following the guide blindly; I do know my way around the command line, and I've been searching the web and the forum links provided here for answers.  I simply haven't found a good explanation of why "mount -a" works and "mountall" does not.

---

### Post by dude2425 on 2009-11-06
I believe the order in which things get mounted is no longer as logical as it was in the past. This guide was written in May 08, and since then we've got mountall and changes to the boot process to make it faster. I've experienced the same problem when adapting a guide for Gentoo to do the same. I think it's just the way mountall parses /etc/fstab or something.

I ultimately decided not to pursue this idea any more due to the fact that I live on the edge and am always updating software. If I kept the stuff required to get squashfs and aufs mounted in /usr, it would never get updated after the squashed image mounts over it. I would have to run an update, resquash everything, and either drop to recovery and run update over, or copy everything from the squashed image that I need back into /usr.

Currently, this is too much of a hassle for me. This is more suited for a system that never needs to receive updates, like gramma's laptop.

---

### Post by tgalati4 on 2009-11-06
Grandma wouldn't know speed if it hit her in the head.  Perhaps this is better suited for some embedded applications with a slimmed-down /usr.  I run firefox using a ramdisk and it's reasonably speedy.  Where are the benchmarks for speed increases and battery savings?

---

### Post by GoatZilla on 2010-01-22
I'm going to ask the obvious question.

How do ANY of the init scripts, etc., manage to run considering they use executables out of /usr before they manage to get mounted?

Hell, mount.aufs itself is a shell script.

---

### Post by Jayferd on 2010-01-22
@GoatZilla, I think the idea was that it should be able to mount the squashed /usr first, so that by the time it tries to use mount.aufs, it's already got all the scripts it needs in /usr.

The problem I was running into, I think, is that Karmic really wanted to run mount.aufs *before* mounting squashfs, despite the order they appeared in my fstab.

Again, these are just my vague theories, but after spending 2 weeks banging my head on the wall over this, I've given up trying to get this to work with Karmic.

---

### Post by Turpin on 2010-02-13
I'm regretting "upgrading" to Karmic.  Has anyone figured out a workable solution for having a compressed /usr folder?  I used to use the old unionfs and squash solution which worked great up to Jaunty.  Now nothing works with Karmic.  If someone thinks I'm missing something, please help.  I'm fairly advanced, but when it comes to boot sequence and the like, it's a scary area for me.  I'm wasting a lot of time trying to save a little space because I have to on my EEE pc701.
If anyone, anyone, posts a procedure for this, you will generally be regarded as a hero, I assure you, because noone has posted anything anywhere for this that works for Karmic.  At least, not that I've found and I've searched for hours.

---

### Post by halfvulcan on 2010-02-14
Ok, I got it working.  Under Karmic, I used the instructions at this link [http://forums.gentoo.org/viewtopic-t-646289.html](http://forums.gentoo.org/viewtopic-t-646289.html)
except I recommend NOT installing aufs-tools (or backup your partition or something first) because it breaks the system, which makes no sense to me, but it is so, in my experience.  Anyway, I kind of skimmed the first few steps, installed squashfs-tools, created /squashed/usr/ro and /squashed/usr/rw, compressed the /usr folder with 
mksquashfs /usr /squashed/usr/usr.sfs -b 65536
, added the following 2 lines to /etc/fstab:
/squashed/usr/usr.sfs   /squashed/usr/ro   squashfs   loop,ro   0 0
usr    /usr    aufs    udba=reval,br:/squashed/usr/rw:/squashed/usr/ro  0 0
rebooted to a Puppy liveusb, but you can use most any live cd or usb.  Mounted the hard drive, renamed /usr to usr-old and created an empty folder renamed to /usr.  Then rebooted, saw that it worked, deleted the /usr.old folder.  I don't know why it only works as long as aufs-tools AREN'T installed.  It should be the opposite you would think, but it took a happy mistake for me to realize this is the case.  If you have aufs-tools installed in Karmic, up-to-date on updates on today, Feb 14, 2010, and if you follow the instructions to compress the /usr folder, it will break the system.  If you don't have aufs-tools installed, it works.

---

### Post by edmondt on 2010-02-16
> **halfvulcan said:**
> Ok, I got it working.  Under Karmic, I used the instructions at this link [http://forums.gentoo.org/viewtopic-t-646289.html](http://forums.gentoo.org/viewtopic-t-646289.html)
except I recommend NOT installing aufs-tools (or backup your partition or something first) because it breaks the system, which makes no sense to me, but it is so, in my experience.  Anyway, I kind of skimmed the first few steps, installed squashfs-tools, created /squashed/usr/ro and /squashed/usr/rw, compressed the /usr folder with 
mksquashfs /usr /squashed/usr/usr.sfs -b 65536
, added the following 2 lines to /etc/fstab:
/squashed/usr/usr.sfs   /squashed/usr/ro   squashfs   loop,ro   0 0
usr    /usr    aufs    udba=reval,br:/squashed/usr/rw:/squashed/usr/ro  0 0
rebooted to a Puppy liveusb, but you can use most any live cd or usb.  Mounted the hard drive, renamed /usr to usr-old and created an empty folder renamed to /usr.  Then rebooted, saw that it worked, deleted the /usr.old folder.  I don't know why it only works as long as aufs-tools AREN'T installed.  It should be the opposite you would think, but it took a happy mistake for me to realize this is the case.  If you have aufs-tools installed in Karmic, up-to-date on updates on today, Feb 14, 2010, and if you follow the instructions to compress the /usr folder, it will break the system.  If you don't have aufs-tools installed, it works.

I did that, and it booted fine... but now NetworkManager cannot connect to any WIFI or Ethernet.

Does anyone have the same problem?

---

### Post by edmondt on 2010-02-22
> **edmondt said:**
> I did that, and it booted fine... but now NetworkManager cannot connect to any WIFI or Ethernet.

Does anyone have the same problem?

Do you guys think it is a permission issue? Do we have to change the owner from root to something else?

Please advice...

---

### Post by Turpin on 2010-07-26
> **edmondt said:**
> Do you guys think it is a permission issue? Do we have to change the owner from root to something else?

Please advice...

Yep, I just experienced this.  And I think I know what it is.  I removed apparmor.  The network is fine now.  So, if you're one who's fond of Apparmor, and I'm not, then you would have to track down what's being blocked by Apparmor and let it do what it needs to do.

---

### Post by nnn4 on 2010-08-06
I got it perfectly working on my eeepc running ubuntu 10.04 netbook  edition, fitting a 1.9Go /usr in 540 Mo. I did every manipulations from  an xterm in a normal session. It works well because /usr is almost never  written to (only while installing or updating packages).

Here is a few tips :

AppArmor does its job and denies  NetworkManager's access to files from the aufs mount. It probably breaks  other programs like dhclient, evince, etc. To fix it you have to  declare the aufs branches by adding the following lines to the file 
*/etc/apparmor.d/tunables/alias* (replace the ro and rw paths by yours) :
```
alias /usr/ -> /var/squashed/ro/,
alias /usr/ -> /var/squashed/rw/,
```Then reload AppArmor profiles (this may take a minute):
```
sudo invoke-rc.d apparmor reload
```Do not forget to run mksquashfs as root, or it will break permissions on  suid files like sudo. Of course before creating the squashfs image,  apply every  tweaks you want, like installing/removing packages (make synaptic  display and sort by packages sizes if you want to free more space).
Then do a backup on a external drive of your usr.sfs alone, because it stores  the file permissions and ownerships and of course it is copied much faster than the uncompressed directory. You will be able to  restore your system by mounting it and copy the mount content back to disk.

To test the system with as little modifications as possible, don't move  the initial usr until you are sure everything works fine. So, modify  /etc/fstab, try sudo mount -a, reboot, test a few things. If no problem  occurs, you can backup/delete /usr. To do so, bind the real  filesystem to access it while running on aufs :
```
sudo mkdir /mnt/root
sudo mount --bind / /mnt/root
```You can't move/delete the usr directory, so delete its content instead :
```
sudo rm -r /mnt/root/usr/*
```To avoid grub complains about a missing file, restore its data to the physical */usr*  :
```

sudo cp -r --parents /usr/share/grub /mnt/root

```With the grub and AppArmor fixes the system should run transparently.  I'm confused with the aufs-tools problem, does it still exist in Lucid ?

---

### Post by nigelhealy on 2010-11-18
Also confirm this is working on my Ubuntu 10.04, on a 32bit minimal netbook it saved me 1GB, on a 64bit more-software laptop it saved me 1.9
GB.;) Taking all the last few posting into one single unified consistent HOWTO:

so installed squash-tools
```
sudo apt-get install squashfs-tools
```
make the mount points, this method does it in one command
```
sudo mkdir -p /squashed/usr/{ro,rw}
```
Backup fstab so we can swap back easily later if required
```

sudo cp /etc/fstab /etc/fstab.presquash
```
edit fstab to add mount points
```
/squashed/usr/usr.sfs /squashed/usr/ro squashfs loop,ro 0 0
usr /usr aufs udba=reval,br:/squashed/usr/rw:/squashed/usr/ro 0 0

```
And backup this edited file
```

sudo cp /etc/fstab /etc/fstab.postsquash
```
make the squashed copy of /usr
Note - I played with differen blocksizes, the figure below the biggest that is supported and I found it made for the greatest disk space saving and the best performance.
```
sudo mksquashfs /usr /squashed/usr/usr.sfs -b 1048576
```
tell appmoor about the new directories
```
sudo gedit /etc/apparmor.d/tunables/alias 
```
appending these lines
```
alias /usr/ -> /squashed/usr/ro/,
alias /usr/ -> /squashed/usr/rw/,
```
and then this command
```
sudo invoke-rc.d apparmor reload

```
then immediate use the squashed /usr however if /usr has an issue commands like vi, gedit, sudo, etc won't work so in case you have to change anything prepare by entering a simple shell
```

sudo -i
mount -a
```
Check things out. If the system complains, then to revert back, don't do anything else, don't exit the "sudo -i" shell but revert back.
```

cp /etc/fstab.presquash /etc/fstab
```
Reboot a few times, once happy then delete the old unsquashed /usr
```
sudo mkdir /mnt/root
sudo mount --bind / /mnt/root
sudo rm -rf /mnt/root/usr/*
sudo cp -r --parents /usr/share/grub /mnt/root
sudo umount /mnt/root
sudo rmdir /mnt/root

```
.... and see free space increase!:P


Timings before/after, its mixed conclusion!
```

                       Before       After 64K      After 1M
From Grub to Login     22s          28s            28s
Login                  10s          14s            11s
OpenOffice Word        11s          7s             7s

```


So some things are slower and others faster:rolleyes:

---

### Post by Turpin on 2010-12-29
On my Asus EEE, before I did this procedure I had only 1.1 GB free after installing everything I use.  After squashing /usr, 2.5 GB free.  As was pointed out, there may be limited performance benefits too, but for most people the tiny performance boost isn't worth it.
.
   If you ever want to revert back to an uncompressed usr folder, you'd just copy the /usr folder to a removable drive or a local folder using something like gksudo grsync, preserving all permissions and file stamps, then boot into something like Puppy linux and move the copied /usr folder into place as /dev/sda1(or whatever it lists your hard drive as)/usr.  Also don't forget to remove the fstab entry that tells it to mount the squashed usr.sfs.
.
At this moment I'm trying to remastersys my system whose usr folder is squashed. So far so good.  I remastersys backed my system up. Booted the livecd. Now installing it to a spare hard drive.  It is hanging a while on "Performing post-install steps now...Please wait."  I'll update this once I see something happen.
.
Update: I was dealing with hardware issues on the first try, but on the third or fourth try after I resolved those and other issues, I was able to make a remastersys livedvd that properly installed a clone of my install.  BUT, to keep from running over the space limit of a dvd, I found it's important to exclude the folder containing the sfs file.  Remastersys doesn't understand that /usr is mounted from a squashed filesystem, so it copies it over as-is, and proceeds to compress it for the dvd, which works out great. So, just exclude the squashed folder in the remastersys options because it's redundant.  After you've used the livedvd to install your system clone to another system, THEN you can do this procedure again on that computer if you'd like. But I don't see why unless that system is limited on space.

---

### Post by kandresen on 2011-04-03
I am using the instructions under this post #20, but including the alias changes for apparmor. That application is still complaining: 

[  120.111316] type=1400 audit(1301868218.495:35): apparmor="DENIED" operation="file_mmap" parent=2923 profile="/sbin/dhclient3" name="/squashed/usr/ro/lib/NetworkManager/nm-dhcp-client.action" pid=2924 comm="nm-dhcp-client." requested_mask="w" denied_mask="w" fsuid=0 ouid=0

I am of course noticing that it is using "/squashed/usr/ro" rather than "/usr". How can I resolve this issue without disabling apparmor?

The same issue is true for CUPS however I assume fixing it for one will fix it for the other? I am also noticed that my CPU temperature sensors stop working. Notice that I did keep my old usr folder as /oldusr. When doing an mount -o bind /oldusr /usr everything start working again. What can I be missing?

I am using Ubuntu 10.04. I checked that the alias path is indeed correct.

---

