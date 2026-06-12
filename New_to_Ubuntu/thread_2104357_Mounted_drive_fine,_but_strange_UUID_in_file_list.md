---
title: "Mounted drive fine, but strange UUID in file list"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by starstreams on 2013-01-12
I was following [this]("http://www.binarytides.com/ubuntu-automatically-mount-partition-at-startup/") advice here exactly.
After I got the UUID of the second partition on the second drive using *sudo blkid*, I added it to *fstab* like this..(substituting my UUID here).


```
UUID=MYID UUID...  /media/MYID UUID...   ext4     errors=remount-ro,auto,exec,rw,user 0       0
```The drive mounts fine, but at the top in the title bar my UUID shows rather than the volume lable and I'm also seeing another.. what looks like a drive in the places list with a long name, which happens to be the identical name of the UUID. I'm also not able to create a folder. I get permission denied. Yet I can mount the first NTFS partition on this second SATA drive. I'm not sure where I went wrong. I also tried removing the commas from the permissions section at the far right using just spaces instead. Made no difference. Shouldn't user 0 0 give anyone rw permission?


The lyout of the 2nd SATA drive is:
sdb1 NTFS
sdb2 EXT4 (partition being mounted)

---

### Post by Wim Sturkenboom on 2013-01-13
Maybe the use of /media and the same UUID that is usually used by automounting confuses the system?

For my internal third HD (ext3 formatted, dedicated to photos), I use the following line in fstab and I don't have issues (as far as I know).
```

UUID="6ff7017c-e4d9-49ba-9a1b-b62e45dab820" /mnt/photos ext3 defaults 0 2

```
It's mounted in /mnt (mountpoint photos), not in /media; /media is, in my opinion, a temporary mount for removable media, not for internal HDs.

Note: Using Ubuntu 12.04, not Lubuntu.

PS
obviously you need to replace the uuid and you need to create a suitable mountpoint (preferably with a name that suites you; e.g. MySecondDisk instead of photos)

---

### Post by starstreams on 2013-01-13
> **Wim Sturkenboom said:**
> It's mounted in /mnt (mountpoint  photos), not in /media; /media is, in my opinion, a temporary mount for  removable media, not for internal HDs.
I don't think this is the case here Wim. Because when I mount a drive (Not using the sftab file) the system mounts hard drives at Media by defult.

This is getting more strange by the min.
This has turned into two different issues I think. 

**EDIT-2:**
Looks like I fixed the 
[COLOR=Red]Error Creating directory: Permission denied.[/COLOR]

Did a: 
```
sudo chown user:user /media/DriveVol
```

Just need to restart and see if the setting holds...

---

### Post by Wim Sturkenboom on 2013-01-14
> **starstreams said:**
> I don't think this is the case here Wim. Because when I mount a drive (Not using the sftab file) the system mounts hard drives at Media by defult.
Temporary mount is still true ;) But I overlooked the internal disks that are not mounted by default; my bad :(

It's not clear from your last post if this is solved or not. If it is, please mark as solved using the thread tools just above the first post on the page. If not, leave it and somebody else who uses Lubuntu might be able to advise; looks like a Lubuntu specific issue.

---

### Post by starstreams on 2013-01-14
Hi Wim

**EDIT**

Ok, everything seems to be working now!

I think this was a permissions issue. I just needed to take ownership of the volume as it was set to root only. My fstab file seems to be working also. From what I've learned tonight from experimenting. *mnt* is a temporary mount point ...(in Lubuntu at least). As my fstab file is set to mount at /Media/Data-drive, it works. Note: The [COLOR=Blue]Dada-drive[/COLOR] folder I made as my mount point also shows up in *mnt*, which I think it should as stated "mnt" is where the system temporarily mounts things.
Also, the reason I'm able to view config files even though I've set my account back from *admin* to a *desktop user* is because I'm a member of the* adm* group which can only read but not write without entering sudo first. Everything seems to be working great!  No strange errors anymore.


P.s I'm not sure why that tutorial I was reading said to use two UUIDs in the fstab file, but you're advice to remove the second was good!

Thanks for the help, Much appreceated!

---

