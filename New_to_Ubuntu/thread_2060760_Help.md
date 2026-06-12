---
title: "Help"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by sachinvaidya9999 on 2012-09-20
:KS. with Ubuntu Desktop Oreginal CD which I got in PC Maxzine.

I was successfully install Ubuntu 11.10 and system is showing restart message, I am restarting my pc.

And I am getting 5 messages 

1) Ubuntu, with Linux 3.0.0-12-generic
2) Ubuntu, with Linux 3.0.0-12-generic ( recovery mode)
3) Memory test (mentest86+)
4) Memory test (mentest86+ , serial console 115200)
5) Microsoft Windows XP Professional (On/dev/sda1) 

When  I pressing 1 option my pc is going to sleep mode and need to restart . I  am using xp then it is start and I also checking my all drivers so i am  not getting and Files relating with Ubuntu .  I believe that only  Ubuntu Bootloader is install Please Help I am using Ubuntu 12.04 and  12.10 but they are showing some problems HELP FRIEND.

---

### Post by sandyd on 2012-09-20
[B]Please create only one post on your topic.

Thanks![/B]

---

### Post by sachinvaidya9999 on 2012-09-20
What it mean

---

### Post by sachinvaidya9999 on 2012-09-20
(I am sending you my hardware information)I was installing Ubuntu 11.10 with XP 3 Pro. with Ubuntu Desktop Oreginal CD which I got in PC Maxzine.

I was successfully install Ubuntu 11.10 and system is showing restart message, I am restarting my pc.

And I am getting 5 messages 

1) Ubuntu, with Linux 3.0.0-12-generic
2) Ubuntu, with Linux 3.0.0-12-generic ( recovery mode)
3) Memory test (mentest86+)
4) Memory test (mentest86+ , serial console 115200)
5) Microsoft Windows XP Professional (On/dev/sda1) 

When  I pressing 1 option my pc is going to sleep mode and need to restart . I  am using xp then it is start and I also checking my all drivers so i am  not getting and Files relating with Ubuntu .  I believe that only  Ubuntu Bootloader is install Please Help I am using Ubuntu 12.04 and  12.10 but they are showing some problems HELP FRIEND.

---

### Post by oldfred on 2012-09-20
Please download into liveCD this repair tool. Post the link on the BootInfo report so we can see your configuration.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If grub2 boot loader is installed and booting to the grub menu, it may not be a boot issue but graphics or need for some other boot parameter.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by cariboo on 2012-09-20
This may be a bit easier, highlight the firstseleclion on the menu, and press ***e*** then add:

```
nomodeset
```

to the end of the line and boot. If all went well, you should boot to a desktop.

---

### Post by YannBuntu on 2012-09-21
Hello
If 'nomodeset' solves the problem, don't forget to report it via the 'ubuntu-bug linux' command.
Also, remember that 'nomodeset' disables many many functionalities, so better trying to find a "smoother" option.

---

### Post by oldos2er on 2012-09-21
> **sachinvaidya9999 said:**
> What it mean

Please don't create more than one thread for each problem or question. Threads merged.

---

