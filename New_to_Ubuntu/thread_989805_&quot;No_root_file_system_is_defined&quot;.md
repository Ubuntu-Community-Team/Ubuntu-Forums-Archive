---
title: "&quot;No root file system is defined&quot;"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-11-22
I've been trying desperately to install Ubuntu on my external HDD that's connected through USB. I'm just starting my ninth day of trying to resolve this problem.

I've been using gparted to re-partition my drive the way I want it, but I can't seem to get it into a state that Ubuntu likes.

What I'm trying to achieve is a set-up whereby:
[LIST][*]the USB HDD acts as a backup storage facility for Windows,
[*]the same partition used as Windows backup is where I'll store any files/documents created under Ubuntu programs that Windows programs can also 'see',
[*]an auto-boot for Ubuntu so that if my USB HDD is connected when I boot up the PC, Ubuntu starts without the need for a menu.lst flash screen.[/LIST]

So, I need to install Ubuntu on the drive, which means having an ext3 partition and a linux-swap partition, as I understand it.

Here's a screenshot of my drive as Ubuntu's Live CD version of Partition Manager sees it:
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/gpartedhdd.png[/IMG]

From what I can deduce from my reading on the subject, the problem appears to be with the 'mount point' of my ext3 partition. It should be '/', shouldn't it? Is there anything else there that looks odd to you folk who know about this stuff?

But my basic problem is, how the heck do I change the mount point? There's no obvious way of doing that in gparted from what I can tell!

Furthermore, the error message I get from Ubuntu when trying to install says:
*"No root file system is defined. Please correct this from the partitioning menu."*

Well, where the flaming hell is the 'partitioning menu'????

---

### Post by adult swim on 2008-11-22
you select the mount point when you are installing ubuntu.  when you install it, dont use the default guided partition, choose manual.  assuming  you want to install ubuntu on the partition /dev/sda1 double click that  entry and it will have  place that says mount point.  enter in / there and it should install.

---

### Post by Roger Allott on 2008-11-22
> **adult swim said:**
> you select the mount point when you are installing ubuntu.  when you install it, dont use the default guided partition, choose manual.  assuming  you want to install ubuntu on the partition /dev/sda1 double click that  entry and it will have  place that says mount point.  enter in / there and it should install.

If I could get the install process to reach that point, it would indeed be pretty simple!

The problem is that I'm prevented from getting to that point for the reasons I tried to explain.

---

### Post by adult swim on 2008-11-22
sorry i cant figure out where you are getting hung up.  you dont set mount points from gparted off of the live cd.  if you are getting the error of no root file system is defined i assume you are getting past the installers partitioner.  are you ever seeing a screen like this [IMG]http://osfreaks.files.wordpress.com/2008/06/ubuntu6.png[/IMG]

---

### Post by Roger Allott on 2008-11-22
> **adult swim said:**
> sorry i cant figure out where you are getting hung up.  you dont set mount points from gparted off of the live cd.  if you are getting the error of no root file system is defined i assume you are getting past the installers partitioner.  are you ever seeing a screen like this [IMG]http://osfreaks.files.wordpress.com/2008/06/ubuntu6.png[/IMG]

No!!! That's the core problem. There's nothing showing on that screen at all. And when I click 'Forward', I'm getting the error message I mentioned.
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/error1.png[/IMG]

---

### Post by prshah on 2008-11-22
> **Roger Allott said:**
> No!!! That's the core problem. There's nothing showing on that screen at all. And when I click 'Forward', I'm getting the error message I mentioned.
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/error1.png[/IMG]

From the first screenshot, notice that there is "key" icon to the left of /dev/sda1. This means that you cannot make changes to this partition. This is probably because it has been "mounted." From Gparted (on the live CD, as before), right-click /dev/sda1 and choose "unmount". Now close gparted and  proceed with the installation, and as suggested earlier, when asked about partitioning, choose "manual".. and so on as earlier suggested.

For good measure, you can also right-click your "swap" partition and choose "swapoff" _before_ exiting gparted. After installation, your swap will be activated automatically.

Just creating /dev/sda1 partition is not enough. It must also be formatted. You can do this either in gparted, or in the manual partitioning dialog.

EDIT: Oopsie; there's no "key" next to /dev/sda1; which means it should allow it to be mounted as "/". Can you post a screenshot of the manual partition window as you see it?

---

### Post by Roger Allott on 2008-11-22
> **prshah said:**
> From the first screenshot, notice that there is "key" icon to the left of /dev/sda1. This means that you cannot make changes to this partition. This is probably because it has been "mounted." From Gparted (on the live CD, as before), right-click /dev/sda1 and choose "unmount". Now close gparted and  proceed with the installation, and as suggested earlier, when asked about partitioning, choose "manual".. and so on as earlier suggested.

For good measure, you can also right-click your "swap" partition and choose "swapoff" _before_ exiting gparted. After installation, your swap will be activated automatically.

Just creating /dev/sda1 partition is not enough. It must also be formatted. You can do this either in gparted, or in the manual partitioning dialog.

EDIT: Oopsie; there's no "key" next to /dev/sda1; which means it should allow it to be mounted as "/". Can you post a screenshot of the manual partition window as you see it?

The 'Prepare partitions' window is completely blank.
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-Install.png[/IMG]

Because I cannot move beyond that screen (because I'm getting the "No root file system is defined" error), I cannot get to the manual partition window in the installation process.

---

### Post by adult swim on 2008-11-22
this seems to be a bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675)
there is a workaround for it but unfortunately it requires an alternate install cd [http://ubuntuforums.org/showthread.php?p=6081365](http://ubuntuforums.org/showthread.php?p=6081365)

---

### Post by prshah on 2008-11-22
> **Roger Allott said:**
> The 'Prepare partitions' window is completely blank.
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-Install.png[/IMG]

Which is highly strange!

Do you have anything useful on the disk or can you delete all partitions and try? 

If you _can't_ delete all partitions, just delete the swap and ext3 created partitions; then try again, don't make the partitions in gparted.

Can you also post the output of ```
sudo fdisk -l
```

---

### Post by Roger Allott on 2008-11-22
> **adult swim said:**
> this seems to be a bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675)
there is a workaround for it but unfortunately it requires an alternate install cd [http://ubuntuforums.org/showthread.php?p=6081365](http://ubuntuforums.org/showthread.php?p=6081365)

Thanks for that. It's good to at least know that it's a bug and not me being crazy! But ......

[LIST=1][*]From where does one get the alternate iso file?

[*]Could you expand on what is meant by: *"when partition, run shell, you can see /hd-media, only need run as following:"*. What is that in full grammar English language sentence construction?[/LIST]

---

### Post by Roger Allott on 2008-11-22
> **prshah said:**
> Which is highly strange!

Do you have anything useful on the disk or can you delete all partitions and try? 
There is nothing whatsoever useful on the disk. I'm very happy to get rid of everything by 'Create New Partition Table' and remake the partitions, but I need a step-by-step guide to what to do next as regards making whatever is necessary.

> **prshah said:**
> If you _can't_ delete all partitions, just delete the swap and ext3 created partitions; then try again, don't make the partitions in gparted.
OK, but I thought gparted was the best tool around for making disk partitions????

> **prshah said:**
> Can you also post the output of ```
sudo fdisk -l
```
I'll come back to that later as it requires a reboot, but I've done it before and everything seemed to look normal.

---

### Post by adult swim on 2008-11-22
the alternate iso can be found here [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)
im not sure about the options available with the alternate iso because ive never used it. surely someone here has had experience with the alternate cd and could fill you in.
EDIT: if you dont care to delete everything on the drive then before you try the alternate iso i would try to use the "guided use entire disk" option and see where that gets you.  if it works you could set up your partition scheme easily with a gparted live cd after ubuntu is installed.

---

### Post by Roger Allott on 2008-11-22
> **adult swim said:**
> the alternate iso can be found here [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)
im not sure about the options available with the alternate iso because ive never used it. surely someone here has had experience with the alternate cd and could fill you in.
Thanks, but isn't the alternate iso a text based installer? In which case, as someone who is extremely uncomfortable with the aspect of Linux that demands command line code, I'll wait for a reliable GUI version of the installer to be made available before I fugg up my hard disk through lack of knowledge!

> **adult swim said:**
> EDIT: if you dont care to delete everything on the drive then before you try the alternate iso i would try to use the "guided use entire disk" option and see where that gets you.  if it works you could set up your partition scheme easily with a gparted live cd after ubuntu is installed.
The problem with that is that I cannot get to the screen that gives me that option as it comes after the one that's causing me the error message.

---

### Post by adult swim on 2008-11-22
does the error pop up immediately after this?
[img]http://i.zdnet.com/gallery/171007-480-360.jpg[/img]

---

### Post by Roger Allott on 2008-11-22
> **adult swim said:**
> does the error pop up immediately after this?
[img]http://i.zdnet.com/gallery/171007-480-360.jpg[/img]

No. The screen immediately after that is:
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-Install.png[/IMG]

It's when clicking forward on that screen that the error message pops up.

---

### Post by prshah on 2008-11-22
> **Roger Allott said:**
> There is nothing whatsoever useful on the disk. I'm very happy to get rid of everything by 'Create New Partition Table' and remake the partitions, but I need a step-by-step guide to what to do next as regards making whatever is necessary.


Here's a quick and instantaneous way to wipe out the partition table:

[indent]
a) Boot into live CD
b) Open gparted, unmount all mounted sda partitions; (Right click the partition entry, choose "Unmount" if available)
c) Turn off swap (In gparted, choose "Swap off" from the context menu for the swap partition)
d) Exit gparted
e) THE NEXT STEP WILL COMPLETELY AND INSTANTANEOUSLY WIPE OUT PARTITIONS ON THE TARGET DISK. Make DOUBLY sure that the disk you want to wipe out is in fact /dev/sda.
f)```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```
g) Confirm partition table is wiped out ```
sudo fdisk -l /dev/sda
```
h) Notify the kernel of changes ```
sudo partprobe /dev/sda
```
i) Proceed with installation again.
[/indent]
Just a thought: Have you turned off "Virus Protection" in the BIOS? That shouldn't cause the problem that you are facing, but you will have to do so anyway if you want to use the above command. If you've previously made changes to the partition structure, then it's probably turned off and you need not check this.

CAVEAT: The above code(s) will instantly remove the partition table entries, rendering all files and directories on the ENTIRE DISK targeted inaccessible without special means, and possibly not even with special means. Use with caution, and at your own risk.

---

### Post by Roger Allott on 2008-11-23
Many thanks to everyone who has offered an opinion on this issue.

As it turned out, I had a left-brain brainwave yesterday on how to resolve it. I installed openSUSE on the external HDD!

It installed fine, with the KDE desktop environment, and I must say that it's rather nice.

The installer for openSUSE seems to my inexpert eyes to be a superior application that the one used for Ubuntu, so it resolved whatever problem I was having with root partitions as part of the process.

Once openSUSE was on though, I thought I'd try to go to the next level and see if I could add Ubuntu to it to make the external drive dual boot (openSUSE-KDE and Ubuntu-Gnome).

Oh dear. The installation seemed to go OK, but then when I tried to boot it gave me the rather final error message of "No Operating System Found"!

So I started over again, rearranging and reformatting the partitions and reinstalled openSUSE as before. Oddly, I had to do that twice because on the first run the bootloader didn't install.

Anyway, once I got to that stage I didn't want to fugg things up again with installing Ubuntu on the external HDD, so I put my main internal HDD back in the machine and booted Windows Vista (i.e. without the external HDD connected).

From Vista, I have just now done a wubi install of Ubuntu to my internal HDD, and that looks to have gone fine from what I can tell so far.

So, whilst I haven't ended up with the system I wanted at outset, what I've got is really rather nice. If my external HDD is connected at boot, I get the option of:
[LIST][*]openSUSE
[*]openSUSE (Xen) (whatever the fugg that is!)
[*]Windows (but this fails to find Vista as it thinks Windows is installed on the external HDD)
[*]openSUSE (failsafe)[/LIST]

If my external HDD is **not** connected, I get the bootloader that's somewhere on my internal HDD that gives me the option of:
[LIST][*]Windows Vista
[*]Ubuntu[/LIST]

Right, my tasks now are to find out how to install/update some software on openSUSE and Ubuntu and, most importantly, try to get my Vodafone Mobile Broadband to connect from them.

---

