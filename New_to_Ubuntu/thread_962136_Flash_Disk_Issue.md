---
title: "Flash Disk Issue"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by kartunista on 2008-10-28
I am new to Ubuntu.

I have some files from my flashdisk that i intended to post on my blg.  However, upon putting the FD into its USB socket, nothing happened.

No new window opened, no notification whatsoever telling me that the system recognized a new hardware.

I checked the Places and theres no FD there.

What should I do?

---

### Post by lhb1142 on 2008-10-29
First, reinsert your flash drive. Then go to "Places" and then to "Computer." With luck, you will see your flash drive there. You should also see it on your desktop.

If you still do not, and you had previously used it on a Windows computer, replace it in that Windows computer and properly uninstall it. Then try it again in your Ubuntu machine. That should do the trick.

This happened to me with an external hard drive that I had merely shut off when using it with Windows rather than uninstalling it first. It would not work with Ubuntu until I had reattached it to a Windows computer and properly uninstalled it before shutting off its power.

I hope this helps you.  :lolflag:

---

### Post by j.miller565 on 2008-10-29
hmm maybe the flash drive is connected but not showing up. It has happened to me once or twice and had to mount it manually.

um how can you try  
> sudo fdsk -l
in the terminal and paste the output in a new post?

---

### Post by kartunista on 2008-10-29
> **lhb1142 said:**
> First, reinsert your flash drive. Then go to "Places" and then to "Computer." With luck, you will see your flash drive there. You should also see it on your desktop.

If you still do not, and you had previously used it on a Windows computer, replace it in that Windows computer and properly uninstall it. Then try it again in your Ubuntu machine. That should do the trick.

This happened to me with an external hard drive that I had merely shut off when using it with Windows rather than uninstalling it first. It would not work with Ubuntu until I had reattached it to a Windows computer and properly uninstalled it before shutting off its power.

I hope this helps you.  :lolflag:

Thanks man.  I will try this.  But i have to ask first, does doing it means that the same might happen when i mount the said FD to a Windows operated PC?

We dont have any public internet cafe here using Linux as their OS.

---

### Post by kartunista on 2008-10-29
> **j.miller565 said:**
> hmm maybe the flash drive is connected but not showing up. It has happened to me once or twice and had to mount it manually.

um how can you try  

in the terminal and paste the output in a new post?

Thanks bro.  But pasting the output in a new post? I dont understand, bro:confused:.

---

### Post by au_vagabond on 2008-10-29
What brand of disk do you use?!?

If you are using those irritating cruzer ones, or any other annoying brand with it's own little UI, try moving all of your files across to your windows hd. After this open diskmgmt (just go, run -> diskmgmt, still in windows), and format the pen-drive to fat 32. Then, move all your files back, and it should work as an external drive in both *nix and windows. 

Huzzah!

Remember, only copy the docs and stuff you need off of the usb - not the annoying software etc.

Good luck ;)

---

### Post by kartunista on 2008-10-29
> **au_vagabond said:**
> What brand of disk do you use?!?

If you are using those irritating cruzer ones, or any other annoying brand with it's own little UI, try moving all of your files across to your windows hd. After this open diskmgmt (just go, run -> diskmgmt, still in windows), and format the pen-drive to fat 32. Then, move all your files back, and it should work as an external drive in both *nix and windows. 

Huzzah!

Remember, only copy the docs and stuff you need off of the usb - not the annoying software etc.

Good luck ;)

Im using Kingston. Fat 32 then. Thanks a lot!

---

### Post by kansasnoob on 2008-10-29
Simply installing either pmount or usbmount makes all of my thumb drives auto mount. They're both in synaptic. I prefer pmount which depends on hal.

NOTE: don't install both usbmount and pmount!

Synaptic explains the difference thus:

> USBmount is intended as a lightweight solution which is independent of
a desktop environment. Users which would like an icon to appear when an
USB device is plugged in should use the pmount and hal packages
instead.

So you can either install from synaptic or:

```
sudo apt-get install pmount
```

hal should already be installed by default.

---

### Post by lhb1142 on 2008-10-29
> **kartunista said:**
> Thanks man.  I will try this.  But i have to ask first, does doing it means that the same might happen when i mount the said FD to a Windows operated PC?

We dont have any public internet cafe here using Linux as their OS.
Windows is somewhat more tolerant of incorrect disconnection of external drives than is Ubuntu Linux. Once the drive is correctly disconnected from a Windows computer, it should work normally on any computer running any operating system. In the future, do make sure that you always unmount this flash drive and all other external drives correctly.

---

