---
title: "Dual boot no longer"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by nickelbox on 2012-10-06
I had a dual boot system running Windows 7 and Ubuntu 12.04 for almost 6 months with no issue. This morning, performed updates like I always have and now when I boot, it only boots to Ubuntu. Any help please!

Thanks

---

### Post by oldfred on 2012-10-06
First try 

```
sudo update-grub
```

And if that does not work post link to run of BootInfo:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by jingaling on 2012-10-06
What he said ^^^^^

---

### Post by Johnyburd on 2012-10-06
When I boot my dual booted computer it shows a purple screen that lists all my bootable partitions.  I have to select one or it'll automatically boot ubuntu.

---

### Post by nickelbox on 2012-10-06
Update didn't work.

Should I attempt to repair or simply create a Bootinfo summary and post it here first?

---

### Post by oldfred on 2012-10-06
Boot-Repair is pretty good, but sometimes you need to change some settings to have it do the best corrections.

Post BootInfo link.

---

### Post by nickelbox on 2012-10-06
[http://paste.debian.net/197121/](http://paste.debian.net/197121/)

---

### Post by oldfred on 2012-10-06
Boot script looks normal. And Windows files all seem to be in correct locations.

Boot repair will only fix grub & Linux boot issues. It cannot fix Broken Windows unless it just is a missing Windows entry in grub's menu.

Have you tried both Windows entries. They both look like they should work.

If you press f8 as soon as you press the entry for sda1 (you have to be quick) do you get into a Windows repair console. Or do you have a Windows repairCD or USB?

---

### Post by nickelbox on 2012-10-07
My system used to boot to grub and from there I selected either Windows or Ubuntu. 

Haven't tried anything other than what's in this thread.

---

### Post by nickelbox on 2012-10-07
I decided to go ahead and run boot repair and it seemed to fix the issue with grub. I now just have to fix the delay so it bounces to windows boot manager, giving me just the two options I used to have previous.

Here's my log
[http://paste.debian.net/197239/](http://paste.debian.net/197239/)

---

