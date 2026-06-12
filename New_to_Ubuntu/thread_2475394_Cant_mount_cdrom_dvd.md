---
title: "Cant mount cdrom dvd"
date: 2022-05-25
forum: New to Ubuntu
---

### Post by bartsimp63 on 2022-05-25
Hi this is the first time i have used ubuntu and cant get my cd/dvd to work its showing up in the bios but wont auto mount when i insert disk.
I have searched but cant seem to find the answer.
I have tried sudo mount /media/cdrom0/ -o unhide.
i get cant find in /ect/fstab.

Any help appreciated.

---

### Post by ajgreeny on 2022-05-25
It's a long time since I used a CD or DVD but if I remember correctly you do not mount them in the same way you would do a hard disk partition or flash drive.

I think I remember the disks showing in the file-manager once inserted, though this will depend on your settings for **Removable Drives and Media**.
How you find that setting will be dependent on the DE version of *ubuntu that you're using so I will leave you to search for that.  In Xubuntu it is easily found in the menu or the Settings-Manager window.

---

### Post by Holger_Gehrke on 2022-05-25
ajgreeny is both right and wrong. By default Data CDs and DVDs should be mounted automatically and they should come up in /media/$USER/{volumelabel}, but you can manually mount them unless udisks2 (the automounter) is acting so quickly and persistently that it automatically remounts media you unmounted to try to mount them manually (don't laugh, that happened just now, had to go into the setting he mentioned and turn it off).

The command to mount a CD-ROM manually is
```

sudo mount -t iso9660 /dev/cdrom /directory_to_mount_the_cd_into

```

The option '-t' gives the type of file system to look for on the device. For CD this is iso9660 (with either Rockridge or Joliet extensions  to give Unix style permissions and filenames longer than 8.3), on DVD it's usually udf (possibly with a iso9660 compatibility bridge). '/dev/cdrom' is the device file for a CD-rom drive. The actual device file is usually named something like /dev/sr0, /dev/cdrom is a symbolic link (and so is /dev/dvd, usually to the same actual device file). The 'directory_to_mount_the_cd_into' is a directory in which you want the contents of the CD to appear. This directory should exist, be accessible to you and be empty (if it isn't it's content will be inaccessible while the CD is mounted).

Alternatively you can use udisksctl to make the automounter mount the disk
```

udisksctl mount -b /dev/cdrom

```
that should mount the CD in the standard place (/media/$USER/{volumelabel})

Holger

---

### Post by guiverc on 2022-05-25
You miss-spelt /etc/  (/etc/fstab)  so maybe your command/accessing it was also miss-spelt.

You haven't provided any OS/release details, as I've used Ubuntu machines that auto-mounted & others that didn't.  I just grabbed a CD/DVD & inserted it into this box, and it doesn't auto-mount; but I was asked if I want to open it in a file-manager; clicking that does cause it to auto-mount; but those prompts can be disabled.  (*also I'm using Lubuntu/LXQt currently and wasn't going to logout & switch to GNOME to see how that DE responds* *given your release maybe very different*)

Do you know the drive actually works...  I've had 3 drives fail in the last maybe 8 uses of them; as drives are getting old & mechanics fail. In my case my replacements are from recycled hardware (*meaning drives are old anyway*) but most dead drives will show up in BIOS, just aren't usable.  (*yours maybe good; this is prompted by my many recent failures*)

---

### Post by ActionParsnip on 2022-05-26
```

sudo mkdir /media/cdrom
sudo mount -o loop /dev/sr0 /media/cdrom

```

Should do it

---

### Post by Holger_Gehrke on 2022-05-26
@ActionParsnip: '-o loop' ? That's for mounting image files through a loop device. At best this will add an unnecessary loop device into the mount (basically you're treating /dev/sr0 as an image and using a new /dev/loop?? to access it) at worst it will fail.

Holger

---

### Post by ActionParsnip on 2022-05-26
D'oh. My bad. Yes omit the loop option

---

