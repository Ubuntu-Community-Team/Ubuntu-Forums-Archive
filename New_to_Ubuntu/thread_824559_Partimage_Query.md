---
title: "Partimage Query"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-06-10
I have just tried Partimage and got an error message saying that I must "umount" my partition before it can proceed . I am a bit wary of this as I am not sure what it does , or how to do it . Can this procedure be reversed?
Also if I do succeed in making an image what burning program do I use to put it on disk ?

---

### Post by drs305 on 2008-06-10
What it is telling you is that it can't perform actions on a partition that is in use. Unmounting a partition does no damage to your system. Unfortunately, many times the partition you want to work on is the partition on which your system is running. In that case, it is impossible to unmount it without exiting the system.

To work on a system partition, you normally would boot from a systemrescuecd or livecd and make sure the partition is unmounted before continuing. I personally like the systemrescuecd for using partimage.
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by ex-wirecutter on 2008-06-10
Thanks for your suggestion , I tried the link to system rescue and followed the instruction for w-get , but dont know what to put next , so it didnt work.

---

### Post by drs305 on 2008-06-10
> **ex-wirecutter said:**
> Thanks for your suggestion , I tried the link to system rescue and followed the instruction for w-get , but dont know what to put next , so it didnt work.

Ok, just go to this link and select **download** from the left side.
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Then select **download now** from the middle section (i486),  and then the **systemrescuecd-x86-1.0.3.iso** and it should just download. Burn that _image_ to a cd. If you use nautilus, I believe you can just right click and select 'write to cd' to get the .iso image copied.

By the way, here is an excellent HOWTO on using partimage:
[Howto: Backup with Partimage]("http://ubuntuforums.org/showthread.php?t=287522")

Sorry, I couldn't post the images.

---

### Post by ex-wirecutter on 2008-06-10
Thanks for that , I now have systemrescuecd X86 1.0.3 .iso , All I need is to burn it to CD. I suppose I could copy it to a usb flash drive then transfer it to Windows and use an ISO burner I have on that . Unless there is a better way .

---

### Post by drs305 on 2008-06-10
I was editing my previous post when you replied. Use nautilus, right click and you should get a 'write to disk' option. That's the easiest way to do it. If I have to use an app, I use k3b - it's in the repos.

---

### Post by ex-wirecutter on 2008-06-10
Thanks again , particularly for staying with this newcomer , I will select a burning program and give it a go .
Once again thanks for the help .

---

