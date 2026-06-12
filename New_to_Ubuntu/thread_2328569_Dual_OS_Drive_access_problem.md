---
title: "Dual OS Drive access problem"
date: 2016-06-22
forum: New to Ubuntu
---

### Post by ksd2 on 2016-06-22
Hi.
I have installed both windows and ubuntu on my laptop, windows coming inbuilt. When I installed ubuntu I might have not checked some option and hence I might be facing this trouble. I can access only the OS drive in ubuntu and not my other drives which i created in windows. There is a lot of movies in thos drives and I want to be able to access them in ubuntu too. Pleas help.

Thanks in advance.

---

### Post by yancek on 2016-06-22
Windows 10 pre-installed is almost always installed UEFI.  Did you install Ubuntu in UEFI mode?

When you say 'drives' do you mean partitions or do you mean physical hard drives?  In Ubuntu if you are using the default Unity Desktop, you should see hard drive icons in the left panel where you can access other non-system drives/partitions.  You can also go to the /media/user directory and access them by UUID.  Have you tried that?  If you don't know if you installed Ubuntu UEFI, go to the site below and get the boot repair software and download and run it in Ubuntu.  Select the option to Create BootInfo Summary and post a link to the output here.  Do not try to make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2016-06-22
Please explain what you mean by only being able to access the OS drive and not the other drives. How do you try to access those other drives? Do you get an error message?

Windows 8 and later gives a fast loading time by hibernating instead of shutting down completely. When Windows is hibernated then Windows partitions cannot be accessed in Ubuntu. We get a message saying that the partition is in an unsafe state. Is this what you are seeing?

Regards.

---

### Post by ksd2 on 2016-06-23
Hey guys thanks for the replies.
I am sorry I am noob and hence could not make it clear to you the problem I am facing.
So I see the options of various drives (4) on the panel left of the screen. While one of it says OS and I can open it, the others say New Volume. I suppose these are the partitions (what I meant by drives, again sorry) I created in Windows. So till yesterday when I clicked on them it said invalid path. But today, I can access them. I dont know why. I just ran the software auto update and nothing else. Confused. But as of now I can access the partitions.
Just so that I understand it, is it possible for me to log out from Windows, Boot up again and log into ubuntu and access the partitions I created in Windows ?
Thank you guys.

---

### Post by yancek on 2016-06-23
> Just so that I understand it, is it possible for me to log out from  Windows, Boot up again and log into ubuntu and access the partitions I  created in Windows ?

Yes, maybe.  If this was a new install, you may not have had the software needed to read/write to windows installed and the update installed it, not really sure what else it might have been.  You should be able to read/write to windows partitions but do not write to any system files, just data.  One exception it that windows 8 and newer version default to always on hibernation to make it appear that your windows system is booting faster.  If you leave windows hibernated, you will NOT be able to mount to access your windows partitions from Ubuntu as there is too much potential for harm.  Of course, you will not be able to access the Linux from windows with a default install.

---

### Post by sheng.lao on 2016-06-23
usualy, I will disable the Secure boot in BIOS and then install Win10 and Ubuntu

---

### Post by ksd2 on 2016-06-24
Thanks Yaneck :)
I did run the update and that might have solved the problem.

---

### Post by ksd2 on 2016-06-24
> **sheng.lao said:**
> usualy, I will disable the Secure boot in BIOS and then install Win10 and Ubuntu
I think I am not yet capable of trying something like that on my own :P
But thanks, will look into it :)

---

