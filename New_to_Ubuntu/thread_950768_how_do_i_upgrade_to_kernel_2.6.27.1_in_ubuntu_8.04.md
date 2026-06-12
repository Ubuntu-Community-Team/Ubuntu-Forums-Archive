---
title: "how do i upgrade to kernel 2.6.27.1 in ubuntu 8.04?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by opendevlite on 2008-10-17
is this possible?

i was just wondering how to do this?

does ubuntu 8.04 recieve updates for upgrading the kernel if i don't upgrade to 8.10?

---

### Post by Tom--d on 2008-10-17
> **opendevlite said:**
> is this possible?

i was just wondering how to do this?

does ubuntu 8.04 recieve updates for upgrading the kernel if i don't upgrade to 8.10?

Ubuntu 8.04 has the Kernel 2.6.24
Ubuntu 8.01 has the Kernel 2.6.27 and will receive updates for that kernel when new ones (of that version) is released.

So, yes, In Ubuntu 8.10 you will get the kernel 2.6.27.1 (If it hasn't updated it yet).


You can of course, compile the kernel and use it.

---

### Post by opendevlite on 2008-10-17
@Tom--d how do i upgrade to kernel 2.6.27.1 in ubuntu 8.04?

---

### Post by Tom--d on 2008-10-17
> **opendevlite said:**
> @Tom--d how do i upgrade to kernel 2.6.27.1 in ubuntu 8.04?

Read mail :)

and, 

[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) GUI for compilation :)

---

### Post by icanfly0307 on 2008-10-17
Hi, 
      You could try to upgrade the kernel by using the system update feature. However, I'm not sure if it will bring you the specific kernel that you want (2.6.27). Another alternative, as Tom said, is to compile the kernel from source. This is a pretty straight forward process and there are tons of guides on the web on how to do this. First of course, you need to download the source from [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/). Download the 2.6.27.1 kernel in the tar.bz2 format. Unzip it into a directory of your choice and then follow the instructions in this guide.

[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)

And don't worry. Even if something goes wrong, you will still be able to boot into your original kernel that shipped with the default Ubuntu 8.04. Good 
Luck!

PS: Don't forget to compile the ext3 filesystem support *directly* into the kernel and NOT as a module. Forgetting this step would result in a waste of time and you would need to compile the kernel all over again.

---

### Post by iponeverything on 2008-10-17
This kernel worked fine for me a while back.. Your mileage  may vary.

```
wget http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb
```

```
sudo dpkg -i linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb

```

---

### Post by opendevlite on 2008-10-18
> ```
wget http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb
```

is this kernel a release candidate or the stable version?

---

### Post by Nepherte on 2008-10-18
rc stands for release candidate. So no, it's not a stable version. Why would you need the latest kernel anyway? Is there some feature you need from it?

---

### Post by opendevlite on 2008-10-18
i just wanted to have the latest kernel thats all

---

### Post by opendevlite on 2008-10-20
bump

---

### Post by AndyCooll on 2008-10-20
Have a read of this: [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158")

:cool:

---

### Post by eldragon on 2008-10-20
i wouldnt replace the kernel just for the sake of it.

if the computer works ok with the default kernel, there is no reason to go breaking things up (unless you really really want to spend a couple of hours compiling, and another couple of days debugging)...

---

### Post by billgoldberg on 2008-10-20
I agree with the above poster.

If the kernel is working, keep it.

I wouldn't recommend compiling your own kernel. If you want you can do so, but if you really want te .27 kernel, upgrade to Ubuntu 8.10 beta.

---

### Post by Archmage on 2008-10-20
> **opendevlite said:**
> i just wanted to have the latest kernel thats all

You know that this will be round about 8 hours work for the first time, it may break a lot and make your whole system instable?

If you want an instable system, than try the Beta of 8.10, although this may be more stable than it would be, if you install the latest kernel in a system that isn't build for it.

Wait one month, than you can install the 9.04. That will be in the beginning as instable as Hardy would be with the latest Kernel.

---

### Post by icanfly0307 on 2008-10-20
Did you try my method of compiling the kernel on your own? Remember, this is probably one of the best ways because you will be able to customize it to your own needs.

---

### Post by enigma101 on 2008-10-29
Hi, I do have a reason to install the new kernel.  I can't use DMA with the current kernel for 8.04 and if I upgrade to 8.10 then I loose 3d acceleration because I have a Gforce4 Ti.  So, I installed that posted deb but, now I need to install the headers, and when I do so, it complains of dependencies, which strangely enough are itself.  :confused:  HELP!

---

