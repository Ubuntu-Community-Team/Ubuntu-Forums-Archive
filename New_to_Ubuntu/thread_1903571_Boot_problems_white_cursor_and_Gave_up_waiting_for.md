---
title: "Boot problems: white cursor and Gave up waiting for root device"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2012-01-02
I just installed Ubuntu 10.04LTS (a dual boot with Windows 7), and have some issues booting into Ubuntu; my problem is pretty much a combination of

 - [http://ubuntuforums.org/showthread.php?t=981159](http://ubuntuforums.org/showthread.php?t=981159)
 - [http://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot](http://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot)

The top of my grub file originally looked  this

  ```
  GRUB_DEFAULT=0
    #GRUB_HIDDEN_TIMEOUT=0
    GRUB_HIDDEN_TIMEOUT_QUIET=true
    GRUB_TIMEOUT=10
    GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    GRUB_CMDLINE_LINUX=""

```

Using this meant that immediately after the `grub` menu screen, I would get a blinking white cursor, and nothing else. Ubuntu would not boot at all

After some googling, I changed the quiet splash line to

```
    GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
```

which still gives me the blinking white cursor, but after a few minutes I get 
```

    Gave up waiting for root device. Common problems:
    Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
    - Missing modules (cat /proc/modules: ls /dev)
    ALERT! /dev/disk/by-uuid/0e53b2-5714-4c83-ae75-aa5a4329545d does not exist. Dropping to a shell!
    
    BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
    Enter 'help' for a list of built-in commands.
```
    

If I type exit, then eventually Ubuntu will boot (hurrah!) However, this is obviously not ideal, as each boot is taking about 10 minutes. 

Can anyone help me fix this? I'll be happy to post output from any commands that will help.

---

### Post by drs305 on 2012-01-02
Try the Boot Repair Tool. It does a great job fixing Grub-related boot problems. 

If that doens't fix things, run the boot info script from within the Boot Repair Tool and post the contents. That will give us information that should help us figure out what's going wrong. But Boot Repair will probably work for you.

Click the 'Boot Repair' link in my signature line.

---

### Post by C. M .Hughes on 2012-01-03
Thanks very much for your reply :)

I installed boot-repair and ran the Recommended Repair, but sadly the issue persists :( Here is a link to the output from the BootInfo summary

[http://paste.ubuntu.com/792313/](http://paste.ubuntu.com/792313/)

---

### Post by drs305 on 2012-01-03
If you run the following do you get a return for sda5 and do they match:
```
sudo blkid /dev/sda5
ls -l /dev/disk/by-uuid | grep sda5
```

This will at least tell us if there might be a problem with the UUID.

Did you try the recommendations from the other threads you referenced. I know a lot of suggestions were thrown out for users to try...  I recall reviewing that thread at the time and hoping there would be a definitive answer.

Have you installed the video driver for your system, which is often the solution to the 'nomodeset' requirement.

I can't spend any time tonight researching this but perhaps someone else will see the post. I'll try to get back to it tomorrow if nobody else has presented a solution.

---

### Post by drs305 on 2012-01-03
Another thing you can try is manually editing the grub entry. Press 'e' with the first menuentry highlighted on the grub menu.

Cursor to the 'search' line and remove it entirely by holding down the DEL key.

Cursor to the 'linux' line and change this part of the line:

```
root=UUID=0e53b3b2-5714-4c83-ae75-aa5a4329545d
to 
root=/dev/sda5
```
Then press CTRL-X to boot and see if that helps.

---

### Post by C. M .Hughes on 2012-01-04
Thanks very much for your reply. I tried your idea of editing the grub from 


```
root=UUID=0e53b3b2-5714-4c83-ae75-aa5a4329545d
```

to
 
```
root=/dev/sda5
```

but I'm afraid it didn't help. Here is the output from the commands you requested

```
sudo blkid /dev/sda5 
/dev/sda5: UUID="0e53b3b2-5714-4c83-ae75-aa5a4329545d" TYPE="ext4"
```

and 

```
ls -l /dev/disk/by-uuid/|grep sda5
lrwxrwxrwx 1 root root 10 2012-01-04 15:31 0e53b3b2-5714-4c83-ae75-aa5a4329545d -> ../../sda5

```

---

### Post by C. M .Hughes on 2012-01-05
I believe I have made some  progress by following the code here

[http://ubuntuforums.org/showthread.php?t=981159&page=4](http://ubuntuforums.org/showthread.php?t=981159&page=4)
```

$ sudo fdisk -l
$ sudo fsck /dev/sda5
$ sudo mount /dev/sda5 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo chroot /mnt
$ update-grub

```

Press Ctrl-D to get back to normal prompt and type to unmount:

```

$ sudo umount /mnt/dev
$ sudo umount /mnt

```

I no longer get the 'Gave up waiting...' message, and it boots just fine. Thanks for your help :)

---

