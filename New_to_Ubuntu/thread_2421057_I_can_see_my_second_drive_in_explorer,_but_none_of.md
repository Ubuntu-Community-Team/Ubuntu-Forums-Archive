---
title: "I can see my second drive in explorer, but none of my applications can see it"
date: 2019-06-15
forum: New to Ubuntu
---

### Post by sheltieherder on 2019-06-15
I took my old Lubuntu install on a 2TB drive and moved it to the secondary slot.
Installed a fresh SSD in the old slot and loaded the new Lubuntu on it yesterday. (19.04)
It all works just fine, but one thing.
I can clearly see my 2TB drive in Explorer and I can access the data from explorer...but when I go to any application...as in VLC for an example, there is no way to access my big drive.
Tried putting in a perma-link, but I am wondering if it has anything to do with the drive being previously bootable???
(It still will boot right into my old setup if I swap boot drives)

fstab must be right if I can see it, no?

"lsblk" returns:
> :~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9492;&#9472;sda1   8:1    0 111.8G  0 part /
sdb      8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.7T  0 part /media/jerry/e9806c8d-bcd3-4f9d-ba47-e64a1d1

---

### Post by TheFu on 2019-06-15
No, being bootable previously has nothing to do with visibility.
What is this "Explorer" thing you mention? Isn't the file manager in Lubuntu Thunar?

Appreciate the attempt to make the lsblk output readable but failed. Using "code tags" is how that is handled.  Adv Editor, use the "#" button.  Things should line up here just like they do in a terminal.

Things mounted under /media are usually NOT mounted via fstab. Instead, the slower gvfs is being used (assuming non-Linux file systems are involved).
When you type **mount** without any options, that shows all the real mounts.  gvfs storage doesn't show up in that output.  The Linux File System Hierarchy Standards explain: [https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf](https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf)> 
3.11. /media : Mount point for removable media
3.11.1. Purpose
This directory contains subdirectories which are used as mount points for removable media such as floppy
disks, cdroms and zip disks.

**df -Th** would be helpful too. We don't need to see any lines with 'loop' devices.

As for the issue with VLC, I suspect the installed version of vlc is using a snap.  By default, that version cannot access storage outside the HOME directory.  This is a security thing.  If you choose to keep using snaps, then learning the commands will be helpful: [https://itsfoss.com/use-snap-packages-ubuntu-16-04/](https://itsfoss.com/use-snap-packages-ubuntu-16-04/)  You can choose to remove all snaps from your system, if you like.  There are trade-offs, but you can remove the vlc snap package and install the normal Ubuntu vlc package which should work as you expect.  There is a way to tell snap to allow vlc access to other storage. I know it is possible, but don't know how to do it. Sorry. A quick google should find the steps.  [https://tutorials.ubuntu.com/tutorial/advanced-snap-usage#0](https://tutorials.ubuntu.com/tutorial/advanced-snap-usage#0) has a tutorial 51minutes!!!  Which they'd just provide a single page with the info.

---

### Post by Morbius1 on 2019-06-16
I haven't used Lubuntu in years so I installed it -- things have changed a bit over the years.

I purposely did not mount the second partition in fstab but mounted it through the file manager ( which uses udisks2 NOT gvfs - and the mount command will confirm that it's using udisks2 ). Seems to work here. VLC is installed by default and it doesn't seem to be a snap. If you installed a later version as a snap that could be the issue as described above.

Are you running as jerry? Because he is the only one that will be able to access the partition if it's mounted at /media/jerry/e9806c8d-bcd3-4f9d-ba47-e64a1d1 due to the access control list on /media/jerry.

If that is the problem you might want to set the mount point in fstab one level up from where you have it: /media/e9806c8d-bcd3-4f9d-ba47-e64a1d1 rather than /media/jerry/e9806c8d-bcd3-4f9d-ba47-e64a1d1.

Back in the day you were always told not to mount things directly under /media because that is where the system mounts things ( udisks2 ) but that changed 4 or 5 years ago changing it to /media/your-user-name. Mounting things under /media/your-user-name is not recommended.

---

### Post by sheltieherder on 2019-06-16
Yes, I mean the file manager.

I would very much prefer not to dump snap if possible.
Really, if I spoke in windows-ese, I want to "map a drive" at a certain folder, instead of across the network.
Ive tried making symlink...fstab lines...

I can SEE the drive.
Here is the fstab;
> 
UUID=4db3dbaf-263a-476e-b3ac-938be566abc9 /              ext4    defaults,discard 0 1
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0
UUID="e9806c8d-bcd3-4f9d-ba47-e64a1d1c6675"  /home/jerry/MOVIEDRIVE ext4  defaults,x-gvfs-show 0 0


The last line is mine. It "works" but the drive is not showing up where I want it to.


I would VERY VERY much like to just create a permanent link in my HOME directory of the new SSD drive, pointing to the DOWNLOADS folder in the big second drive.
(Which is what I tried to do in that last line.)


Thanks for the pointers!

---

### Post by sheltieherder on 2019-06-16
> **Morbius1 said:**
> 
Are you running as jerry? Because he is the only one that will be able to access the partition if it's mounted at /media/jerry/e9806c8d-bcd3-4f9d-ba47-e64a1d1 due to the access control list on /media/jerry. 
Yup. I guess this is another thing I will have to fix.

> **Morbius1 said:**
> 
If that is the problem you might want to set the mount point in fstab one level up from where you have it: /media/e9806c8d-bcd3-4f9d-ba47-e64a1d1 rather than /media/jerry/e9806c8d-bcd3-4f9d-ba47-e64a1d1.
Going to do that right now. Thanks.

***EDIT=well, that cleared up half the issues I was having right there. Thank You much.

Since there are thirty different ways to create symlinks/pointers (whatever folks may call them) what would you suggest?

---

### Post by sheltieherder on 2019-06-16
> lsblk -l
NAME MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda    8:0    0 111.8G  0 disk 
sda1   8:1    0 111.8G  0 part /
sdb    8:16   0   1.8T  0 disk 
sdb1   8:17   0   1.7T  0 part /home/jerry/MOVIEDRIVE
sdc    8:32   0 931.5G  0 disk 
sdc1   8:33   0 931.5G  0 part 


^That is the present rendition when entering "lsblk"

---

### Post by Artim on 2019-06-16
Oh, just for a minor point: **Thunar** is the file manager in [COLOR=#0000ff]**X**[/COLOR]ubuntu.  I think it's PCManFM in [COLOR=#0000ff]**L**[/COLOR]ubuntuntu.

---

### Post by sheltieherder on 2019-06-16
This may sound stupid, but moving all the files to a new folder cured the issue, along with the fstab modification  (putting my line before "tmpfs                                     /tmp           tmpfs   defaults..." instead of how it appears in post #4) seems to have worked.
Thanks much!

---

### Post by Artim on 2019-06-16
How cool is that!  Make sure you mark the thread as SOLVED, so others can benefit from learning an easy way to fix it!

---

### Post by TheFu on 2019-06-17
> **sheltieherder said:**
>  
Since there are thirty different ways to create symlinks/pointers (whatever folks may call them) what would you suggest?

```
$ ln -s {source} {target}
```

That's the only way I know to make a symbolic link.

---

