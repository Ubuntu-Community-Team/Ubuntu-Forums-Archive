---
title: "Ubuntu not loading after boot menu"
date: 2015-10-31
forum: New to Ubuntu
---

### Post by daemonxaneo on 2015-10-31
I am trying to boot Ubuntu from a 8gb usb and i have followed the instructions for downloading it but when i geet to the menu to select if i want to boot it without installing it and all the other stuff, when i select install Ubuntu it gives me a gray screenbwith text that says at the end "[end kernel panic not syncing vfs" sorry if this is vague, im fairy inept at computers.

---

### Post by yancek on 2015-10-31
Did you do an md5 checksum on the Ubuntu iso file you downloaded:  in the directory where the iso file is from a terminal type:  md5sum Ubuntu.iso.  You need the actual/exact name of the Ubuntu iso in the command, case-sensitive.  This is to verify the download was good.  Compare it to the md5sum for the iso you downloaded at the Ubuntu site.  If they are not exactly the same, there's no point in trying to use it as you will have problems.

The normal process after downloading the iso is to "burn it as an image" or use software designed to create a bootable usb and boot from it.  Which process did you use and which software?

---

