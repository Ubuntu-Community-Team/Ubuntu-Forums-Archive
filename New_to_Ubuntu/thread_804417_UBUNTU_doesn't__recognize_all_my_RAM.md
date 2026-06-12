---
title: "UBUNTU doesn't  recognize all my RAM"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by rafelprohens on 2008-05-23
Hi, I have a problem with my RAM memory:

I have UBUNTU 7.10
I have just installed RAM: 4 x TRANSCEND 2 GB PC800 =  8 GB (total)

but when I ask for the ammount of it we get: free -m

            total       used       free     shared    buffers     cached
Mem:          3290       1187       2103          0        101        828
-/+ buffers/cache:        257       3033
Swap:         1953          0       1953

even, if I ask:  top

top - 09:21:00 up  1:02,  1 user,  load average: 0.01, 0.03, 0.07
Tasks: 125 total,   1 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  0.0%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3369808k total,  1201880k used,  2167928k free,   102516k buffers
Swap:  2000084k total,        0k used,  2000084k free,   842460k cached

I have seen the BIOS and there appear the total 8 Gb of RAM.

Could You help me?
Plaese!

Many thanks in advantge

Rafel

---

### Post by Technoviking on 2008-05-23
You will need to install the 64bit version of Ubuntu to see more than 4GB of ram.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Joeb454 on 2008-05-23
Mike's right, a common limitation of 32 bit systems is that you can only use up to 4GB RAM (sure you can have more but it's pretty pointless unless you want to compile a custom kernel ;))

If you want to upgrade to 64 bit, you shouldn't have any issues (I don't :))

---

### Post by Trebaruna on 2008-05-23
I understand that the Server kernel of the 32bit edition has its PAE flag enabled. This means that it is able to address upto 64GB of RAM.
The disadvantage, of course, is that you'll need to install a graphical system and any other applications (e.g. OpenOffice) yourself.

This is just to point out you do not /have/ to get 64bit. Having said that, I'm using 64bit and have for some time now. There are fewer and fewer problems with it. In fact, I can now do everything either without any extra effort, or with a minimum of additional steps.

---

### Post by hyper_ch on 2008-05-23
You could also recompile the server with PAE or you could install the server-kernel....

---

### Post by barnex on 2008-05-23
This is easy to fix, I've had the same problem on my 8GB machine. You do indeed need to use a server kernel, install it with: ```
sudo aptitude install linux-server
``` Then reboot your machine. There is a possibility that you may have to choose the new kernel in the GRUB boot menu.

---

### Post by rafelprohens on 2008-05-23
Many thanks to all of You.

Your responses have been fas,  useful, clear and understandable.

The only pity think is that I am new in the Linux world
and, hence, I am afraid to follow Your suggestions.
Probabiliy, I was wrong when I bought so much RAM.
But I still thinking that Linux is our wolrd

In any case, I sincerely would give You, Thanks.

---

### Post by hyper_ch on 2008-05-23
recompiling the kernel shouldn't be *that* difficult. Basically you take all the settings you have now and just enable PAE. There's a howto I have wanted to try for a long time, haven't done yet so:  [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Otherwise do as barnex says. That will install the server kernel which has PAE already enabled. However the server kernel is more streamlined towards a headless server and not a desktop machine. There are some differences but I don't know all of them.

---

### Post by rafelprohens on 2008-05-23
Hi hyper_ch,

I'll try do it and I'll post the experience.
Thanks

Rafel

---

### Post by hyper_ch on 2008-05-23
if you have questions, just ask ;)

Btw, when you do install linux-server you need then to boot into the server kernel. At bootup you should have two new entries... if you want to boot by default the server kernel then you can alter it in the grub menu.lst file:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksu gedit /boot/grub/menu.lst

```

---

### Post by Efros on 2008-05-23
Seriously go for it, I have installed the 64bit version on several machines running C2D processors and AMD dual cores with very few problems. I would recommend the alternate disk though, I had a few issues with the live cd.

---

