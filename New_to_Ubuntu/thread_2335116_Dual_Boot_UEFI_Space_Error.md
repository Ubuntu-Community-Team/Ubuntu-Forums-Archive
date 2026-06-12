---
title: "Dual Boot UEFI Space Error"
date: 2016-08-25
forum: New to Ubuntu
---

### Post by idaniel2 on 2016-08-25
Hello,

I tried to install in dual boot with Windows 10 with USB installer UEFI. After the step where I choose language and connect wifi, I receive the error: Not enough space. It is telling that I need at least 8.5GB and I have only 3Gb free.
I think it is a problem with the installation place. I don't want to install on USB drive. I have created a partition with 40GB.
Could you help me and tell me what to do?
Thank you. Sorry, I am beginner in Linux.
Cheers.

---

### Post by idaniel2 on 2016-08-25
I add the mention that I use Laptop Dell E7450, SSD 512Gb, RAM 16Gb.

---

### Post by oldfred on 2016-08-25
Are you using the Something Else install option?

Did you leave Windows fast start or its always on hibernation on? Then installer may not see SSD to install into.

Post this from live installer's terminal (if sda is SSD):
       sudo parted /dev/sda unit s print 
    
See also link in my signature below (it is a lot of info).

---

### Post by leunam12 on 2016-08-25
Shutdown windows from the terminal. Press the Windows key and type cmd, then type this on the terminal ```
shutdown -s -t 00
``` and press enter. Then start Ubuntu from the USB stick and you will be able to install to your ssd. Choose "Something else", select your 40GB partition on the next screen and click "change". on the window that will open pick the type of partition that you want (ext4); put a check mark next to "format" and the mount point "/". After installation you may have to boot from USB again and run boot-repair.

---

