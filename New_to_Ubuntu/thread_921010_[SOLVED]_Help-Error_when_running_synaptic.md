---
title: "[SOLVED] Help-Error when running synaptic"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by c2rjay on 2008-09-15
I'm trying to run synaptic and then i get this error message. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running dpkg --configure -a in the terminal but it says i need superuser privileges. Is there a way to actually configure dpkg so i can run synaptic. And what is causing the error?

I am totally new to linux, so if the problem can be solved simply that would be great. 

-Ray

---

### Post by howefield on 2008-09-15
prefix with sudo eg,

sudo dpkg --configure -a

---

### Post by c2rjay on 2008-09-15
> **howefield said:**
> prefix with sudo eg,

sudo dpkg --configure -a

Hey howefield, thanks for the help, but when i type it in the terminal i get this:

<Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135>

any solutions?

---

### Post by gali98 on 2008-09-15
Wow libc6?
hmmm... can you post the output of :

```
df
```

also just try the command again to see if maybe it works on the second try (you never know...)
Can you think of the last thing you might have installed with Synaptic or with Add/Remove Programs, or if you may have shutdown during an update or installing something?

Kory

---

### Post by c2rjay on 2008-09-16
Well i can't try it right now, im at work. Is libc6 a major problem?

Also i remember i installed Virtual Box two days ago using the Add/Remove Programs in Gutsy. Maybe Virtualbox messed up the system some how i don't know? Also if i try to install something on Add/Remove Programs now it can't run, saying failed installation, run "dpkg --configure -a"

---

### Post by gali98 on 2008-09-16
Well libc6 is one of the basic librarys. I think most everything uses it:(

I also know virtualbox has been known to cause a few problems before.
And you are on Gusty?

Kory

---

### Post by philinux on 2008-09-16
use this.

sudo apt-get -f install

If this fails run

sudo apt-get update && sudo apt-get upgrade

then run the above again.

---

### Post by c2rjay on 2008-09-16
gali98, yea i'm running gutsy. Man, if i knew i would have problems running virtualbox i would have never installed it. 

> **philinux said:**
> use this.

sudo apt-get -f install

If this fails run

sudo apt-get update && sudo apt-get upgrade

then run the above again.

yea ill run it but i'm at work, and the computer is at home. So when i try it, i'll let you guys know.

thanks for the help

---

### Post by c2rjay on 2008-09-16
ok so this is what i got with running df
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             18381960  10257244   7190940  59% /
varrun                  513688        96    513592   1% /var/run
varlock                 513688         0    513688   0% /var/lock
udev                    513688        64    513624   1% /dev
devshm                  513688         0    513688   0% /dev/shm
lrm                     513688     34696    478992   7% /lib/modules/2.6.22-15-generic/volatile

```

and i can't run 
```
sudo apt-get -f install

```

or 

```
sudo apt-get update && sudo apt-get upgrade

```

it tells me to manually run 'dpkg --configure -a

---

### Post by niglet101 on 2008-09-16
try this...

[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by gali98 on 2008-09-17
Okay I may have found something...

please do the following commands..

cd ~/Desktop

sudo strace ldconfig > strace.txt

then upload that the file on your desktop named strace.txt so I can look through it..
If you think you are up to it, you can look through it yourself using the post:
[http://ubuntuforums.org/showthread.php?p=4040893](http://ubuntuforums.org/showthread.php?p=4040893)
but if you are new, you will probably need my or someone else's help.

Kory

---

### Post by c2rjay on 2008-09-17
alright kory this is what i got after running sudo strace ldconfig>strace/txt

```
execve("/sbin/ldconfig", ["ldconfig"], [/* 41 vars */]) = 0
brk(0)                                  = 0x805f000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f29000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59045, ...}) = 0
mmap2(NULL, 59045, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f1a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260a\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1339816, ...}) = 0
mmap2(NULL, 1349136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7dd0000
mmap2(0xb7f14000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x143) = 0xb7f14000
mmap2(0xb7f17000, 9744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f17000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7dcf000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7dcf6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f14000, 4096, PROT_READ)   = 0
munmap(0xb7f1a000, 59045)               = 0
getpid()                                = 6634
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
geteuid32()                             = 0
brk(0)                                  = 0x805f000
brk(0x8080000)                          = 0x8080000
getppid()                               = 6631
stat64("/home/ray/Desktop", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/sbin/ldconfig", O_RDONLY)        = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x80551b0, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0
read(10, "#!/bin/sh\n\nif  test $# = 0\t\t\t\t\t\t"..., 8192) = 465
execve("/sbin/ldconfig.real", ["/sbin/ldconfig.real"], [/* 41 vars */]) = 0
uname({sys="Linux", node="ray-laptop", ...}) = 0
brk(0)                                  = 0x80dd000
brk(0x80ddcb0)                          = 0x80ddcb0
set_thread_area({entry_number:-1 -> 6, base_addr:0x80dd830, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
brk(0x80fecb0)                          = 0x80fecb0
brk(0x80ff000)                          = 0x80ff000
--- SIGBUS (Bus error) @ 0 (0) ---
+++ killed by SIGBUS (core dumped) +++
Process 6634 detached

```

So what is the next step? i checked the link you gave me so i have to run the following commands? I'm not really sure what commands to write down, maybe you can help me out.

Thanks

---

### Post by gali98 on 2008-09-17
Okay sorry, both of us messed up the commands :)

okay if you would, reboot.
Then run:

sudo dpkg --configure -a

cd ~/Desktop

sudo strace ldconfig > strace.txt


last time you did strace/txt. Make sure it is strace.txt :)

then upload the file named strace.txt on your desktop.

and post the output of all those commands.

The most important thing is to upload that file.
It has everything that I need to help you. Sorry for the runaround!
Kory

---

### Post by c2rjay on 2008-09-18
hey don't worry about it
so this is what i got when running the commands but i cannot upload the strace file. It says failed up load, and when i check the size of the file, its 0 bytes. And when i open the file, theres nothing in it, no code. 

heres whats on the terminal

```
ray@ray-laptop:~$ sudo dpkg --configure -a
[sudo] password for ray:
Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
ray@ray-laptop:~$ cd ~/Desktop
ray@ray-laptop:~/Desktop$ sudo strace ldconfig > strace.txt
execve("/sbin/ldconfig", ["ldconfig"], [/* 41 vars */]) = 0
brk(0)                                  = 0x805f000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f29000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59045, ...}) = 0
mmap2(NULL, 59045, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f1a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260a\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1339816, ...}) = 0
mmap2(NULL, 1349136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7dd0000
mmap2(0xb7f14000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x143) = 0xb7f14000
mmap2(0xb7f17000, 9744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f17000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7dcf000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7dcf6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f14000, 4096, PROT_READ)   = 0
munmap(0xb7f1a000, 59045)               = 0
getpid()                                = 6219
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
geteuid32()                             = 0
brk(0)                                  = 0x805f000
brk(0x8080000)                          = 0x8080000
getppid()                               = 6218
stat64("/home/ray/Desktop", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/sbin/ldconfig", O_RDONLY)        = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x80551b0, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0
read(10, "#!/bin/sh\n\nif  test $# = 0\t\t\t\t\t\t"..., 8192) = 465
execve("/sbin/ldconfig.real", ["/sbin/ldconfig.real"], [/* 41 vars */]) = 0
uname({sys="Linux", node="ray-laptop", ...}) = 0
brk(0)                                  = 0x80dd000
brk(0x80ddcb0)                          = 0x80ddcb0
set_thread_area({entry_number:-1 -> 6, base_addr:0x80dd830, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
brk(0x80fecb0)                          = 0x80fecb0
brk(0x80ff000)                          = 0x80ff000
--- SIGBUS (Bus error) @ 0 (0) ---
+++ killed by SIGBUS (core dumped) +++
Process 6219 detached
ray@ray-laptop:~/Desktop$ 


```

---

### Post by gali98 on 2008-09-18
Okay, I have a couple things to try...

first do:

cd ~/Desktop

wget [http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-i686_2.7-10ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-i686_2.7-10ubuntu3_i386.deb)

sudo dpkg -i libc6-i686_2.7-10ubuntu3_i386.deb

and see if that works....

even if it does not work (but also if it does)

run 

ldconfig

then post all output from those commands....

Kory

---

### Post by c2rjay on 2008-09-18
kory this is what i got, seems like the link you gave me doesn't work. 

```
ray@ray-laptop:~$ cd ~/Desktop
ray@ray-laptop:~/Desktop$ wget http://mirrors.kernel.org/ubuntu/poo...untu3_i386.deb
--22:39:53--  http://mirrors.kernel.org/ubuntu/poo...untu3_i386.deb
           => `poo...untu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:40:04 ERROR 404: Not Found.

ray@ray-laptop:~/Desktop$ ldconfig
Bus error (core dumped)

```

---

### Post by c2rjay on 2008-09-18
kory i think i got it. I kinda understand what you wanted me to do. So i installed the package from another link. and Synaptic works. Thanks.

---

### Post by gali98 on 2008-09-19
Great!!!
I'm glad we got it working again...
It was an interesting way, but it worked...
Kory

---

