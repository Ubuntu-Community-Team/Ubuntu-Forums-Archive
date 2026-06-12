---
title: "How to remove auto mount to /dev/sda2"
date: 2017-09-09
forum: New to Ubuntu
---

### Post by vtx1001 on 2017-09-09
I pretty new to Ubuntu and link OS; I had set the /dev/sda2 to auto mount via disk UI interface in gnome. 

So getting failed boot up? Is there a way for uncheck the auto mount command via recovery console at boot up?

What is the command to remove auto mount from /dev/sda2;  I have check /etc/sftab  the entry is not there?:o

---

### Post by yetimon_64 on 2017-09-10
> **vtx1001 said:**
> I pretty new to Ubuntu and link OS; I had set the /dev/sda2 to auto mount via disk UI interface in gnome. 

So getting failed boot up? Is there a way for uncheck the auto mount command via recovery console at boot up?

What is the command to remove auto mount from /dev/sda2;  I have check /etc/sftab  the entry is not there?:o

The disks utility may possibly have used a UUID entry in /etc/fstab for mounting and not the /dev/sda2 naming style you are expecting to see.

Try the next command in the terminal or on the recovery console (without sudo if on a root/recovery console) to find the UUID of /dev/sda2 and compare that UUID with the entries in /etc/fstab ...
```
sudo blkid -c /dev/null | grep /dev/sda2
```
You will need to enter your user password for sudo (if in the GUI) and it will not show in the terminal but that is normal, press enter and check the output of the command.

You can edit the /etc/fstab file in the terminal with the next command. Again you don't need "sudo" if on a recovery/root console.
```
sudo nano /etc/fstab
```

If you find the correct entry with the UUID as returned by the above blkid command all you need to do is put a hash symbol "#" at the start of the line with "UUID=", with /dev/sda2's UUID in, and save the file. **Edit:** putting a "#" symbol at the start of an entry is referred to as "commenting out" an entry. You nee to comment out the correct line to block fstab from processing  the loading of /dev/sda2.

To save a file in the command line editor "nano" use the key combination of "ctrl + o" (the letter "oh" not a zero) and then press the Enter key when asked to save the file (the address /etc/fstab should be noted when prompted for saving the file). 

To exit the editor when completed saving use the key combination "ctrl + x".

A good idea when editing /etc/fstab, after saving the file and BEFORE doing a reboot, is to run the next command...
```
sudo mount -a
```
This command will not return anything but will return to a normal prompt if all is OK; however if you have made a mistake the output of the command will show it up clearly before you try to reboot the system with a faulty fstab file (which can cause serious headaches at times). Best to check the file is good with the command first always.

Good luck and cheers, yeti. :)

---

