---
title: "Crash and Lock errors"
date: 2020-02-22
forum: New to Ubuntu
---

### Post by freebornman on 2020-02-22
Hello All,

New Ubuntu user here and I would appreciate any help for the following: while trying to install Vivaldi and Node today, I kept getting multiple error messages such as "E: could not get lock /var/lib/dpkg/lock",  "unable to lock the administration directory...is another process using it" and "dpkg was interrupted, you must manually run sudo dpkg...." I was also getting an error report whenever I powered up but that seems to have been corrected. After finding and using a few potential remedies I have found myself in a loop and am currently stalled with the following message:

~$ ls -l /var/lock/
total 4
-rw-r--r-- 1 root     root     22 Feb 22 20:48 asound.state.lock
drwxr-xr-x 2 root     root     40 Feb 22 20:48 subsys
drwxr-xr-x 2 whoopsie whoopsie 60 Feb 22 20:49 whoopsie

Any suggestions?

Many thanks,

John

---

### Post by him610 on 2020-02-23
> E: could not get lock /var/lib/dpkg/lock, unable to lock the administration directory...is another process using it
I believe this message normally indicates your system is in the process of performing an auto-update, maybe security. Whenever happens to me on occasion, I get another cup of coffee and try again later.

---

### Post by CelticWarrior on 2020-02-23
> **him610 said:**
> I believe this message normally indicates your system is in the process of performing an auto-update, maybe security. Whenever happens to me on occasion, I get another cup of coffee and try again later.

+1

Also > "dpkg was interrupted, you must manually run sudo dpkg...."

Yes, you must do that before installing any new software:
```
sudo dpkg --configure -a
```

And Vivaldi's preferred installer is a .deb file that can be opened with Ubuntu Software, the app store app. Opening with it would have shown the locked database due to other process running, likely updates, waited for the process to finish and then install your .deb. (Any other graphical installer - GDebi, Synaptic, etc. - would do the same). Unless you're running a server without desktop environment there's no reason not to use the GUI tools available, especially for trivial tasks. It's good to know the commands as well but for the situation you described GUI tools are perfectly fine and advantageous due to their capability to enqueue installations.

---

