---
title: "I  can't find where I open my floppy ?"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by skalman65 on 2013-04-22
Just install xubuntu 12.04 with a minimal installation.

Now I can't find where I open my floppy 
( yes, Believe it or not, I have and need a old-fashioned floppy:)).

maybee, I might have missed to install something, or is floppy not functioning in xubuntu?

---

### Post by anakai on 2013-04-22
Try this [http://www.ubuntugeek.com/tiphow-to-mountunmount-and-format-floppy-disk-in-ubuntu.html](http://www.ubuntugeek.com/tiphow-to-mountunmount-and-format-floppy-disk-in-ubuntu.html)
I haven't even touched a floppy in 10 years.....hahahha hope it helps

---

### Post by kuifje09 on 2013-04-22
I do not know for sure, but maby you also need to load the floppy kernel module.

you can check if it is loaded with,

lsmod | grep flop

if it is not loaded, then,

sudo modprobe floppy , and then you need to add the floppy to the modules file if it was not loaded at start of the system
as root do :
echo floppy >> /etc/modules

---

### Post by squakie on 2013-04-22
I believe that even if you put a floppy disk in the drive you would probably need to mount it.  I don't have a floppy drive, so I can only guess, but I would think it would be something along the lines of:

mkdir ~/myfloppy  (create a folder called "myfloppy" in your home folder)

sudo mount /dev/floppy1 myfloppy  - you'd have to check in your /dev folder to see what your floppy device is actually called - I used "floppy1" as an example.  Also, I don't know if a floppy device needs special mount options - you have to check man mount to see

After that, the contents should be visible under ~/myfloppy - try pointing the file manager to it.

Also, if there is no disk in the drive, I don't know if it shows or not in the file manager.

Someone may tell me I'm completely wrong - I'm just thinking about what I've had to do with other devices.

---

### Post by kuifje09 on 2013-04-23
if the floppy driver/module is activ, then you can mount the floppy inside your nautilus i.e.
But doing it by hand is not forbidden.:D then you devicefile would probably be /dev/fd0

---

