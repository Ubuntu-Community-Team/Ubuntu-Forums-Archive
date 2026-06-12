---
title: "Symbolic Links - Broken on restart"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by james139 on 2015-06-01
I've created a couple of links on my Ubuntu desktop to my windows partition to access My Documents etc. instead of having to click through to them, but when I restart the system, the links always appear broken. I first though that it was because the Windows drive wasn't automatically mounted on start-up. I clicked the drive to access it via the Unity side panel which works, but the link is still broken. The filepath is exactly the same. I don&#8217;t know why it's not working and it's  annoying me!

I tried a link to /etc on the same drive as ubuntu and that is fine.

The method I used was to cd to Desktop and then: ln -s /filepath/to/thewindows/folders/iwant

---

### Post by dino99 on 2015-06-01
go for sharing folders/files  [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by leunam12 on 2015-06-01
I would mount the drive automatically via fstab. make sure that you have ntfs-3g first

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by sean93 on 2015-06-01
Odd, I have experienced the same issue.

---

### Post by mcduck on 2015-06-01
> **james139 said:**
> I've created a couple of links on my Ubuntu desktop to my windows partition to access My Documents etc. instead of having to click through to them, but when I restart the system, the links always appear broken. I first though that it was because the Windows drive wasn't automatically mounted on start-up. I clicked the drive to access it via the Unity side panel which works, but the link is still broken. The filepath is exactly the same. I don’t know why it's not working and it's  annoying me!

I tried a link to /etc on the same drive as ubuntu and that is fine.

The method I used was to cd to Desktop and then: ln -s /filepath/to/thewindows/folders/iwant

That is exactly because the drive ins't mounted on startup. ;)

If a drive isn't configured in */etc/fstab*, it will apppear in your file manager's side panel and is then mounted as soon as you try to access it. (Same system that's used for removable drives, optical media etc).

To actually have the drive mounted in startup (and the symlinks to work straight away as well) you need to add it to fstab.

---

### Post by james139 on 2015-06-03
> **leunam12 said:**
> I would mount the drive automatically via fstab. make sure that you have ntfs-3g first

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Brilliant, thanks. Followed the above link from Manual Configuration onwards and it's worked first time.

---

### Post by leunam12 on 2015-06-03
You are welcome, I'm glad it helped. Please mark the thread as solved.

---

