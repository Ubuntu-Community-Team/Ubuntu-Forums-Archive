---
title: "Possible to access my windows partition?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by leotemp on 2008-04-30
Well its day 2 of my conversion to ubuntu and I am really damn pleased, it looks better then vista and mac and everything i could want seems to be free and just trickle in from the PM, its like dating a super model!

1] So now that i have it all up and running i need to get all my crap off the windows partition and I don't want to burn 10 DVDs to do it plus I have photoshop docs that are larger then DVDs :(  Can I just somehow access the windows partition and move them over to my new tasty OS?

2] When i get this all exactly how I want it, is it possible to somehow make a backup or image of the whole thing so that If something terrible happens i can just slap it all back on without reinstalling? I also have other identical machines i wouldn't mind putting my install on without going through the whole process.

Ubuntu is totally F-ing METAL :guitar:

---

### Post by inferiorwang on 2008-04-30
Yes you should be able to grab your files unless they're encrypted.  Ubuntu supports windows file systems.  You should be able to go to the Places menu and see a list of drives available, but they won't have the labels you're used to in windows.

---

### Post by leotemp on 2008-04-30
Doh! The only thing i see listed under places for drives is "computer" and the only thing listed under that is my DVD and "File System" which appears to be straight ubuntu..

---

### Post by pikabuntu on 2008-04-30
places > computer > it should be in here. it will be named something like: 27.5 GB media (yours will be different)

---

### Post by leotemp on 2008-04-30
huh, i dont have anything like that all i have is:

Leo
Desktop
File System
Network Servers
Trash
-------------
Documents
Music
Pictures
Video

---

### Post by cwgatling on 2008-04-30
You might have to mount it. Try a 'sudo fdisk -l' from the terminal and identify the location of your partition (e.g. /dev/sda2). Then do 'sudo mount -t ntfs /dev/sda2 /mnt' /mnt can be any mount point you want. apt-get install ntfs-3g to have read+write access to NTFS partitions.

---

### Post by woocashacn on 2008-04-30
> **leotemp said:**
> huh, i dont have anything like that all i have is:

Leo
Desktop
File System
Network Servers
Trash
-------------
Documents
Music
Pictures
Video
Maybe your windows session was not clearly closed (hibernated / power reset) and that causes NTFS / FAT not being mounted automaticaly...

(guessing as I had such problem)

---

### Post by leotemp on 2008-04-30
im not sure i understand so is it:
'sudo mount -t ntfs /dev/sda2 /[folder you want mount to appear?]'

---

### Post by cwgatling on 2008-04-30
That's it exactly. For example, you could do:
mkdir /windows-mount
sudo mount -t ntfs /dev/sda2 /windows-mount

Then 'cd /windows-mount' to (hopefully) see your files.

---

### Post by doorknob60 on 2008-04-30
It depends, type the following command in a terminal (Applications ->Accessories ->Terminal)
```
sudo fdisk -l 
```
THen, looking at the output, choose the NTFS one
EXAMPLE:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23549368+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            9364        9729     2939895    5  Extended
/dev/sda3            2933        9363    51657007+  83  Linux
/dev/sda5            9365        9729     2931862+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
for me, my windows partition is /dev/sda1 which has the type NTFS (default in Windows XP), but it might be different for you, just look for NTFS. Then, type the following command:
```
sudo mount -t ntfs /dev/[whatever] /[wherever you want it, I use /windows personally] 
```

Also, you could add a line to your /etc/fstab file to make it automount when you start your computer, but I kinda forgot how to do that :P

---

### Post by leotemp on 2008-04-30
Thanks Gatling! I am in my windows right now gutting it from the inside out! :)

Question, will this mount be permanent or do i have to do this every time i boot?

---

### Post by leotemp on 2008-04-30
heh, thanks for the info, ill just google that as i am sure there is an easy to find answer for that one, right now my big problem is I only know how to relate my questions in windows terminology which just pulls windows results in google.

---

### Post by cwgatling on 2008-04-30
Excellent man! Well done. Yep, you've got to add a line to /etc/fstab as doorknob60 said. Psychocats has the answer here -> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
I'm not at my Ubuntu machine at the moment, so I couldn't tell you the exact syntax.
Good luck :)

---

