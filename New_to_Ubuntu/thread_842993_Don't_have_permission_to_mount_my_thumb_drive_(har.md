---
title: "Don't have permission to mount my thumb drive (hardy)"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Moey on 2008-06-27
Finally decided to take an older dell that I had laying around (p4 system) and install Ubuntu (hardy) on it and set it up as a media server for my Xbox 360.  

Everything was going fine, then today I plugged by 2gb thumb drive into it to transfer some files and when I try and access the thumb drive I get the following message.  "Cannot mount volume.  You are not privileged to mount the volume"

This was a fresh install from a live cd.

Any help would be greatly appricated.

I have searched alot for a solution for this, but nothing seems to fit my situation.  Thanks

---

### Post by ConMan318 on 2008-06-27
You could try hitting Alt + F2 and then typing "gksudo nautilus" so you would be root in the GUI.  Then mount it.

---

### Post by gnuwatch on 2008-06-27
type in terminal    sudo nautilus

this will open up a root terminal which should give you the permission to access the drive

---

### Post by defrex on 2008-06-27
Mind you, that doesn't explain why you can't mount it yourself in the first place...

---

### Post by Moey on 2008-06-27
Alright,  I just tried gksudo nautilus and it opened up the root folder.  From there I clicked on my thumb drive on the left side of the window (places) and I get the error, "Cannot mount volume.  Unable to mount volume."  Then I can expand the details and it says "Failed to write lock '/dev/sdb1': Resource temporarily unavailable.  Error opening partition device: Resource temporarily unavailable.  Failed to mount '/dev/sdb1': Resource temporarily unavailable."

Thanks for the quick response guys,  I have been tinkering with Ubuntu for about a year and a half now with dual boots, and this is going to be my first computer only runnung ubuntu.

Also if this helps,  the thumb drive is Fat32 and works fine on the windows laptop next to this computer.

---

### Post by Moey on 2008-06-27
> **defrex said:**
> Mind you, that doesn't explain why you can't mount it yourself in the first place...

Im sorry but I dont completly understand that.

Im trying to just be able to plug my thumb drive in and be able to read/write on it.  I know I had no problems doing that on the previous version of ubuntu that I used (gutsy?).

---

### Post by Moey on 2008-06-28
Anyone else have any ideas???

---

### Post by cprofitt on 2008-06-28
> **Moey said:**
> Anyone else have any ideas???

My assumption based on what has been posted is that your thumb drive was last used in a Windows machine and you did not use the option to eject it or safely remove the device... this means that the FS is still marked as in use by Windows.

---

### Post by Moey on 2008-06-28
I am aware of the problem with windows locking things that have not been removed properly, but I am sure that I have removed my thumbdrive correctly.  I have a laptop sitting right next to the my linux box and have tried if a few times....still no love....

oh ubuntu...this is the first time I couldnt google my way out of a problem

---

### Post by Moey on 2008-06-29
Anyone else have any ideas, probably going to bump this to another forum if I cant get it figured out.

---

### Post by bertlacy on 2008-06-29
I had the same problem, first thing you need to do is open Synaptic and install ntfs support.  Just type ntfs in the search option. 

Then with the drive in, you can use the force mount option.  Just type sudo force mount -t 'location of thumb drive'

---

### Post by king leoric on 2008-06-29
try rebooting your system

---

### Post by Under_score on 2008-06-29
I had this same problem a while ago, the computers at my uni (which run linux), wouldn't let me mount my usb, it kept saying that it wasn't recognised or something.

To solve it I had to 'clean' the usb, I typed in the commands, "unmount usb", "clean usb" and "mount usb", in that order into the terminal, that solved the problem.

I don't know if that helps, but I think the solution would be similar to the way in which I did it, if its the usb not being recognised.

---

### Post by bertlacy on 2008-06-29
I apologize, i gave the wrong command, here is what you will need to do to get it work...

mount -t ntfs-3g /dev/sdb1 /media/"name of device"

Just replace "name of device" with the name of your usb drive.  You can get this name from the 'Computer' link

---

### Post by nothingspecial on 2008-06-30
I may be way off the mark here but you`ve not locked the thumb drive have you?

---

### Post by BandD on 2008-06-30
> **bertlacy said:**
> I apologize, i gave the wrong command, here is what you will need to do to get it work...

mount -t ntfs-3g /dev/sdb1 /media/"name of device"

Just replace "name of device" with the name of your usb drive.  You can get this name from the 'Computer' link


Generally thumb drives (and other external storage devices) are formatted as fat32 out of the box.  And only change unless the owner of the devices reformats it.  Plus, the OP stated on the first page of the thread that the drive is indeed formatted in fat32.  So the ntfs fix probably won't help in this case.

---

### Post by Moey on 2008-06-30
I have tried to restart my computer multiple times, still nothing.  

The thumb drive is formatted in Fat32, so the ntfs support doesnt apply to this (I do have it installed though)

When I try the command in terminal "unmount usb" I get command not found.

Im thinking about just creating a new partition, backup all of my files on there, then reinstalling hardy, then just merging the two partitions after.

I really didnt want to do that because I already have twonky setup to stream media to my xbox 360 (and it works wonderfully if anyone was wondering).

Any last ideas, or should I try the reinstall, and if that fails just go back to gutsy?

---

### Post by BandD on 2008-06-30
You are getting the command not found because that isn't really the command to unmount something.  Try this instead:

```
umount usb
```

(note the absence of an 'n')

Before you try to reinstall, see if the drive will mount with the LiveCD.  If it doesn't then I wouldn't bother with all the trouble of a re-install becuase it probably won't work anyway.

I'm sure there is a way to get that stick mounted.  A reinstall seems a little extereme, IMHO.

---

### Post by BandD on 2008-06-30
Can you post the results of:

```
sudo fdisk -l
```

with your thumb drive plugged in?

---

### Post by novatotal on 2008-06-30
had the same issue heres how I solved it

eduardo@eduardo-desktop:~$ sudo fdisk -l
Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x77b84e2a
Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sda1 * 1 1246 10000000 7 HPFS/NTFS
/dev/sda2 1247 38913 302560177+ 5 Extendida
/dev/sda5 1247 37295 289563561 83 Linux
/dev/sda6 37296 38540 10000431 83 Linux
/dev/sda7 38541 38913 2996091 82 Linux swap / Solaris
Disco /dev/sdf: 1001 MB, 1001914368 bytes
255 cabezas, 63 sectores/pista, 121 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000a745d
Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdf1 1 121 971901 b W95 FAT32

Last entry is the thumb drive(needs to be atached)

And then:

eduardo@eduardo-desktop:~$ sudo gedit /etc/fstab
# /etc/fstab: static file system information.
#
#
proc /proc proc defaults 0 0
# /dev/sda6
UUID=918ce997-5ad3-4eb1-9fa3-f6732508a28e / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=ec01b5a5-d57e-4c5e-bcab-2bfe3a38e9f9 /home ext3 relatime 0 2
# /dev/sda7
UUID=3b3444cb-817e-4993-857a-9ef2c4e0fe0e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Montar usb
UUID= 0x000a745d
#/dev/sdf1(leave five spaces here)/media/usb vfat users,exec,noauto,noatime,rw 0 0

Last 3 lines added by me
uuid identifies the port your usb is atached to I think
sdf1(one), is my pendrive on my machine
hope this helps you

---

### Post by Jackfrost123 on 2008-07-04
hey novatotal tried your advice to no avail, can you please exmplain some more the steps taken, how do you find the uid? Why do you add the line? Why isn't there to begin wiht? Although the drive appears in my computer.

---

### Post by Moey on 2008-07-09
just a quick note.

did another fresh reinstall on hardy, and my thumbdrive works fine now.

not sure what caused this because i used the same disk to install, and didnt change any settings

thanks for the help everyone!

---

### Post by Jackfrost123 on 2008-07-12
I am again having the same problems...and I am not even using windows...just my pen drive and ubuntu, they won't work together, I have to open gparted and mounted from there because it wont mount automaticall, and even then it wont copy files to it...

---

