---
title: "Hwving problems with the disk partitioner."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Puroch on 2008-11-07
I've been trying to install Ubuntu 8.1 on my older HP, and I've been getting errors from the disk partitioner during install.  Does anyone know a way around this or have encountered this problem and found a way around it.

---

### Post by Yuki_Nagato on 2008-11-07
Are you dual booting or installing a total-Linux machine?

If you are dual-booting, can you report back any errors or output that might have cropped up, or any other details we might want?

If you are just doing a Linux install, first try DBANing the computer.  

[http://www.dban.org/]("http://www.dban.org/")

Running this and then typing in the option "quick" will completely wipe your computer.  Everything.  (Good for when the Feds are knocking on your door.)  Then you run the installation again, and see if the partition is still having problems.

Did you run a md5 or sh1 check on the Ubuntu ISO?

---

### Post by Puroch on 2008-11-07
I don't know what md5 or sh1 is, so I have not tried that, but I am trying to run a complete Linux machine.  I will try dban, and get back to you all.  Thanks.

---

### Post by oldos2er on 2008-11-07
> **Puroch said:**
> I've been trying to install Ubuntu 8.1 on my older HP, and I've been getting errors from the disk partitioner during install.  Does anyone know a way around this or have encountered this problem and found a way around it.

 What are the errors?

---

### Post by Puroch on 2008-11-07
It says the disk partitioner failed.

---

### Post by Yuki_Nagato on 2008-11-07
The partitioner should be able to eat hard disks alive, so I am guessing that there is a problem with the install media.  You will need to redownload the ISO file, and then run it through a md5 program, and then compare the hash value it spits out with the one provided on the website.

[http://www.blisstonia.com/software/WinMD5/]("http://www.blisstonia.com/software/WinMD5/")

This will allow you to check md5 hashes on Windows.

More info from Wikipedia: [http://en.wikipedia.org/wiki/Md5]("http://en.wikipedia.org/wiki/Md5")

---

### Post by Puroch on 2008-11-08
Ok, I got it installed correctly, the DBAN worked.

---

### Post by hyper_ch on 2008-11-08
if your thread is solved, please use the "Solved" item from the "Thread Tools" on top :)

---

