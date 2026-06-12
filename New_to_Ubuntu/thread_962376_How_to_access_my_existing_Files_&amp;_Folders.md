---
title: "How to access my existing Files &amp; Folders?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Saurabhdua on 2008-10-29
Hi There!

Relishing my first-stand with Ubuntu.A Gr8-Gr8 option given with this Version 8.0 to install the OS with Windows!

I have done the same.Surfed a lot of Net! However,***_ can someone please tell me on how to access the various files & folders, that are already there in Windows(under My Docs., Pictures..etc.) in the Ubuntu environment??_***:confused:

Places>>Computer comes with CD Drives, Floppy & Filesystem; there is NO Hard disk listed over there!

Please HELP!

---

### Post by philinux on 2008-10-29
Open a terminal. Applications>Access>Terminal

Use this command

```
**[FONT=Courier New]sudo fdisk -l[/FONT]**
```

Thats a small L at the end.

---

### Post by Saurabhdua on 2008-10-29
Ok..What Next?...This lists amount of Hard disk space as well as type of "File System".Mine is NTFS.

I need to access my Resume stored in My Docs. folder(Windows).This command do not seem to solve the purpose!

Please guide..!

---

### Post by philinux on 2008-10-29
> **Saurabhdua said:**
> Ok..What Next?...This lists amount of Hard disk space as well as type of "File System".Mine is NTFS.

I need to access my Resume stored in My Docs. folder(Windows).This command do not seem to solve the purpose!

Please guide..!

Copy and paste the output of the command back here.

By the way how did you install. Was it the live cd or wubi.

---

### Post by germanix on 2008-10-29
If you dual-boot Ubuntu with Windows (which I presume you are) Ubuntu will attempt to make your Windows partitions available automatically. I fthe drive has automatically been made available, an icon for it should appear on the desktop. Double-clicking this should show your Windows partition contents. This Icon could have a name like hda1. First check if the icon is there and advise.

---

### Post by germanix on 2008-10-29
If the icon is not on the Desktop you need to mount the Windows partition. The following instructions need to be carried out at the command prompt, so start by opening the terminal: click Applications>Accessories>Terminal.
You need to identify the Unique Udev ID (UUID) number of your Windows partition. If your computer is relatively new it probably has a Sata hard disk, so type or better copy and paste the following into the terminal: 

sudo vol_id -u /dev/sda1

The above command assumes that the Windows partition is the first on the hard disk. If you know that the windows partition is the second then replace sda1 with sda2

You will be prompted to enter your password, do so.

Make a note of the output of this command. It will show a hexadecimal number, something like 6236501A876FEEFK, yours will be different.

Now you need to create a mounting point. Type (copy/paste) the following:

sudo mkdir /media/Windows

You now need to edit the /etcfstab file. Type the following:

gksu gedit /etc/fstab

A text editor opens. Scroll to the bottom and press enter to create a new line. Then type the following:

UUID=<UUID> /media/Windows ntfs defaults,nls=utf8,unmask=007,gid=46 0 0

Replace <UUID> with the hexadecimal number you noted before, so the start of the above entry should look something like this: UUID=623591A876FEEFK /media/Windows ntfs defaults,nls=      (etc.)
Click File>Save within your text editor to save your changes.

From now on the Windows file system will be made available automatically whenever you Boot and it should appear as an icon on the desktop and within the computer view (Places>Computer) You can also mount it immediately (without first re-booting) when you type:

sudo mount /media/Windows

---

