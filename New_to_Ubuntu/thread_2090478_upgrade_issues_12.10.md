---
title: "upgrade issues 12.10"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by Jimmy Francis on 2012-12-02
Hi, I am relatively new to Ubuntu and recently ran into an issue while performing an upgrade. During upgrade to Ubuntu 12.10, the upgrade froze at: installing new upgrade
  I re-booted the computer, and now I get an error message at startup:
```
 starting up&#8230;
untall: /lib/x86_64-linux-gnu/libc.so.6: version &#8216;GLIBC_2.14&#8217; not found (req by /lib/libply.so.2)
error mounting system.
maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system 
```  

I tried: ```
sudo apt-get upgrade
```       and got the following message:```

Not using locking for read only lock file /var/lib/dpkg/lock
dpkg was interrupted, you must manually run &#8216;sudo dpkg &#8211;-configure &#8211;a&#8217; to correct the problem   


```Not too sure what that means. Any idea how I can get the system to boot again? 
Thanks

---

### Post by Hank_The_Dog on 2012-12-02
Re install from fresh .iso

---

### Post by lisati on 2012-12-02
Before you go anywhere near doing a fresh install, are you able to open a terminal and run the following?
```
sudo dpkg &#8211;-configure &#8211;a
```
You might need to select recovery mode from the grub menu to be able to do this.

---

### Post by Jimmy Francis on 2012-12-02
I tried: sudo dpkg --configure -a

and got this message: dpkg: error: unable to access dpkg status area: Read-only file system

---

