---
title: "moved my /lib folder"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by akmodi on 2013-05-20
Hi -- I have a ubuntu 12.04 on a headless server, 4gb flash disk. The data drives are on ZFS, folder is /data.

The root disk was full , so wanted to move the /lib folder to the ZFS disk and then symbolic link it to the / folder. ](*,)](*,)

The problem being that I cannot execute any commands as  (Now I realize ) I have moved my /lib folder.

Can some one help? :confused:

Thanks

---

### Post by Impavidus on 2013-05-20
You can boot from a live disk and then try to move it back. /lib has to be in the root partition, just like /etc, /sbin and /root. It is save to move /usr to a different partition.

---

### Post by akmodi on 2013-05-20
HI Impavidus,

2 problems, first the /lib is now on the ZFS folder, so a live disk will not read to it. Secondly, the ubuntu is on a volumne manager -- so will this be read/ written to  from a live disk? I was hoping to be able to type a command to state where the /lib folder is, then move it back. 

I have not shut off the system, so am unsure whether I will be able to boot back onto it. Can you confirm / deny that atleast it will boot to a partially working system? Then maybe I can work on the above options.

Thanks in advance.

---

### Post by The Cog on 2013-05-20
I think Impavidus is right. /lib has to be on the root partition because it needs access to /lib contents to be able to mount other partitions. So I think at the moment, it could not boot at all. But without being able to run commands, I can't think how to get things back. 

Maybe putting the disk as a second disk into another system (specially installed for the job perhaps) that can mount all the partitions and move /lib back would work.

---

### Post by steeldriver on 2013-05-20
I think #1 problem will be just about all your shells are dynamically linked to shared libs on /lib 

```

$ ldd $(which bash)
        linux-gate.so.1 =>  (0xb77a7000)
        libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xb7780000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb777b000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb75d0000)
        /lib/ld-linux.so.2 (0xb77a8000)
$
$ ldd $(which mv)
        linux-gate.so.1 =>  (0xb7779000)
        libselinux.so.1 => /lib/i386-linux-gnu/libselinux.so.1 (0xb7752000)
        librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xb7749000)
        libacl.so.1 => /lib/i386-linux-gnu/libacl.so.1 (0xb773f000)
        libattr.so.1 => /lib/i386-linux-gnu/libattr.so.1 (0xb7739000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb758f000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb758a000)
        /lib/ld-linux.so.2 (0xb777a000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb756f000)
$
```

If you still have a shell prompt up (presumably meaning whatever .so are loaded in memory) and the zfs parition with your lib on it is still mounted, then you could try dropping to static-sh / busybox which I *think* has a mv built-in 

DISCLAIMER - I HAVE NEVER TRIED THIS!

```
$ file -L /bin/static-sh
/bin/static-sh: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), **statically linked**, for GNU/Linux 2.6.24, BuildID[sha1]=0xcd1f26d962ba4460c5239a401d0568c6f2fded27, stripped

```

```
$ static-sh


BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

~ $ help
Built-in commands:
------------------
        . : [ [[ alias bg break cd chdir command continue echo eval exec
        exit export false fg getopts hash help jobs kill let local printf
        pwd read readonly return set shift source test times trap true
        type ulimit umask unalias unset wait [ [[ acpid addgroup adduser
        adjtimex ar arping ash awk basename blockdev brctl bunzip2 bzcat
        bzip2 cal cat chgrp chmod chown chroot chvt clear cmp cp cpio
        crond crontab cut date dc dd deallocvt delgroup deluser df diff
        dirname dmesg dnsdomainname dos2unix dpkg dpkg-deb du dumpkmap
        dumpleases echo ed egrep eject env expand expr false fbset fdflush
        fdisk fgrep find fold free freeramdisk fsck.minix ftpget ftpput
        getopt getty grep gunzip gzip head hexdump hostid hostname httpd
        hwclock id ifconfig ifdown ifup init ionice ip ipcalc kill killall
        klogd last length less linuxrc ln loadfont loadkmap logger login
        logname logread losetup ls lzcat lzma makedevs md5sum mdev mesg
        microcom mkdir mkfifo mkfs.minix mknod mkswap mktemp more mount
        mt [COLOR=#ff0000]**mv **[/COLOR]nameif nc netstat nslookup od openvt passwd patch pidof
        ping ping6 pivot_root printf ps pwd rdate readlink realpath renice
        reset rev rm rmdir route rpm rpm2cpio run-parts sed seq setkeycodes
        sh sha1sum sha256sum sha512sum sleep sort start-stop-daemon static-sh
        strings stty su sulogin swapoff swapon switch_root sync sysctl
        syslogd tac tail tar tee telnet telnetd test tftp time timeout
        top touch tr traceroute traceroute6 true tty tunctl udhcpc udhcpd
        umount uname uncompress unexpand uniq unix2dos unlzma unxz unzip
        uptime usleep uudecode uuencode vconfig vi vlock watch watchdog
        wc wget which who whoami xargs xz xzcat yes zcat

~ $
```

---

