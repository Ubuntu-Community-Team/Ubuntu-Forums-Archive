---
title: "Removalbe Drives Unmounting automatically"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by wingrider78 on 2012-11-04
Hello, I am running Xubuntu 12.04 and have been for about 3 months.  I have just started having an issue with removable drives unmounting when transferring files to/from them.  The device in question is my samsung android phone.  When trying to transfer a video file from the built in memory, or from the removable sd card, the transfer will start and then after about 3 seconds, both drives will be unmounted, the file transfer will error out, and the drives will be remounted again.  The cycle will continue over and over.

When using any other usb stick, the drive will be mounted and the folder will be displayed automatically.  When using the phone, the icons will show on the desktop, but both drives will not actually mount and display their contents, until double clicked.  

Removing my sd card from the phone and using a card reader, everything works as normal, so it's not a faulty card.  

Trying the same scenarios with my wifes phone will produce the same results...she also has the same make/model phone (different ROMs though).  

Is there anything to test/try to fix this issue???  Thanks for looking...

---

### Post by newb85 on 2012-11-04
This might sound like a cop-out, but it sounds to me like the issue is the phone.

> **wingrider78 said:**
> When using any other usb stick, the drive will be mounted and the folder will be displayed automatically.  When using the phone, the icons will show on the desktop, but both drives will not actually mount and display their contents, until double clicked.

This could well be a setting or property of the phone.  I know that with my HTC Android phone, I can set in the phone whether or not it automatically mounts.  My guess, though, is that functionality is provided by the phone manufacturer, not the OS.

---

### Post by wingrider78 on 2012-11-05
I understand that logic, but I've had the phones for around 3 years.  I've been using Ubuntu since Hardy, and just recently switched to xubuntu within the past three months.  I've only had this problem for about two or three days.  I just tested the phones on my laptop which also has xubuntu, and the phones act normally. Something has to be different about the desktop installation to be causing this problem, but other than the updates nothing has been changed on either machine for at least a month.

---

### Post by newb85 on 2012-11-05
Fair enough.  Something else I've noticed with my phone is that Ubuntu doesn't treat it exactly like a thumb drive.  (The icon assigned to it looks like a .mp3 player, rather than like a flash drive.)

Could it have to do with your settings for automatic behavior based on content?  (For example, your phone might contain photos whereas your flash drives don't.)  The automatic behavior could require unmounting.

---

### Post by wingrider78 on 2012-11-05
I don't think that would be the issue since I can take the card out of my phone and put it in a card reader and the card will automount and display the contents just like any other removable drive/cd/dvd does.

I've also tried using different usb cables and different usb ports on the computer...

---

### Post by wingrider78 on 2012-11-10
I have now also tried the phone on a winxp box at my dad's house, and everything works normally.  Can anyone think of any reason why it would keep un-mounting itself on this computer only???  Is there anything to run in terminal to see what is happening to try and pinpoint the issue?

---

### Post by Oddbrid on 2012-11-10
Have you tried to mount particular device through the console?!

#sudo mount /dev/sdX

---

### Post by Merrattic on 2012-11-10
As a workround try **Airdroid**, a phone app that you access from your PC and transfer files and allsorts :)

---

### Post by wingrider78 on 2012-11-11
> **Oddbrid said:**
> Have you tried to mount particular device through the console?!

#sudo mount /dev/sdX

After trying 'sudo mount /dev/sde' I get this

mount: can't find /dev/sde in /etc/fstab or /etc/mtab

but just double clicking the icon that shows up on my desktop will mount the drive and open it up.  The problem lies when trying to access the files.  Thats when the drive unmounts itself.

---

### Post by wingrider78 on 2012-11-11
> **Merrattic said:**
> As a workround try **Airdroid**, a phone app that you access from your PC and transfer files and allsorts :)

I will look into it, thanks.  It has been a pain to take my sdcard out everyday to access the files...

---

