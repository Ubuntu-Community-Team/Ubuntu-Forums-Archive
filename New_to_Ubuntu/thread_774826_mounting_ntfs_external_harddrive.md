---
title: "mounting ntfs external harddrive"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by TechDragon on 2008-04-29
I plugged it in to the usb port and a box popped up saying add me to the fstab, so I opened a terminal and sudo'd fstab and added the line it requested.  Now when I plug the drive into the USB port it says I do not have privelges to mount said drive.  What group do I need to add myself to?

Thanks

---

### Post by Brightbelt on 2008-04-29
Try going to either Synaptic Package Manager or Add/Remove and search for NTFS-3g and install that program. It gives linux write access to ntfs drives.

After installing it, go to the 'Applications Menu', then 'System Tools' and you'll see it as the NTFS Configuration Tool. 

This may help. Good Luck, Frank B.

---

### Post by iSplicer on 2008-04-29
What version of ubuntu are you using? If its 7.10 or 8.04 you dont need to install ntfs-3g... use the mount command with "sudo" infront.

eg. sudo mount /dev/sdax... etc etc

---

### Post by TechDragon on 2008-04-30
added the ntfs-3g config tool enabled the features, rebooted, added the appropriate line to my fstab, rebooted.

now it throws no errors, but doesn't even appear to see the drive at all.

any ideas?

btw using 7.10  --- 8.04 = BUGGY!

---

### Post by TechDragon on 2008-05-01
Okay, figured it out. 

Do not add anything to fstab.

Install the ntfs-3g configuration tool.
Launch tool you will be given the option to allow read access to an external drive
Click ok 
reboot
launch ntfs-3g tool again now you will be given a new option.  
Click both options = on
click ok
reboot

Should work

---

