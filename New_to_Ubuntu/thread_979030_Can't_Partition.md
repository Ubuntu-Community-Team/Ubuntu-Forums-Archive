---
title: "Can't Partition"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by talguy on 2008-11-11
I have used linux (fedora) before for my basic c++ programming course but other than that not really.  For my senior engineering design project my group members would like to base our application off of Linux.  for this reason I need to install a version of linux onto my computer where i will be dual booting w/ XP.  I have partition magic and was recently trying to resize my NTFS partition to give ubuntu 10GB.  When the partitioner was running it gave me this error
> 
Error #1642
Index sequence number mismatch, File 24961 (144)

Does anyone know what is causing this error.  I have defraged my hard drive a couple of times so I really don't think it would be that.

---

### Post by Pro-reason on 2008-11-11
That's really a Windows problem and a Partition Magic problem.  This is a Linux forum!

You could run CHKDSK on the drive in question.

I don't know what else to suggest, apart from trying GParted in Ubuntu.

---

### Post by talguy on 2008-11-11
I'll try that.

I know this is a linux forum, I just figured that everyone in this section of the forum are tryign to install the OS and are partitioning their HDD and might run into this problem.

---

### Post by dsurge on 2008-11-11
You dont need to do that. The ubuntu live cd auto partitions for you. Pop it in and start the install, it'll ask how you want to split up your drive:)

---

### Post by talguy on 2008-11-11
it will even if my NTFS partition uses my whole HDD.  I tried to do that before and I didn't see that options also

---

### Post by dsurge on 2008-11-11
Yep. there are a few options when it comes to the partition editor screen. Use the guided resize, it should pop up with a bar on your screen. Drag the ubuntu partition to 10gb, click next.

---

### Post by talguy on 2008-11-15
ok so i finally have gotten some free time to try and install ubuntu on to my computer and when I get to the partitioning page I have found that i do not get the guided partitioning option to come up.  does anyone know why this is happening

---

