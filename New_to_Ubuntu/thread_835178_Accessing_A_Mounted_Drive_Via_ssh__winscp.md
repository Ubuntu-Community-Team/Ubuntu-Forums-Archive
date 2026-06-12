---
title: "Accessing A Mounted Drive Via ssh / winscp"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by KevinD_Atl on 2008-06-20
[FONT="Tahoma"]So I mount a drive to my other PC, let's say 192.168.1.110 and can access just fine in Ubuntu, with full permissions.  When I'm using SSH client, like WinSCP for example; How can I access that drive?  I thought you could find it in /mnt and find it in there, after I mount it but cannot find it.  Is it possible to access this via WinSCP so I can move some files over?[/FONT]

---

### Post by ilrudie on 2008-06-20
if its an external usb drive or similar its probably mounted in /media.  On the box with the drive connected navigate to the drive in nautilus and then click the icon that looks like a little piece of paper with a pencil on it just above the list of "places" on the left side of the nautilus browser.  The icons to the right of the little paper icon should change to a text box which reveals the path to the device.

---

### Post by KevinD_Atl on 2008-06-25
I have figured out external devices and CD-ROMS, but still can't find the 'link' to the already mounted "mapped" drive.

---

### Post by ilrudie on 2008-06-25
Run a ```
df -kh
```  Does the drive show up in that list?  The last column will show where it is mounted.

---

