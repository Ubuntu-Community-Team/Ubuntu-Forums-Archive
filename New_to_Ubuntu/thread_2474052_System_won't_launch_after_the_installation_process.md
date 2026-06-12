---
title: "System won't launch after the installation process"
date: 2022-04-21
forum: New to Ubuntu
---

### Post by denixius on 2022-04-21
Hello,

I installed 20.04 on my Windows 11 Lenovo IdeaPad 1, however, after the installation, the system won't launch. It just blinks on a black screen with the text upper left corner Reset System.

Secure Boot is disabled, ubuntu is at the first boot order. I can use the Try Ubuntu option, and while the system checks the disk it won't find any problem, also nothing bad happens while installation. Everything seems fine, but I just can't launch the system after the installation.

The specs of my laptop are Intel Celeron N4020 1.1 GHz Turbo Boost 2.8 GHz, Intel UHD Graphics, and 4GB RAM.

I kindly request help with this issue.

Bests,

---

### Post by tea for one on 2022-04-21
Do you have Platform Trust Technology (PTT) in your UEFI settings?
If so, please disable it.

---

### Post by denixius on 2022-04-21
Hi! Thanks for your reply. I installed it with legacy support for boot mode and legacy for priority. Now, I can start the system just with boot mode (F12 on my laptop). However, it won't launch by itself with a regular way. So, I need to open the laptop with boot mode, everything is fine in this way. However, I don't want to use it this way all the time. How can I save from here?

I also disabled PTT. Now, it opens grub. Can I save it from here?

---

### Post by tea for one on 2022-04-21
I do not quite understand your comments.
> I installed it with legacy support for boot mode
You can have legacy support enabled and still install in UEFI mode.
Boot into Ubuntu and run this in a terminal
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Can you post the output in this thread using code tags?
> Now, it opens grub. Can I save it from here? 
Grub is already saved on your PC so I'm not sure what you mean?

---

### Post by denixius on 2022-04-21
> **tea for one said:**
> I do not quite understand your comments. You can have legacy support enabled and still install in UEFI mode.

First, I installed the system which enabled Boot Mode and Boot Priority:  UEFI in BIOS. It won't launch the system, I can't even open the grub.  So, then I changed Boot Mode and Boot Priority as Legacy. now, I can  open the system in Boot Mode by choosing ubuntu.

> **tea for one said:**
>  Boot into Ubuntu and run this in a terminal
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
``` 

This just show me this: "Legacy mode" as a line.

> **tea for one said:**
> Can you post the output in this thread using code tags?

I'm quite new to ubuntu, so, can you please explain what this means and how can I do it? Sorry.

> **tea for one said:**
> Grub is already saved on your PC so I'm not sure what you mean?

I can't even use grub until you suggest disabling PTT. Now, I can't exit from grub to use the system.

This is kinda new situation for me, so, this is why I asked for help. However, I'm learning a lot. Read some articles about grub and boot problems, but they never worked for mine.

Thanks,

---

### Post by tea for one on 2022-04-21
Are you trying to dual boot with Windows 11?

---

### Post by grahammechanical on 2022-04-21
Ubuntu will install in either UEFI boot mode or BIOS/Legacy/Compatibility Support Module (CSM). If we load the Ubuntu live session in UEFI mode then Ubuntu will install in UEFI mode. If you load the Ubuntu live session in BIOS/Legacy/CSM mode then Ubuntu will install in BIOS/Legacy/CSM mode.

It sounds like you have installed Ubuntu in BIOS/Legacy/CSM mode and then used the UEFI settings utility to change the boot to UEFI mode. If this is true then that I guess that is the reason why Ubuntu is not booting except when you use the UEFI settings utility to boot in BIOS/Legacy/CSM mode.

The solution would be to decide which mode you want the machine to boot in. If that is UEFI mode then you re-install Ubuntu and load the Ubuntu live session in UEFI mode.

Regards

---

### Post by denixius on 2022-04-22
> **tea for one said:**
> Are you trying to dual boot with Windows 11?

First, I did try a dual boot with Windows 11. Then I reinstalled it again with a clean boot and erased the disk entirely along with both Windows 11 and Ubuntu. After that, I installed only Ubuntu on the disk.

> **grahammechanical said:**
> Ubuntu will install in either UEFI boot mode or BIOS/Legacy/Compatibility Support Module (CSM). If we load the Ubuntu live session in UEFI mode then Ubuntu will install in UEFI mode. If you load the Ubuntu live session in BIOS/Legacy/CSM mode then Ubuntu will install in BIOS/Legacy/CSM mode.

It sounds like you have installed Ubuntu in BIOS/Legacy/CSM mode and then used the UEFI settings utility to change the boot to UEFI mode. If this is true then that I guess that is the reason why Ubuntu is not booting except when you use the UEFI settings utility to boot in BIOS/Legacy/CSM mode.

The solution would be to decide which mode you want the machine to boot in. If that is UEFI mode then you re-install Ubuntu and load the Ubuntu live session in UEFI mode.

Regards

Hello! I added images below for every step I followed while installing 20.04. And yes, I boot the disk as UEFI with Rufus. I just wanted to try if it is work on Legacy, too. But it won't work at all. So, once again, as you suggested I changed back Boot Mode to UEFI and enabled Secure Boot. Again, it didn't work.

Step 1 (Secure Boot) - [https://images2.imgbox.com/fc/fd/zS9fc6HF_o.png](https://images2.imgbox.com/fc/fd/zS9fc6HF_o.png) (I tried disabling Secure Boot option, too.)
Step 2 (Boot Mode) - [https://images2.imgbox.com/5e/49/JDIDByF6_o.png](https://images2.imgbox.com/5e/49/JDIDByF6_o.png)
Step 3 (Installation Type) - [https://images2.imgbox.com/a4/b7/wopXtNs1_o.png](https://images2.imgbox.com/a4/b7/wopXtNs1_o.png)
Step 4 (Partition Warning to Disk Write) - [https://images2.imgbox.com/fd/fa/awRYAsJS_o.png](https://images2.imgbox.com/fd/fa/awRYAsJS_o.png)
Step 5 (Installing) - [https://images2.imgbox.com/21/dc/XrWYkR1L_o.png](https://images2.imgbox.com/21/dc/XrWYkR1L_o.png)
Step 6 (Installation Complete) - [https://images2.imgbox.com/53/07/jX6v9q2D_o.png](https://images2.imgbox.com/53/07/jX6v9q2D_o.png)
Step 7 (Remove the disk and then press Enter) - [https://images2.imgbox.com/64/16/UAvd7paq_o.png](https://images2.imgbox.com/64/16/UAvd7paq_o.png)
Step 8 (Black Screen with Reset System Message) - [https://images2.imgbox.com/1d/39/ipmHLuB8_o.png](https://images2.imgbox.com/1d/39/ipmHLuB8_o.png) (On this screen it blinks, restarts the system and shows this message every time.)

I'm really confused about what is the problem... I will try the latest version too, 22.04. 

Any thoughts on what can I do?

---

### Post by denixius on 2022-04-22
Hi!

It seems, disabling PTT and Secure Boot solved the problem. Now, I can boot Ubuntu 20.04 easily.

Thank you!

---

### Post by tea for one on 2022-04-22
> **denixius said:**
> Hi!
It seems, disabling PTT and Secure Boot solved the problem. Now, I can boot Ubuntu 20.04 easily.
Thank you!
Splendid.
Have you now installed in UEFI mode with GPT (Guid Partition Table)?

Also, it is useful to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by denixius on 2022-04-22
> **tea for one said:**
> Splendid.
Have you now installed in UEFI mode with GPT (Guid Partition Table)?

Also, it is useful to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Yes. I boot the disk with a fresh version of 20.04 again, and I used Rufus. And the rest of it was easy. I used your suggestion; disabled PTT and Secure Boot, and then magic happened.

Thank you!

---

