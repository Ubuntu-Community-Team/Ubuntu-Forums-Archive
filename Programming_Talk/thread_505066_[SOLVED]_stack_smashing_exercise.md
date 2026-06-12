---
title: "[SOLVED] stack smashing exercise"
date: 2007-07-19
forum: Programming Talk
---

### Post by PastorTaz on 2007-07-19
I'm working on a stack smashing exercise for the CEPT certification.  The problem that I'm having is that I need to use a distro that does not have stack smashing protection and the company suggested using RedHat 9 with kernel version 2.4.20-8.  I've tried that and there are no compilers installed and installing one is turning out to be a bear.  I can untar, but when I try to ./confiture it gives this error

> [root@localhost gcc-3.3]# ./configure
Configuring for a i686-pc-linux-gnu host.
Created "Makefile" in /root/gcc-3.3 using "mt-frag"
./configure: line 8: cc: command not found
*** The command 'cc -o conftest -g   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.


I like Ubuntu, but it has stack smashing protection.  I've tried to compile programs with gcc-3.3 and that worked for some, but it is not working for all.  I'm currently running Feisty both native and VMWare.

Can anybody either help me with the compiler issue in RH9 or suggest a flavor of Ubuntu that meets the criteria?

Thanks,

---

### Post by leibowitz on 2007-07-19
I can't help you but trying to figure out how do you think you can compile a compiler without any compiler installed?

You need to install some kind of compiler on your Red Hat box. Try to install it with official packages (yum is good tool for this task). 

It should be easy as "yum install gcc-3.0" but I suppose it may be harder than this.

Then you will be able to use gcc for what you need.

---

### Post by duff on 2007-07-19
With Ubuntu, try compiling with the "-fno-stack-protector" flag.

---

### Post by PastorTaz on 2007-07-19
I tried the yum and it is not installed.  Here is a list of my /bin...

-------------------------------------------------------------------------------------------------
[root@localhost bin]# ls
arch           cut            gawk      mkdir          rmdir      true
ash            date           grep      mknod          rpm        umount
ash.static     dd             gtar      mktemp         rvi        uname
aumix-minimal  df             gunzip    more           rview      unicode_start
awk            dmesg          gzip      mount          sed        unicode_stop
basename       dnsdomainname  hostname  mt             setfont    unlink
bash           doexec         igawk     mv             setserial  usleep
bash2          domainname     ipcalc    netstat        sh         vi
bsh            dumpkeys       kbd_mode  nice           sleep      view
cat            echo           kill      nisdomainname  sort       ypdomainname
chgrp          ed             link      pgawk          stty       zcat
chmod          egrep          ln        ping           su
chown          env            loadkeys  ps             sync
cp             ex             login     pwd            tar
cpio           false          ls        red            tcsh
csh            fgrep          mail      rm             touch
-----------------------------------------------------------------------------------------------------------

I'm starting to wonder if I somehow get a bad RH9 distro...  

I'll try the -fno-stack-protector and see how that works. 

What flavor of Ubuntu has kernel version 2.4.20-8?

---

### Post by leibowitz on 2007-07-20
> What flavor of Ubuntu has kernel version 2.4.20-8?

None I suppose.


Note that if you have rpm installed on your red hat box, it's easy to download and install yum. Of course easy means "when you know how to do it". And sorry, I don't have a Red Hat box to try this at home.

---

