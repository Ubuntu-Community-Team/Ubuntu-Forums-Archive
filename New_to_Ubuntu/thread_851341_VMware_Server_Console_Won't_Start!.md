---
title: "VMware Server Console Won't Start!"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by revun096 on 2008-07-06
Hello.

VMware Server Console doesn't start!  I run 'vmware' in the terminal, and it says:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

I then installed almost every gcc package there is!  What do I do?

---

### Post by lamego on 2008-07-06
Try the following:
[http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

---

### Post by dicecca112 on 2008-07-06
specifically just copy and paste this into the terminal

```
sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

---

### Post by mustava on 2008-07-19
I'v got the same problem, but those two lines don't fix it for me.
Vmware starts to load (icon on bottom bar) then after about 5 secs disappears

Thanks Mustava

---

### Post by dahaggis on 2008-07-24
worked a treat, thanks...

---

### Post by tinny on 2008-07-24
Go with this tutorial, it is constantly being updated as new versions of VMWare become available.

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

VMWare server 1.0.5 was a problem, it needed a patch to be applied in order to work. But now VMWare server 1.0.6 is available and this patch is no longer needed. GO WITH 1.0.6!

---

### Post by Greencoat1982 on 2008-08-03
I get the same problem with the console not starting but with the box disappearing, when i try to run 'vmware' in terminal I get this error message: process 6817: Attempt to remove filter function 0xb6abfcd0 user data 0x88bc7c8, but no such filter has been added. Then it just sits at idle.

Any pointers in the right direction?

---

### Post by casperfelix on 2008-08-14
Worked for me dicecca112 - in my 8.04 64bit install...........

---

### Post by Jole on 2008-09-04
I instaled the VMware Server 1.0.6 with no problem..folowing [this]("http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04") tutorial and I created a VM but it won't start. The console goes black for a 5 sec and then nothing. It doesn't start, nothing....Can anyone help with this..

Ubuntu 8.04 running...


[COLOR="DarkOrange"]Update:[/COLOR] The problem was that my VM was on a NTFS partition. I moved it to a ext3 partition and everything worked fine. There is a workaround for this problem with the NTSF partitions. Here's the [link]("http://sudan.ubuntuforums.com/showthread.php?t=684615").

---

### Post by Ocelaris on 2008-09-16
ditto worked for me, just needed those symlinks, running x64 apparently needed those links to the compiler.

---

