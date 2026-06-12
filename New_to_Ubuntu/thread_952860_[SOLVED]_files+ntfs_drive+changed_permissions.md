---
title: "[SOLVED] files+ntfs drive+changed permissions"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by geokok1981 on 2008-10-19
Hi. I have an external ntfs formatted hard drive. 
I noticed today that when I copy my home files into that drive
all the permissions change to "root" (which may be reasonable cause 
they change back to "my_username_here" when copied back to my desktop.

The one thing that is weird though is that the box 
"allow to execute as program gets ticked and stays that way even after 
copying back to the desktop. That is really annoying especially when it 
comes to text files where the dialog "do you want to run the file or view 
its contents" pops up all the time...

Any clue on how to prevent this from happening..?

---

### Post by geokok1981 on 2008-10-21
anyone?...

---

### Post by Titan8990 on 2008-10-21
This is because EXT3 permissions do not work on a NTFS drive.

---

### Post by Nepherte on 2008-10-21
You can set permissions and ownership of the disk in /etc/fstab.

This is an example I have in my /etc/fstab:
```
# Entry fo Windows (/dev/sda1)
UUID=EE7017327017014F   /media/Windows  ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137 0       0
```
dmask defines the permissions of directories. It uses the complement (7 - x) of real permissions. So in this case, 027 permission is actually 750. fmask defines the permission of files, in this case 137 -> 640.

gid determines who the group owner is (100=users) and uid determines the user owner (1000=myuseraccount).

For a detailed overview of fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by geokok1981 on 2008-10-22
@Nepherte.

I appreciate your effort to help me but the truth
is that the solution you provide me with really,,,
overwhelms me....

Any chance there is an easier workaround for this?
Something that I won't have to search for a guide the 
next time I want to apply it?
Thanks.

---

### Post by Nepherte on 2008-10-22
I don't know of a easier solution. But I'll walk you through it.

[LIST=1]
[*]First we are going to figure out the unique id of your disk which we will use later on. You can find the so-called "UUID' by opening places > computer. Right click on your external ntfs disk and choose properties. Pick the volume tab and look for UUID.

Another way of doing this is to run this command in the terminal:
```
sudo blkid
```
If you don't find your disk immediately, look for type="ntfs" and Label to identify it.
[*]We will now create the mount point:
```
sudo mkdir /media/just_give_it_a_name
```
[*]Open up /etc/fstab with:
```
gksudo gedit /etc/fstab
```
and put in a line like this:
```
UUID=yourdisksuuidnumber   /media/just_give_it_a_name  ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137 0       0
```
Don't forget to replace yourdisksuuidnumber and /media/just_give_it_a_name with the actual values.
[*]At bootup the changes you made, will be permanently. To make it available in this session:
```
sudo mount -a
```

I hope this helps you out. If you have further questions, feel free to ask.
[/LIST]

---

### Post by Titan8990 on 2008-10-22
Isn't the default gid for the admin group 1000 and not 100?

---

### Post by Nepherte on 2008-10-22
uuid=1000 is the user's account, gid=100 is the group users. Root is uuid=0 and gid=0. I figured it would be easier for him to own his own external disk as long as there are no "system files" on it.

---

### Post by run1206 on 2008-10-23
also, make sure your windows partition name is not two or more words separated (i made the mistake of making the label "Hard Drive" in windows, screwing up my mount points in Linux :oops:, so i changed mine to HDD.  Thanks to Nepherte for the walkthrough :D

---

### Post by geokok1981 on 2008-10-23
Thank you for all the help!!
I'' ll try it as soon as I can.
However, I have one last (maybe silly) question.

Will any of this affect the way 
1)my external drive interacts with windows xp 
when connected to my laptop or 
2)accesed from the win machine through samba while being attached to my linux box?

Also, my drive is currently named "My book".
Should I rename it? If yes, how (without formatting if possible).

---

### Post by Nepherte on 2008-10-23
1) No. The changes made to /etc/fstab are for the computer only, not the external disk. They basically tell the computer how and where to access your external disk but it doesn't change anything to the disk itself. You can pretty much compare it with plugging in an usb stick, only this time the computer knows about the disk in advance (you listed it in fstab) and you told the computer exactly what to do with it (again, fstab).

2) Again, no. Linux knows what to do with the disk for itself (fstab). Samba will deal with the part of making it available for the network so windows can access it. Of course, Samba itself relies on linux knowing what to do with the disk.

"My Book" is just a label given to the disk. You can change it without reformatting it. But I don't see a reason why you should rename it. But hey, if the name does't suit you... The label of the disk itself has nothing to do with attaching the disk to your computer.

---

### Post by geokok1981 on 2008-10-24
Tested it. Works like a charm.
A million thanks again for your excellent help
and attitude!

---

