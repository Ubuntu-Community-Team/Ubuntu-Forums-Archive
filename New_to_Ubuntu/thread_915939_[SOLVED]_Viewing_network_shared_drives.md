---
title: "[SOLVED] Viewing network shared drives"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by moody_mark on 2008-09-10
Hi Folks, This doesnt seem to be a problem on ubuntu or kubuntu with the resident file managers on there but in xubuntu I cannot seem to find a way to browse or map a shared drive. I can only add it as a FTP link (im mapping to a NAS drive).

Can this be done with the resident Xubuntu file manager or do i need to install Nautilus or Dolphin etc?

---

### Post by moody_mark on 2008-09-13
Well whadaya know I solved it! With a bit of googling about and a lot of dead ends, I found out something on another forum! Heres how;

The first problem I had was when I tried to mount my drive like so

```

curtis@marge:/media$ sudo mount.cifs //192.168.2.2/Shared /home/curtis/NetworkShare/ -o username=curtis

```

I got the following error

```

mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

So after some googling around I found out that the following allowed the mount to work

```

echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled

```

Now as I'm kinda new to Linux I checked out (and backed up) the file before I edited it. Basically this file has a "1" or a "0" in it. I'm not too sure what it does but anyway this seemed to solve my problem. Note: you need to be root to edit this file using "sudo" wouldn't work, possibly because of permissions. So, to test i did this;

```

root@marge:/media# echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
root@marge:/media# exit
exit
curtis@marge:/media$ sudo mount.cifs //192.168.2.2/Shared /home/curtis/NetworkShare/ -o username=curtis

```

Then I checked I could browse, read / write all my NAS directories and files (well, not every single one!). All was good...

The next problem was to ensure that this persisted across reboots. So I rebooted and guess what? It didn't! Thats because you have to put the entry into your **/etc/fstab** file. Now when you add the mount its added to another file called **/etc/mtab**. So I checked in here to see what the format was after repeating my actions above;

**/etc/mtab** had the following

```

//192.168.2.2/Shared /home/curtis/NetworkShare cifs rw,mand 0 0

```

I copied that to append current entries in **/etc/fstab** and added the following (its always good to have a comment)

```

#Network File Share
//192.168.2.2/Shared /home/curtis/NetworkShare cifs rw,mand 0 0

```

Next thing I found that even after a reboot the **/proc/fs/cifs/LinuxExtensionsEnabled** file value was reset to "1" again! So I done a bit more looking around and found out that you have to put the following into /etc/rc.local;

```

# Line added to allow NAS drive access
echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled

exit 0

```

Note: (the exit 0 was already there just showing that it was left at the end).

So that was it for me. Its a shame xubuntu needs to have all this done when Ubuntu and Kubuntu have file managers and probably some other components that allow network browsing by default. I did try installing "Nautilus" but it didn't work at all, so I got rid of it. The **Thunar file manager** is fine. Im running xubuntu because this is a low spec machine and I wanted something simple, reliable and faster than Windows XP which is on the other HDD (dual boot). Heres my machine CPU spec for reference;

```

  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MiB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.6
          size: 750MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
(omitted rest of lshw command output)

```

I want to thank the following posts for helping me with my problem;

[http://www.linuxquestions.org/questions/linux-networking-3/mount.cifs-mount-error-20-not-a-directory-443693/](http://www.linuxquestions.org/questions/linux-networking-3/mount.cifs-mount-error-20-not-a-directory-443693/)

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

[http://ubuntuforums.org/archive/index.php/t-188027.html](http://ubuntuforums.org/archive/index.php/t-188027.html)

There was also a big thread here, but to be honest it didn't work for me. However it does seem to have helped a lot of people so I thought it worth referencing here;

[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131) 

I hope this thread helps some others ;)

---

