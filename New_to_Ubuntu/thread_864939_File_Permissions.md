---
title: "File Permissions"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by finlow on 2008-07-20
Hi I have recently mounted an external hard drive using the following.

mkdir /media/SeaGate
sudo mount -t vfat /dev/sda1 /media/SeaGate/

After doing this I can see all my files and open them but I cannot write to them. I get an error message telling me I do not have the necessary permissions to save the file.

Dose any one have any advice so I can write to all my files.

Thanks for any help.

---

### Post by sdowney717 on 2008-07-20
try using
'gksudo nautilus'
this will open up directories as root user
and then maybe you can go into permissions and put yourself as a the owner for the files on the drive

'gksudo whateverprogramyouuse'
to open up the files as root
this should give writing ability

---

### Post by finlow on 2008-07-20
Hi thanks that seems to have solved the problem.

---

### Post by coffeecat on 2008-07-20
> **finlow said:**
> Hi I have recently mounted an external hard drive using the following.

mkdir /media/SeaGate
sudo mount -t vfat /dev/sda1 /media/SeaGate/

After doing this I can see all my files and open them but I cannot write to them. I get an error message telling me I do not have the necessary permissions to save the file.

You've mounted the drive as root which is why, as the ordinary user, you don't have permission. But why mount it that way? Is it a USB drive? Just plug it in and it will be automounted with a Nautilus window popping up. Then you'll be able to read, write, drag, drop, copy and delete to your heart's content.

Or have you had a problem with automounting?

---

### Post by finlow on 2008-07-21
Hi, Yes I recently upgraded from ubuntu 6.06 to ubuntu 8.04. Under 6.06 my device was automatically detected but not using 8.04.

---

### Post by candtalan on 2008-07-21
Is it automatically detected if you use a (8.04) live CD? I wonder if the upgrade  ha ssomehow left something out  about automatic detection?

---

### Post by Rolcol on 2008-07-21
After mounting it, can't you change the owner so you don't have to be root to write files to it? (chown)

---

