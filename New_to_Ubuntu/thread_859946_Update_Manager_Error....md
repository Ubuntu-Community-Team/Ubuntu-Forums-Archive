---
title: "Update Manager Error..."
date: 2008-07-15
forum: New to Ubuntu
---

### Post by kss_me_1s on 2008-07-15
Total ubuntu/linux newbie here, getting this error when trying to download/install updates....thx in advance for any help ;)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2008-07-15
> **kss_me_1s said:**
> Total ubuntu/linux newbie here, getting this error when trying to download/install updates....thx in advance for any help ;)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

On your terminal:

```
sudo dpkg --configure -a
```

You just have to insert **sudo** to get the privilege.

---

### Post by kss_me_1s on 2008-07-15
thank you so much for ur help! any reason why this worked perfectly before....how would this have been changed? i am the only user on this comp. thanks again

---

### Post by iaculallad on 2008-07-15
> **kss_me_1s said:**
> thank you so much for ur help! any reason why this worked perfectly before....how would this have been changed? i am the only user on this comp. thanks again

If a user sees that message from APT it means the last time
they ran dpkg it died horribly while processing installations.
The dpkg utility was designed with the intent that it would never leave the
updates directory dirty.

---

### Post by Mr_Lazy on 2008-07-15
Hi,

I have exactly the same problem, but when I run the command:
sudo dpkg --configure -a

I get the error:
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 linux-image-2.6.24-19-generic


How do I do the reinstall? I don't even know the name of the damaged package.

Thanks,
Lazy

---

### Post by Mr_Lazy on 2008-07-16
OK, it seems to have fixed itself :). After shutting down, leaving it over night, the update manager now updates with no issues. Spooky.

L.

---

### Post by Celeb on 2008-07-16
That's becouse the damaged pkg was in your /tmp. When you got those kind of trouble reboot, unless you want to get dirty in the command line and fix it your self.


Celeb

Vi is not death...

---

