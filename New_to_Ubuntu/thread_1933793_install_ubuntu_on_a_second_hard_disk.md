---
title: "install ubuntu on a second hard disk"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by gilatino on 2012-03-01
I tried to install ubuntu by a USB on a second hard disk but it doesn't recognize it. It only shows /dev/sda and its partitions.

[IMG]http://i41.tinypic.com/260esle.jpg[/IMG]

---

### Post by HeroOfCanton on 2012-03-01
Windows can't see linux, but linux can see windows partitions/drives. If you boot to a live cd you will be able to see the linux drive.

---

### Post by gilatino on 2012-03-01
> **HeroOfCanton said:**
> Windows can't see linux, but linux can see windows partitions/drives. If you boot to a live cd you will be able to see the linux drive.

I haven't installed ubuntu. I try to install it on Disk 0 which is showing as unallocated space in win7. The problem is when I reach the manual partitioning screen in ubuntu installation, it only shows one hard disk which is Disk 1 and its partitions.

---

### Post by HeroOfCanton on 2012-03-01
> **gilatino said:**
> I haven't installed ubuntu. I try to install it on Disk 0 which is showing as unallocated space in win7. The problem is when I reach the manual partitioning screen in ubuntu installation, it only shows one hard disk which is Disk 1 and its partitions.

Sorry, misunderstood your post. Since that was a windows screenshot I just assumed. We all know what that does... ;)

First recommendation is to make sure the windows is on the first HDD (for windows sake). Probably want to check the numbering on your motherboard and make sure the windows drive is on a lower numbered port.

I do remember having something similar happen to me way back when. This was probably Win95 or 3.1 and linux together so it may not work today, but what I did was create a basic partition in Windows (okay, technically DOS) then boot the linux install disk. No need for a format, just created the file structure. When I tried again the disk showed up. Worked more than 15 years ago, so it may be worth a shot today. :P

---

### Post by gilatino on 2012-03-03
> **HeroOfCanton said:**
> Sorry, misunderstood your post. Since that was a windows screenshot I just assumed. We all know what that does... ;)

First recommendation is to make sure the windows is on the first HDD (for windows sake). Probably want to check the numbering on your motherboard and make sure the windows drive is on a lower numbered port.

I do remember having something similar happen to me way back when. This was probably Win95 or 3.1 and linux together so it may not work today, but what I did was create a basic partition in Windows (okay, technically DOS) then boot the linux install disk. No need for a format, just created the file structure. When I tried again the disk showed up. Worked more than 15 years ago, so it may be worth a shot today. :P

Thanks for your help, I managed to install Ubuntu on the second drive.

---

### Post by HeroOfCanton on 2012-03-04
> **gilatino said:**
> Thanks for your help, I managed to install Ubuntu on the second drive.

Glad I could help. Don't forget to mark the thread as solved in Thread Tools.

---

### Post by NikTh on 2012-03-04
> **gilatino said:**
> I tried to install ubuntu by a USB on a second hard disk but it doesn't recognize it. It only shows /dev/sda and its partitions.

That is weird. I remember that to all my installations of ubuntu , was recognized the unallocated space  as free space , at the partitioning stage.

---

