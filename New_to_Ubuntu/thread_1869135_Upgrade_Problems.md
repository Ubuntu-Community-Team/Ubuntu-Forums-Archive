---
title: "Upgrade Problems"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by icyubok on 2011-10-25
I'm a noob at Linux, so maybe I missed this problem. Search is not helping, if I'm doing it correctly.
I have Ubuntu 10.10 Maverick Meerkat on my computer and tried to upgrade to Natty 11.04 as I get the message to upgrade when I use the Update Manager. After the upgrade process, I rebooted the computer and viewed a blank screen with a floating rectangle with the message, "Input not supported". I have tried this several times. I then downloaded the Ocelot 11.10 iso  and made a disk to upgrade from my Ubuntu 10.10 version only with the same results, "Input not supported." I really want to break away from Windows, but this is a big disappointment. Maybe the following will help someone to figure out my problem or direct me to a thread.
VGA: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
ISA bridge: nVidia Corporation MCP61 LPC Bridge (Rev a2)
SMBus: nVidia Corporation MCP61 SMBus (Rev a2)
PCI bridge: nVidia Corporation MCP61 PCI bridge (Rev a2)
Host bridge: Advanced Micro Devices '[AMD] Family 10h Processor HyperTran sport Configuration
Multimedia Audio Controller: Creative Labs CA0106 Soundblaster
:(

---

### Post by Rubi1200 on 2011-10-25
Hi and welcome to the forums :-)

Try booting into recovery mode and then use the suggestion in post # 2 here:
[http://ubuntuforums.org/showthread.php?t=1769385](http://ubuntuforums.org/showthread.php?t=1769385)

You can also check out this thread:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by melora.adams on 2011-10-26
It's really my own fault, I guess. I let Ubuntu persuade me to upgrade to Ocelot. 

Now it won´t boot at all, unless I select an older kernel - about three kernels earlier. 
Linux 3.0.0-12-generic

Here's what I get:
error: cannot read the Linux header
error: you need to load the kernel first

I just kept selecting earlier kernels until finally it booted, so I guess it's a kernel problem. Now it's got a new user interface, too, so I don't know how to so much as open a terminal window. (there's nothing on the top left line -- no Applications, or Places, or System)

So I'm going to continue to run using an old kernel, since I can't boot a newer one. And try to figure out how to use this new interface, though I suspect that if I could get the boot to work properly, the interface would be better.

If you can help me, please do.

---

### Post by cariboo on 2011-10-27
> **melora.adams said:**
> It's really my own fault, I guess. I let Ubuntu persuade me to upgrade to Ocelot. 

Now it won´t boot at all, unless I select an older kernel - about three kernels earlier. 
Linux 3.0.0-12-generic

Here's what I get:
error: cannot read the Linux header
error: you need to load the kernel first

I just kept selecting earlier kernels until finally it booted, so I guess it's a kernel problem. Now it's got a new user interface, too, so I don't know how to so much as open a terminal window. (there's nothing on the top left line -- no Applications, or Places, or System)

So I'm going to continue to run using an old kernel, since I can't boot a newer one. And try to figure out how to use this new interface, though I suspect that if I could get the boot to work properly, the interface would be better.

If you can help me, please do.

It sounds like you upgrade didn't complete properly, which seems to be a very common problem for new users. Open a termianl:

```
Ctrl-Alt-t
```

and type the following commands:

```
sudo apt-get -f install
```

then

```
sudo apt-get update
```

followed by

```
sudo apt-get dist-upgrade
```

BTW, you could have clicked the settings button on the update-manager window, and set the notify if there is a new version to never.

---

### Post by melora.adams on 2011-10-27
Thank you so much for your help. All went well (it was great to see the terminal window). That is, up until the last command. The last two lines printed by "sudo apt-get dist-upgrade" were

dpkg: error: dpkg status database is locked by another process
E: Sub-process /usr/bin/dpkg returned an error code (2)

I've left it as it is rather than restart. Should I ignore the error and go ahead, or is there more that I need to do at this point?

You are quite right about not accepting the upgrade without knowing what I was doing. Thanks again.

---

### Post by melora.adams on 2011-10-28
I went ahead and restarted this morning. No change; I'm still getting 

error: cannot read the Linux header
error: you need to load the kernel first

I still have to choose an old kernel in order to boot.

Is there some way I could undo the "upgrade" which has caused the trouble? Or should I just bag it and do a fresh install of the old version which worked, or should I look for a different Linux?

---

### Post by frotzed on 2011-10-28
> **cariboo907 said:**
> 

```
sudo apt-get -f install
```



Question: What does the above command do?  I've never seen the "-f install"

EDIT: Nevermind.  Searched forums, found answer to my own question.

---

### Post by zx5000 on 2011-12-16
Hi All,

I recently took the standard security upgrades which include 3.0.0-13 and have the same problem. I allowed it to upgrade to -14 which I hoped would fix this as well. Needless to say the -12 kernel boots fine. The /boot folder looks correct (see below). Until this is fixed I'm selecting the -12 as my default in the grub.cfg.

Does anyone have ideas about how to fix this?

```

-rw-r--r-- 1 root root   734707 2011-10-07 15:37 abi-3.0.0-12-generic
-rw-r--r-- 1 root root   734780 2011-11-02 14:28 abi-3.0.0-13-generic
-rw-r--r-- 1 root root   734974 2011-11-21 19:33 abi-3.0.0-14-generic
-rw-r--r-- 1 root root   141616 2011-10-07 15:37 config-3.0.0-12-generic
-rw-r--r-- 1 root root   142026 2011-11-02 14:28 config-3.0.0-13-generic
-rw-r--r-- 1 root root   141993 2011-11-21 19:33 config-3.0.0-14-generic
drwxr-xr-x 3 root root    12288 2011-12-16 14:35 grub
-rw-r--r-- 1 root root 13621590 2011-10-25 07:58 initrd.img-3.0.0-12-generic
-rw-r--r-- 1 root root 13631233 2011-11-23 06:19 initrd.img-3.0.0-13-generic
-rw-r--r-- 1 root root 13641015 2011-12-10 20:58 initrd.img-3.0.0-14-generic
-rw-r--r-- 1 root root   176764 2011-05-02 17:53 memtest86+.bin
-rw-r--r-- 1 root root   178944 2011-05-02 17:53 memtest86+_multiboot.bin
-rw------- 1 root root  2130938 2011-10-07 15:37 System.map-3.0.0-12-generic
-rw------- 1 root root  2131134 2011-11-02 14:28 System.map-3.0.0-13-generic
-rw------- 1 root root  2132195 2011-11-21 19:33 System.map-3.0.0-14-generic
-rw------- 1 root root     1215 2011-10-07 15:40 vmcoreinfo-3.0.0-12-generic
-rw------- 1 root root     1215 2011-11-02 14:30 vmcoreinfo-3.0.0-13-generic
-rw------- 1 root root     1215 2011-11-21 19:35 vmcoreinfo-3.0.0-14-generic
-rw-r--r-- 1 root root  4632128 2011-10-12 09:36 vmlinuz-3.0.0-12-generic
-rw------- 1 root root  4632736 2011-11-02 14:28 vmlinuz-3.0.0-13-generic
-rw------- 1 root root  4636512 2011-11-21 19:33 vmlinuz-3.0.0-14-generic


```

---

### Post by zx5000 on 2011-12-23
Tried removing newer (unbootable) kernels with apt-get remove and got the grub> prompt. Tried grub-update, grub-install, grub-purge-and-install always grub>

Did an "update" install from 11.10 to 11.10 and lost everything that was not in my home folder. All mysql databases, printer settings, installed applications and libraries.

Upgrades are the only thing that is weak in Ubuntu but it's a killer! It all started with the automatic update that included 3.0.0-13-generic kernel.

---

### Post by zx5000 on 2012-05-04
For anyone following this I discovered that my issue was a BIOS issue.

[http://superuser.com/questions/381539/cannot-read-the-linux-header-new-install-old-machine](http://superuser.com/questions/381539/cannot-read-the-linux-header-new-install-old-machine)

---

