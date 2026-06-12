---
title: "gparted partition manager"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by shahin on 2013-05-01
Greetings-
I just installed a new larger hard drive on my xp machine, and moved the MyDocuments folder to the new drive. But I like to move more files to free up space on the old hard drive. Can i do this with GParted? I really don't want to make the new hard drive primary unless I have to or there is a good reason to do that. My old hard drive is 120 Gig, and the new one is 1/2 Tera Bytes. I would be happy if I could free up another 40 Gig or so.

---

### Post by ibjsb4 on 2013-05-01
You don't move files with gparted, but you could make a data partition for them.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

---

### Post by Mark Phelps on 2013-05-02
It's generally a bad idea to use Linux filesystem utilities on Windows filesystems.  While they often work OK, they do sometimes fail -- and when they do, they leave the Windows filesystem in a corrupted state.

If you need to do partitioning changes on a Windows filesystem, then Google for, download, and create a CD using the Minitool Partition Wizard CD.  It is free and will be able to do all the Windows filesystem partitioning work you need.

---

### Post by Mopar1973Man on 2013-05-02
Like other have mention it best to use Gparted to setup the drive partitions but I would use like Grsync to move data from one partition to another.

---

### Post by stylintile on 2013-05-04
Can't you just cut and paste the files, or copy and paste to the new drive, and then delete them from the older one?  Unless there is a different OS on each drive.  If so I just boot into a live cd and move or copy the files I want, and then reboot to the hard drive.

---

### Post by Mopar1973Man on 2013-05-04
As far as I know I've had no problem copy and pasting between Windows and Linux.

---

### Post by dave2001 on 2013-05-05
You got your answer on Gparted.. it's not for file-migration. As for simply copying the files, I've been using Windows7 and Ubuntu together for years, often cross-saving files between OS's, and there have not been any problems (even with an NTFS data partition). I still make sure to save important documents in a place they won't be written to by a non-native program, but that's starting to seem like out-of-date paranoia.

---

