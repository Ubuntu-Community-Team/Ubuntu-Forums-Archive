---
title: "[SOLVED] Mount windows USB drive in ubuntu 8.04"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-10
Question - how can I or should I say can I access a USB drive that I had under windows.  Now that I am running ubuntu?  ie. I think the drive format is NTFS - This is a big I think.  

I have files on this drive that I would really like to get to and when I try to mount it in ubuntu it wont mount :(  

Is there anything I can do ??  Any ideas would be a big help please :)


~Dan

---

### Post by TeoBigusGeekus on 2008-05-10
Doesn't it show up in your /media folder?

---

### Post by bumanie on 2008-05-10
Are you getting any error messages? If so please post the error message. Usb devices should automount under ubuntu. Ubuntu 7.10 and 8.04 can read/write to ntfs so the file format is not a problem.

---

### Post by hufferd on 2008-05-10
HEre is the screen shot





That is to say this is the error message I am getting when trying to mount the old USB windows drive

---

### Post by bumanie on 2008-05-10
That is advising you do a chkdsk under windows to check the file system. Follow the instructions. It could also be that the device is faulty, but if it works in windows ,this is unlikely. If it works under windows and you can read/write to it, it may be an idea to copy the files off and reformat it.

---

### Post by hufferd on 2008-05-10
> **bumanie said:**
> That is advising you do a chkdsk under windows to check the file system. Follow the instructions. It could also be that the device is faulty, but if it works in windows ,this is unlikely. If it works under windows and you can read/write to it, it may be an idea to copy the files off and reformat it.

Thanks for the info 

~Dan

---

### Post by hufferd on 2008-05-10
YAY! an update to my question.....  I took the USB drive to a windows machine to copy all data onto CD's about 400mb I would say. (mostly music)

Anyway made copies of the info I wanted and came back to ubuntu machine hooked up the USB drive to the ubuntu machine and bam it found it that time.  ?? Go figure so now atleast I have back up copies of all the info on that drive

---

