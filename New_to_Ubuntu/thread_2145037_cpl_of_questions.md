---
title: "cpl of questions"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by mreyna16 on 2013-05-14
I am currently dual booting windows 8 and ubuntu 13.04 both uefi and i have a cpl of questions...



how can i hide ubuntu drives (partitions) in windows without affecting ubuntu and vise versa?

how can i uninstall software such as boot-repair? i dont think ill need it anymore and id like to remove it

last but not least, i have a fat formatted partition to be used for my media files by both windows and ubuntu... so, in ubuntu, how can i link my music folder in /home to the music folder in my other partition? id like for my music folder in ubuntu to show whatever is inside plus the other music folder i have in the separate partition

---

### Post by fantab on 2013-05-14
Are you dual booting with WUBI? otherwise windows will not show Linux partitions. 

Use Synaptic package manager to uninstall Boot-repair. Use option 'mark for complete removal'.

Instead of FAT use NTFS. But that's ok. to link your media files:

[FONT=monospace]ln -s /path/to/folder /location/of/link[/FONT]

---

### Post by mreyna16 on 2013-05-14
> **fantab said:**
> Are you dual booting with WUBI? otherwise windows will not show Linux partitions. 

Use Synaptic package manager to uninstall Boot-repair. Use option 'mark for complete removal'.

Instead of FAT use NTFS. But that's ok. to link your media files:

[FONT=monospace]ln -s /path/to/folder /location/of/link[/FONT]


im new to linux, but out of the top of my head i dont think so... wubi is when u use the installation from windows right? and what i did is created for both os's a uefi usb stick and installed them from there seperately

ill try out synaptic

i was under the impression that ubuntu could not see ntfs partitions but now that i think about it, then how is it seeing my windows partitions lol 

im gonna format it first to ntfs then ill try that command out

---

### Post by Kopkins on 2013-05-14
A better, but more difficult (for beginners) way to do that, is to edit the fstab file. That file contains the information of where to mount your partitions when you boot. I don't think that putting a symbolic link would allow for automatic mounting of the partition with the music on it. So before using your music I think you would have to mount your partition each time, or basically Ubuntu will think that the files don't exist. 

Before editing your fstab file you should make a backup of it in case something goes wrong. 

```
sudo cp /etc/fstab /etc/fstab.old
```
If you need to revert the changes for any reason use this:
```
sudo mv /etc/fstab.old /etc/fstab
```

Then you need the UUID for your music partition. I'm assuming you know the partition number of your music partition. For this example I'll use /dev/sda5.

Run the command ```
ls -l /dev/disk/by-uuid/
```

and you should get an output that has the UUID's highlighted followed by their partition number. 

For example it might look like ```
lrwxrwxrwx 1 root root 10 May 13 12:31 a3ca2474-5ec5-4360-a351-4abf127db18e -> ../../sda6
lrwxrwxrwx 1 root root 10 May 13 12:31 b6cce33a-f9c3-4064-84ce-98d7d8b3a1fb -> ../../sda5
```

This part 'b6cce33a-f9c3-4064-84ce-98d7d8b3a1fb' is what you want for /dev/sda5 in this example. 

Then you'll want to open up the fstab file for editing. Make sure you have the original backed up!

```
gksudo gedit /etc/fstab
```

You should have something like this. 
```
# 
# /etc/fstab: static file system information
#
# <file system> <dir>   <type>  <options>       <dump>  <pass>
# /dev/sda4
UUID=4e450a74-d94d-45af-870e-1e156b9cf99a       /               ext4            rw,relatime,data=ordered 0 1

# /dev/sda3
UUID=7d545aa0-da1a-44c7-9a22-a78a30d5e453       /boot           ext4            rw,relatime,data=ordered 0 2

# /dev/sda1 LABEL=EFI
UUID=70D6-1701          /boot/efi       vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro      0 2


```

Then you just need to add your partition

You should be able to just follow the other entries, just add yours onto the end like: ```
# /dev/sda5
UUID=<your_UUID>       /home/<your_username>/music           ext4            rw,relatime,data=ordered 0 2
```

Except where it says UUID= you want to make sure you put in the UUID you got from the earlier command and make sure you change the <your_username> to whatever your commandline username is. 

Then all you have to do is reboot and you should have the music partition mounted at /music in your home directory.

Good luck!

Kopkins

---

### Post by mreyna16 on 2013-05-14
> **Kopkins said:**
> A better, but more difficult (for beginners) way to do that, is to edit the fstab file. That file contains the information of where to mount your partitions when you boot. I don't think that putting a symbolic link would allow for automatic mounting of the partition with the music on it. So before using your music I think you would have to mount your partition each time, or basically Ubuntu will think that the files don't exist. 

Before editing your fstab file you should make a backup of it in case something goes wrong. 

```
sudo cp /etc/fstab /etc/fstab.old
```
If you need to revert the changes for any reason use this:
```
sudo mv /etc/fstab.old /etc/fstab
```

Then you need the UUID for your music partition. I'm assuming you know the partition number of your music partition. For this example I'll use /dev/sda5.

Run the command ```
ls -l /dev/disk/by-uuid/
```

and you should get an output that has the UUID's highlighted followed by their partition number. 

For example it might look like ```
lrwxrwxrwx 1 root root 10 May 13 12:31 a3ca2474-5ec5-4360-a351-4abf127db18e -> ../../sda6
lrwxrwxrwx 1 root root 10 May 13 12:31 b6cce33a-f9c3-4064-84ce-98d7d8b3a1fb -> ../../sda5
```

This part 'b6cce33a-f9c3-4064-84ce-98d7d8b3a1fb' is what you want for /dev/sda5 in this example. 

Then you'll want to open up the fstab file for editing. Make sure you have the original backed up!

```
gksudo gedit /etc/fstab
```

You should have something like this. 
```
# 
# /etc/fstab: static file system information
#
# <file system> <dir>   <type>  <options>       <dump>  <pass>
# /dev/sda4
UUID=4e450a74-d94d-45af-870e-1e156b9cf99a       /               ext4            rw,relatime,data=ordered 0 1

# /dev/sda3
UUID=7d545aa0-da1a-44c7-9a22-a78a30d5e453       /boot           ext4            rw,relatime,data=ordered 0 2

# /dev/sda1 LABEL=EFI
UUID=70D6-1701          /boot/efi       vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro      0 2


```

Then you just need to add your partition

You should be able to just follow the other entries, just add yours onto the end like: ```
# /dev/sda5
UUID=<your_UUID>       /home/<your_username>/music           ext4            rw,relatime,data=ordered 0 2
```

Except where it says UUID= you want to make sure you put in the UUID you got from the earlier command and make sure you change the <your_username> to whatever your commandline username is. 

Then all you have to do is reboot and you should have the music partition mounted at /music in your home directory.

Good luck!

Kopkins

that seems practical, but what if i have folders in that partition? i have my music, pictures, videos, etc... im guessing one of the commands above should be changed right? to something more specific? in this case the music folder in that partition

---

### Post by Kopkins on 2013-05-15
This method might not be technically correct, but it should work. 

Make a directory in your /home
```

#this doesn't have to be in your /home, it could technically be anywhere.
#to make it hidden, we'll make it a .folder. 
#as your user:
cd
mkdir .media

```

Change the mount location in fstab to /home/user/.media

Then make some symbolic links to the folders in the hidden folder .media. 

Let's use the three you mentioned, Music Pictures and Video.

```

#for reference, the contents of .media
ls .media
  Music          Pictures          Video

ln -s ~/.media/Music/* ~/Music
ln -s ~/.media/Pictures/* ~/Pictures
ln -s ~/.media/Videos/* ~/Videos

```

This way, you have a filesystem mounted to a hidden location with it's contents linked to the respective folders you want them in.

Kopkins

---

### Post by fantab on 2013-05-15
Instead of automounting with 'fstab' you can manually mount the partition when needed by just clicking on the partition under 'Devices' from Nautilus, the file explorer. It is after all a data partition and you need it mounted only when you need it. I don't automount my DATA partitons... its a personal thing.

My two cents...

---

