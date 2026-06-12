---
title: "Virtual CD Shell Script"
date: 2007-12-29
forum: Programming Talk
---

### Post by InGunsWeTrust on 2007-12-29
I am trying to make a shell script that will do the following:

General Description:
The script will mount an ISO as a CD in the directory /media/cdrom1. The script should appear in the right click context menu of an ISO in nautilus.

Normal flow of events:
1. Ask for sudo password to run the rest of the script as root.
2. Check if anything is already mounted in /media/cdrom1.
3. unmount anything that is already mounted in the directory.
4. Mount the selected ISO from nautilus into /media/cdrom1.

So far I know that if I I put a script in /home/username/.gnome2/nautilus-scripts it will appear in the right click context menu of everything listed in nautilus. If possible I'd like it to only appear if I right click an ISO. This would be nice but not required.

I also know that the command "sudo mount myiso.iso /media/cdrom1 -t iso9660 -o ro,loop=/dev/loop0" will mount the ISO as desired. The only thing I need to know is the syntax I need to check if something is already mounted. To unmount. and to remount the selected thing from nautilus.

---

### Post by disturbed1 on 2007-12-29
Take a look at this program, it's a shell script something similar to what you wan to do. Perhaps the code could be useful.

[http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml)

---

### Post by InGunsWeTrust on 2008-01-14
I can't seem to install it. There is some wierd error trying to install it so I can't really see what it is going to do. And I don't see a place for the source code on that particular website so all i have is an install script that doesn't work.

---

### Post by disturbed1 on 2008-01-14
Just open the install.sh with a text editor.

---

