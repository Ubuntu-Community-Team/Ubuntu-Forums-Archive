---
title: "I can't boot the desktop  it seems no space for the system, how can I fix it??"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by liangliming on 2013-05-27
Hello, everyone! 

Yesterday when I was exucting a C++ program with eclipse in linuxcnc-ubuntu 10.04 OS. I met some problem about the C++ program, it always happens, so I reboot the computer, unfortunately, I failed to login the desktop, it display the following message:

[I]Insmod: Can’t read ‘/usr/realtime-2.6.32-122-rtai/modules/rtai_shm.ko’: No such file or directly
Speech-dispatcher configured for user session
                                      Starting common Unix Printing system: cupsd                                   [OK]
pulseAnd configured for per-user sessions
                                                Enabling additional executable binary formats binfmt-support    [OK]
Checking battery state…       [/I]                                                                                             [OK]

I entered the tty1, and found  that the [COLOR=#333333][FONT=Helvetica]dev/sda1   was 100% full used,
So I search a lot of information from the internet, and clean the Trash as suggested, however, It dosen't work, the [/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]dev/sda1   is still 100% used.
What  should I do now, can you help me?
any suggest is appreciated!
Thanks a lot!

[/FONT][/COLOR]

---

### Post by MG&amp;TL on 2013-05-28
Well, if there's no space for the system to boot, there's a fairly simple solution: you need to get rid of some of your files or other data. Either back them up, or just find ones you don't need anymore, then remove them.

I'm assuming that /dev/sda1 is your ubuntu partition: you can find out if it is by running:

```
sudo fdisk -l
```

and seeing which are marked as 'linux': there's probably a big partition with ubuntu on, and a roughly 4GB partition for swap data.

As an alternative to removing your files, you could try:

```
sudo apt-get autoremove
```

which will remove unecessary packages that are no longer required.

---

### Post by liangliming on 2013-05-28
> **MG&TL said:**
> Well, if there's no space for the system to boot, there's a fairly simple solution: you need to get rid of some of your files or other data. Either back them up, or just find ones you don't need anymore, then remove them.

I'm assuming that /dev/sda1 is your ubuntu partition: you can find out if it is by running:

```
sudo fdisk -l
```

and seeing which are marked as 'linux': there's probably a big partition with ubuntu on, and a roughly 4GB partition for swap data.

As an alternative to removing your files, you could try:

```
sudo apt-get autoremove
```

which will remove unecessary packages that are no longer required.

Thanks for your reply, I enter the desktop with the code :startx
and then I remove something . Therefore I got about 34M free space and then ,I let it alone,and no one use it, after a few hours, I found it reduce to 14M, I don not know why, then ,I use another computer search some information in the internet, it takes about few minutes ,when I back to check the free space decrease 0.3M, and it continue decrease to 13M free space until I reboot it. I checked again, It stable now, the free space is always 13.2M.

So what is the problem of my system? what should I do?

---

### Post by MG&amp;TL on 2013-05-28
> **liangliming said:**
> Thanks for your reply, I enter the desktop with the code :startx
and then I remove something . Therefore I got about 34M free space and then ,I let it alone,and no one use it, after a few hours, I found it reduce to 14M, I don not know why, then ,I use another computer search some information in the internet, it takes about few minutes ,when I back to check the free space decrease 0.3M, and it continue decrease to 13M free space until I reboot it. I checked again, It stable now, the free space is always 13.2M.

So what is the problem of my system? what should I do?

Temporary files are always being created and destroyed. Log files, configuration, cookies and such. Your system has no problem as such, just an acute lack of disk space.

---

### Post by liangliming on 2013-05-29
> **MG&TL said:**
> Temporary files are always being created and destroyed. Log files, configuration, cookies and such. Your system has no problem as such, just an acute lack of disk space.
Thanks for the information, I have clear the log,and also the histories of Firefox, thus I get about 200M freespace!

---

