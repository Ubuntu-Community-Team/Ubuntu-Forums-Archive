---
title: "[SOLVED] Setting up SUM- Startup Manager"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Sherina on 2008-06-22
Today I downgraded from Hardy Heron to Gusty Gibbon on my laptop and I recently installed SUM-Startup Manager to shorten my boot time. However it is not working. I have installed it before but I can't find the thread that help me configure it last time. Can someone help me?

Thanks

---

### Post by iaculallad on 2008-06-22
You can manually change the your Ubuntu's boot-time (when you're speaking of the default 3 seconds delay: timeout=3)

```
gksu gedit /boot/grub/menu.lst
```

Search for the "timeout" string and replace the default integer 3 to "1". (This delay's the Ubuntu boot before loading the default GRUB boot entry)

---

### Post by Sherina on 2008-06-22
It takes 3 or 4 minutes for my login screen to appear and I don't see a splash screen. I installed Startup Manager to fix my splash screen and to start up faster.

---

### Post by drs305 on 2008-06-22
Here's something I wrote about grub displays that discusses StartUp-Manager. If you still have questions I'd be glad to answer them if I can.
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by randy78 on 2008-06-22
You may be referring to BUM (Boot up manager) which will allow you to de-select unnecessary processes from starting during boot.

Just be careful what you uncheck!

sudo apt-get install bum

Take Care ;)

---

### Post by Sherina on 2008-06-22
randy78: I am pretty sure it was startup manager but thanks.

Why does gusty show up twice:
        gusty 7.10
        gusty 7.10(recovery)
        gusty 7.10
        gusty 7.10(recovery)

---

### Post by iaculallad on 2008-06-22
> **Sherina said:**
> randy78: I am pretty sure it was startup manager but thanks.

Why does gusty show up twice:
        gusty 7.10
        gusty 7.10(recovery)
        gusty 7.10
        gusty 7.10(recovery)

Everytime the Kernel file is updated (update-grub), it edits your /boot/grub/menu.lst file inserting the latest Kernel version to be used as a boot option. In you're case, Gutsy's Kernel.

---

### Post by drs305 on 2008-06-22
> **Sherina said:**
> randy78: I am pretty sure it was startup manager but thanks.

Why does gusty show up twice:
        gusty 7.10
        gusty 7.10(recovery)
        gusty 7.10
        gusty 7.10(recovery)

It is probably different kernels. Each time a new kernel is introduced it is added to the boot menu. Any version of ubuntu is likely to have at least several kernels introduced during its run.

For instance, in just the short time Hardy has been out, my Hardy entries in menu.lst look like this (I had some others but edited them out):
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro 
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
initrd		/boot/initrd.img-2.6.24-18-generic

```

The extra kernels can be removed from view with Startup-Manager or removed completely using Synaptic (which also updates the menu.lst display).

---

### Post by Sherina on 2008-06-22
Thank you.

is there a way to remove them?

Also does it matter which one I choose?

---

### Post by drs305 on 2008-06-22
> **Sherina said:**
> Thank you.

is there a way to remove them?

Also does it matter which one I choose?

Do you see the kernel information after Gutsy 7.10 as in my example. You should first check to see which kernel you are running:
```
uname -a
```

This kernel should match one of the two gutsy options you see displayed and is definitely the one you want to keep.

My recommendation, however, is that you always keep at least 2 kernels just in case you start having problems with the newer one.

To answer your question, however, you can uninstall it from synaptic. Look for packages called "linux-image" with the kernel number attached. The one with the lower number is the one you would delete (but again, I would always keep 2). If you delete it in synaptic, it will disappear from your grub menu.lst automatically.

You can also just "hide" the entry in StartUp-Manager by changing the number of kernels to keep (in Advance tab). It only hides them, SUM doesn't actually delete them.

---

### Post by Sherina on 2008-06-22
Does having more than one kernel effect startup manager from working? 
because when I installed startup manager before I upgraded to 8.10 I had only one kernel and everything worked fine. 

I am not sure what thread I found this in but it said that the reason for gusty's login screen taking so long to show up was because the screen resolution was wrong. In the to tutorial I read I was told to install SUM and then make sure that the resolution was its lowest setting(640x480) and color depth set to 8 bits.

---

### Post by Sherina on 2008-06-22
> **drs305 said:**
> Do you see the kernel information after Gutsy 7.10 as in my example. You should first check to see which kernel you are running:
```
uname -a
```

This kernel should match one of the two gutsy options you see displayed and is definitely the one you want to keep.

My recommendation, however, is that you always keep at least 2 kernels just in case you start having problems with the newer one.

To answer your question, however, you can uninstall it from synaptic. Look for packages called "linux-image" with the kernel number attached. The one with the lower number is the one you would delete (but again, I would always keep 2). If you delete it in synaptic, it will disappear from your grub menu.lst automatically.

You can also just "hide" the entry in StartUp-Manager by changing the number of kernels to keep (in Advance tab). It only hides them, SUM doesn't actually delete them.


thank you.
```
Linux sherina-laptop 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux
```

---

### Post by drs305 on 2008-06-22
If you are now satisfied with how your system boots I'd leave things alone. In any case, do not delete "linux-image-2.6.22-15-generic" from synaptic or your menu.lst until you start using another one.

I went back and reread your entire thread. Having more than one kernel listed  should not effect your boot times. You can change how LONG the menu is displayed by changing the value in SUM, but the default is 10 seconds so we aren't talking 3-4 minutes. My boot screen is also 640x480 8-bit but I've never played with it.

There is an app called "bootchart" that can display how long each process takes during boot and is used to troubleshoot problems. You can install it via synaptic and a search on this forum will probably provide you with enough information to get you started.

Best wishes.

---

### Post by Sherina on 2008-06-22
Thank you all for your help. I fixed it by changing the resolution in Startup Manager from 640x480 8-bit to 1024x768 16-bit.

---

