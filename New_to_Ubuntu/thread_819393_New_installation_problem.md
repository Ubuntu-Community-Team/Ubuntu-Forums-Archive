---
title: "New installation problem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by parkinrg on 2008-06-05
Hi , 
I am completley new to Ubuntu and have recently installed Ubuntu inside windows , so I get a choice of windows or Ubuntu on start up. The first time I choose Ubuntu it loads up OK and works fine, but when I restart the computer and choose Ubuntu I get a text screen with the following text
"Busybox V1.1.3 ( Debian 1.1.1.3-5ubuntu12)
(initramfs)"

Does anyone know what the problem is

---

### Post by MDSmith2 on 2008-06-05
1. edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "debug" (without quotes)
3. reboot
4, at the command line type "cat /tmp/initramfs.debug" <enter> (without quotes)
5. there should be an error in the latest few lines, post it here.

---

### Post by parkinrg on 2008-06-05
Thanks for the reply 
I edited that file and saved it , rebooted the PC then started up Ubuntu which gave me the Busybox screen again , put in           cat /tmp/initramfs.debug, and the replay was  "No such file or directory" I have checked the file again , it definitley has "debug" were "quiet splash" used to be  .
Am I doing something wrong ?

---

### Post by bikinguy77388 on 2008-06-05
Hi,

I am a newbie and the same happened to me.

I sloved it maybe not as elegant as some but when you are booting after selecting ubuntu...when it says you have so many seconds to hit Esc key..do it. They select a different kernel. I have kernels that end in 18..17 and 16.

If I select the newer kernels 17 or 18 I get the same as you.
I select the oldest 16 and it boots fine.

Hope this helps

bikinguy

---

### Post by parkinrg on 2008-06-05
Thanks Bikinguy , Selecting a different kernel works !
Maybe if I decide to ditch Windows completely and do a full install that problem will disappear

---

### Post by MDSmith2 on 2008-06-05
> **parkinrg said:**
> Thanks Bikinguy , Selecting a different kernel works !
Maybe if I decide to ditch Windows completely and do a full install that problem will disappear
That might work but you should make sure you don't need windows any more because of the genuine advantage thing.
When this thread is solved please mark it as so using the Thread Tools at the top rihgt corner of the thread.

---

### Post by bikinguy77388 on 2008-06-05
Parkinrg,

I would hold off and use ubuntu awhile and make very sure you won't miss windows.
Glad it worked.

bikinguy

---

