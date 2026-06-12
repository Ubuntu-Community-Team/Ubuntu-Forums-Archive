---
title: "Helping a mate with ubuntu and xp, trouble with restore disk."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by philinux on 2008-06-07
I need to repair his xp system. And I dont feel like joining a windblows forum they suck.

Using his recovery cd, not got a oem xp disk, go for recovery mode and it asks for a password. Trouble is it says the password is invalid even though his admin account is the original user.

How can I find the password it thinks it needs.

Thanks.

---

### Post by fiddledd on 2008-06-07
Rather than pointing you to a link about the Recovery Console (which I think is what you are using), here's the relevant info:

Remove the prompting of a password

When the Recovery Console starts it will ask for your Administrator password before continuing. In many cases when you have XP pre installed on your computer the Recovery Console will not recognize your Administrator's password. In these situations it is possible to edit a registry setting so that the Recovery Console does not ask for a password. This setting works on both Windows XP Home and Pro editions.

To change this setting do the following:

   1. Click on the Start button.

   2. Click on the Run option

   3. Type regedit.exe in the open field and press the OK button.

   4. Navigate to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\Setup\RecoveryConsole

   5. Change the value of SecurityLevel value to 1

   6. Close regedit

   7. Reboot your computer.

Now the Recovery Console will no longer ask for a password.

Edit:
I forgot to post the link in case there's other info you  need, it's [http://www.bleepingcomputer.com/tutorials/tutorial117.html](http://www.bleepingcomputer.com/tutorials/tutorial117.html)

---

### Post by philinux on 2008-06-07
Excellent. I thought we'd be into a bit of password hacking, slightly disappointed now. :lolflag:

Unless I misunderstand you. We're booting his recovery disk there's a recovery partition on his HD.

---

### Post by spiderbatdad on 2008-06-07
You could try cracking it for fun.[http://lifehacker.com/394100/ophcrack-live-cd-cracks-windows-passwords](http://lifehacker.com/394100/ophcrack-live-cd-cracks-windows-passwords)

---

### Post by philinux on 2008-06-07
Yeah.

But there is only one admin password on the system and this has been set since day one never changed. So what it's expecting is a mystery.

---

