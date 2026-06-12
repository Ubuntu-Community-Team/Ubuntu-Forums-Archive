---
title: "Problem saving new swap partition using /etc/fstab/ &quot;access denined'"
date: 2017-08-12
forum: New to Ubuntu
---

### Post by small.wilson on 2017-08-12
When I initially installed Ubuntu I failed to create a swap partition during the instillation, so I did so using the terminal.
My problem is when attempting to save my changes so I will not have to make them again every time I restart my computer,
I get this permission denied error:

```
hagile@eli-pc:~$ sudo -s
[sudo] password for hagile: 
root@eli-pc:~# free -h
              total        used        free      shared  buff/cache   available
Mem:           7.3G        2.2G        3.5G         36M        1.5G        4.7G
Swap:           13G          0B         13G
root@eli-pc:~# /etc/fstab
bash: /etc/fstab: Permission denied


```
I am a newer Linux user.
I also hope this is the appropriate forum, please forgive me if it is not.

---

### Post by DuckHook on 2017-08-12
Welcome to the forums, small.wilson

You are posting in the proper forum.

The following link might be of assistance: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Merely typing into bash:```
/etc/fstab
```&#8230;will not do anything for you. In this case, the "Permission denied" error is misleading. The real problem is that you're invoking *fstab*, and *fstab* is designed to be executed at boot; not from an interactive terminal session.

If you are trying to ***edit*** fstab:
[LIST=1]
[*]you don't need:```
sudo -s
```
[*]the proper command is:```
sudo nano /etc/fstab
```
[/LIST]

---

### Post by vocx on 2017-08-12
> **small.wilson said:**
> When I initially installed Ubuntu I failed to create a swap partition during the instillation,** so I did so using the terminal.**
My problem is when attempting to save my changes so I will not have to make them again every time I restart my computer,
I get this permission denied error:

How exactly did you create a swap partition from the terminal? Which guide did you follow?

> 
```

root@eli-pc:~# /etc/fstab
bash: /etc/fstab: Permission denied

```
I am a newer Linux user.
I also hope this is the appropriate forum, please forgive me if it is not.
What you are attempting to do here is run the "/etc/fstab" file as if it were a program. This file is not a program, it should not even have execute permissions.
```

wilson@eli-pc:~$ ls -alh /etc/fstab
-rw-r--r-- 1 root root 2.7K Jul 11 17:39 /etc/fstab

```

What this file does is pass its information as arguments to the "mount" command. If the "/etc/fstab" file has the appropriate line for swap, you can mount the swap partition using mount.
```

# inside "/etc/fstab"

# swap was on /dev/sda2 during installation
UUID=7c0bb94d-b555-4d08-87e1-d784d5379f79 none            swap    sw              0       0

```

```

# mount all partitions defined in the "/etc/fstab" file
sudo mount -a

```

The "/etc/fstab" file also defines which partitions will be mounted during boot, so your swap partition should also be mounted automatically when you reboot and start your system again.

Also, don't use "sudo -s" and then type a bunch of commands. You will be running all these commands with root privileges, but you don't want to run a lot of stuff with root. It's better to use "sudo" with the specific command you want to use, like "mount".

---

### Post by small.wilson on 2017-08-12
> **vocx said:**
> How exactly did you create a swap partition from the terminal? Which guide did you follow?


What you are attempting to do here is run the "/etc/fstab" file as if it  were a program. This file is not a program, it should not even have  execute permissions.
```

wilson@eli-pc:~$ ls -alh /etc/fstab
-rw-r--r-- 1 root root 2.7K Jul 11 17:39 /etc/fstab

```

What this file does is pass its information as arguments to the "mount"  command. If the "/etc/fstab" file has the appropriate line for swap, you  can mount the swap partition using mount.
```

# inside "/etc/fstab"

# swap was on /dev/sda2 during installation
UUID=7c0bb94d-b555-4d08-87e1-d784d5379f79 none            swap    sw              0       0

```

```

# mount all partitions defined in the "/etc/fstab" file
sudo mount -a

```

The "/etc/fstab" file also defines which partitions will be mounted  during boot, so your swap partition should also be mounted automatically  when you reboot and start your system again.

Also, don't use "sudo -s" and then type a bunch of commands. You will be  running all these commands with root privileges, but you don't want to  run a lot of stuff with root. It's better to use "sudo" with the  specific command you want to use, like "mount".
Thank you for your response, I followed the link you provided carefully, along with your advice it helped solve my problem, thank you very much. I now know the appropriate setting to invoke *fstab*.:)

> The "/etc/fstab" file also defines which partitions will be mounted  during boot, so your swap partition should also be mounted automatically  when you reboot and start your system again.

Also, don't use "sudo -s" and then type a bunch of commands. You will be  running all these commands with root privileges, but you don't want to  run a lot of stuff with root. It's better to use "sudo" with the  specific command you want to use, like "mount".

Thank you for your reply Vocx, you've shown me alot, this is the guide I used  I followed those steps until I ran into the error.:
[URL="https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04"]https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04

[/URL]

---

