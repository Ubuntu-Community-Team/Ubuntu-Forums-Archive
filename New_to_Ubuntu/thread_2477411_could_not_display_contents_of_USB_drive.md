---
title: "could not display contents of USB drive"
date: 2022-07-24
forum: New to Ubuntu
---

### Post by billy3xs on 2022-07-24
"Could not display all the contents of USB: Error when
getting information for file "/media/me/tyson/NVIDIA_SHIELD':
Input/output error"

In Files /media/me/tyson shows up, but won't display contents.
So I have three other USB drives that are ok, I went back to the Nvidia Shield and the drive is ok and I closed everything carefully.
I tried Win 10, but I didn't see any way to eject or unmount the drive, so I just shut down windows. 
ReadyBoost is turned off. It might have been scanned for errors in win 10. 
It's exFAT. A Crucial 2T and my current fav!

So I went back to windows and put NVIDIA-SHIELD  in the $recycle.bin, in the USB. Then it opened in Ubuntu.
But when tried Nvidia Shield again it worked, but again it doesn't work in Ubuntu. Same error.
I imagine Nvidia created another NVIDIA_SHIELD folder. And in all USBs the folder is empty!

This is a reinstall of 20.04, it worked really nice, deleting old partitions, etc.
Laptop i5 intel 64 bit

---

### Post by ActionParsnip on 2022-07-24
Before you physically unplug the device do you use the safe remove feature in the OS or do you just yank it out?
Sounds like an NTFS based storage so I suggest running a full chkdsk in Windows to make sure the file system is healthy and consistent.

---

### Post by grannysmith on 2022-07-24
In windows I haven't seen "safe to unplug" in a long time, maybe my PC is too slow.
The USB is formatted exFAT.
I could run a chkdsk in windows, each time it sez it might be corrupt it checks forever and comes up with nothing.
Also as I said, the other USBs do not have this problem. And they have the Nvidia folder.
It's interesting that folder is called "System Volume Information" in Ubuntu. But not in my problem USB.
Sorry for the long delay, now I can't figure out my Login Keyring password.

---

### Post by ActionParsnip on 2022-07-24
Safe unplug is in the system tray near the time. Right click the USB stick icon then safe remove the device. Wait for the OS to say it can now be removed
This is the icon
[https://i.ytimg.com/vi/dwcdJ91Vq2s/maxresdefault.jpg](https://i.ytimg.com/vi/dwcdJ91Vq2s/maxresdefault.jpg)

---

### Post by grannysmith on 2022-07-24
Well thank you, I'll look for it! I think Ubuntu's unmount is easier to find...

---

### Post by ActionParsnip on 2022-07-24
Can be. If you know where to look. I use sync, umount, eject personally as I use CLI more than anything else

---

### Post by billy3xs on 2022-07-25
Oh, in Ubuntu after using the USB SSD in Nvidia Shield, the drive was not viewable, so I clicked unmount. 
But then I thought what if I mount it again and it worked!

So, could still be mindful of ejecting in Windows and thankyou sooo much.
Personally I shudder each time I have to use the CMD line!   LOL

Edit:  Nope it didn't work, back to the salt mines!

Edit: Son of gun! I found the USB icon and eject button!  It was in show hidden icons.
Ok, that still didn't work. Next I'll delete the Nvidia folder with windows.
So that worked, and found the eject stuff. I don't see why eject isn't in the Rt Clk menu in File Explorer anymore?

I need to learn about Virtual Machines now so I can load windows to access this SSD. 
I don't really want to have to fire up another PC just for this.

---

### Post by ActionParsnip on 2022-07-25
It's important to use. It sysncs the file system so that nothing is in cache then kicks the disk from the OS. NTFS is a proprietary file system to Microsoft. The NTFS access you enjoy is a best effort attempt. If the file system isn't pristine then you can expect issues.
This is why it is the first thing I ask.
Glad you got sorted

---

