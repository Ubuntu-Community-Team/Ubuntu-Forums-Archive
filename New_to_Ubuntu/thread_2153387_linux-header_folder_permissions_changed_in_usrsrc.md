---
title: "linux-header folder permissions changed in /usr/src"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by enoch7thgen on 2013-06-10
greetings all,

I accidentally messed up file permissions on the /usr/src folder and did it recursively so now everything that was in /usr/src has been altered in their permissions ie linux-headers-3.5.0-23 + the generic + linux-headers-3.5.0-32 + generic.   Will somebody please point me to a reference guide on what the default permissions are for /usr/src and linux-headers as I have chmoded them to
777.   My mistake is limited to this folder (src) and all that's in it (linux-headers).  Im afraid to shut down  the computer so Im going to leave it on until i have a reply.


Thanks to the one who saves my bacon [CENTER][COLOR=#000000]](*,)

enoch7thgen[/COLOR][/CENTER]

---

### Post by claracc on 2013-06-11
All of the linux-headers directories inside /usr/src are owned by root, owner group is also root and the permissions are: drwxr-xr-x

I think that your best bet is to reinstall the system, anycase, I have found this link: [http://sysadminnotebook.blogspot.com.es/2012/06/how-to-reset-folder-permissions-to.html](http://sysadminnotebook.blogspot.com.es/2012/06/how-to-reset-folder-permissions-to.html), I don't know if it can be useful in your case but you can try.

---

### Post by Impavidus on 2013-06-11
All directories have permissions 0755, all files 0644 and all have root:root as owner:group.

On my system there's one exception, which must be the default as I didn't change it, and this the /usr/scr directory itself. It's group is src and it has the setgroupID bit set and group write permission: root:src, permissions 2775.

This shouldn't be too difficult to fix without reinstalling.

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]enoch7thgen; Hi !

I thought I had posted this earlier... but did not see it -> maybe be of some assistance along with [/COLOR][COLOR=#000000]Impavidus' advise.[/COLOR][COLOR=#000000]

If this helps... minimal install of 13.04:
[/COLOR]>  
sysop@1304mini:~$ ls -la /usr/src/
total 32
drwxr-xr-x  8 root root 4096 Jun  1 01:20 .
drwxr-xr-x 10 root root 4096 May 19 10:53 ..
drwxr-xr-x 24 root root 4096 May 19 10:56 linux-headers-3.8.0-21
drwxr-xr-x  7 root root 4096 May 19 10:56 linux-headers-3.8.0-21-generic
drwxr-xr-x 24 root root 4096 May 24 21:18 linux-headers-3.8.0-22
drwxr-xr-x  7 root root 4096 May 24 21:18 linux-headers-3.8.0-22-generic
drwxr-xr-x 24 root root 4096 Jun  1 01:20 linux-headers-3.8.0-23
drwxr-xr-x  7 root root 4096 Jun  1 01:20 linux-headers-3.8.0-23-generic
sysop@1304mini:~$ 

and one subdirectory --still owned by root
> 
sysop@1304mini:~$ ls -la /usr/src/linux-headers-3.8.0-21
total 152
drwxr-xr-x  24 root root  4096 May 19 10:56 .
drwxr-xr-x   8 root root  4096 Jun  1 01:20 ..
drwxr-xr-x  30 root root  4096 May 19 10:56 arch
drwxr-xr-x   3 root root  4096 May 19 10:56 block
drwxr-xr-x   4 root root  4096 May 19 10:56 crypto
drwxr-xr-x  23 root root  4096 May 19 10:56 Documentation
drwxr-xr-x 108 root root  4096 May 19 10:56 drivers
drwxr-xr-x   2 root root  4096 May 19 10:56 firmware
drwxr-xr-x  73 root root  4096 May 19 10:56 fs
drwxr-xr-x  25 root root  4096 May 19 10:56 include
drwxr-xr-x   2 root root  4096 May 19 10:56 init
drwxr-xr-x   2 root root  4096 May 19 10:56 ipc
-rw-r--r--   1 root root  2536 Feb 18 17:58 Kbuild
-rw-r--r--   1 root root   252 Feb 18 17:58 Kconfig
drwxr-xr-x  10 root root  4096 May 19 10:56 kernel
drwxr-xr-x   9 root root  4096 May 19 10:56 lib
-rw-r--r--   1 root root 48539 May 14 17:17 Makefile
drwxr-xr-x   2 root root  4096 May 19 10:56 mm
drwxr-xr-x  55 root root  4096 May 19 10:56 net
drwxr-xr-x  13 root root  4096 May 19 10:56 samples
drwxr-xr-x  13 root root  4096 May 19 10:56 scripts
drwxr-xr-x   9 root root  4096 May 19 10:56 security
drwxr-xr-x  22 root root  4096 May 19 10:56 sound
[INDENT=2]
I do hope this helps but getting ALL the permissions back correctly -- gonna be a challenge !(but maybe not)

[/INDENT]

---

### Post by Impavidus on 2013-06-11
Yes, it's the same with me, except that I have```

ls -la /usr/scr
totaal 44
drwxrwsr-x 11 root src  4096 mei 31 12:15 .
drwxr-xr-x 10 root root 4096 jun  8 10:23 ..
drwxr-xr-x 24 root root 4096 apr  9 08:39 linux-headers-3.2.0-40
...

```I don't think it really matters. And I have a different kernel, running 12.04.

The tricky part is to remove execute permissions from all files, but keep them on directories.

---

### Post by steeldriver on 2013-06-11
I wouldn't think it's necessary to reinstall the system - it's not like you've messed up / or even /usr or /etc

It's fairly easy to chmod all the dirs to 755 and all the plain files to 644 HOWEVER at least on my system(s), there are a bunch of executable scripts that would not fit that pattern

But AFAIK /usr/src is only used for things like building kernel modules - and even then you'd only need your current kernel's - personally I'd not sweat it, change the parent dir back (it's plain root:root and mode 755 on mine fwiw) then IF you need to build any module / dkms stuff BEFORE your kernel gets upgraded anyway, then reinstall the current headers package

```
sudo apt-get install --reinstall linux-headers-$(uname -r)
```

If you want to be tidy, just uninstall all the older linux-headers packages

---

