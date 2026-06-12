---
title: "Installing Ubuntu on slave"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by BugJuice on 2013-06-04
I currently have windows 8 pro on my computer 64 bit. I have it installed on my SSD and i have a slave HDD for my files. My SSD isn't very big to dual boot so i want to install it on my slave. How would one go about this?

---

### Post by Mark Phelps on 2013-06-05
I really doubt the HDD is a "slave" as you put it -- because that's a term held over from the IDE disk controller days when you had to jumper multiple drivers as "master" and "slave".  Most likely, you have SATA disk controllers and cabling, and the whole master/slave does not apply.

Anyway ... the FIRST thing you should do is boot from an Ubuntu LiveCD or LiveUSB and see how well it detects your hardware and installs working drivers.  Any problems you find then will range from trivial to impossible to fix.  That way, you will know what to expect when you do the actual install.

Also, if your PC uses UEFI boot, that is much more complicated than just sticking in the Ubuntu install media, booting from it, and installing.  I don't use UEFI myself, so you will need to wait until a UEFI expert comes along for detailed advice.

Win8 comes with a feature for making a Recovery drive.  BEFORE you jump into installing Ubuntu, you should read the thread and make the drive:  [http://www.eightforums.com/tutorials/5132-recovery-drive-create-usb-flash-drive-windows-8-a.html]("http://www.eightforums.com/tutorials/5132-recovery-drive-create-usb-flash-drive-windows-8-a.html")

---

