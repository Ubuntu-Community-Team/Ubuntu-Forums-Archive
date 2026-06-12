---
title: "sudo apt-get clean problem"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by omart on 2013-02-25
On running update manager it reports that boot is full and tells me to run sudo apt-get clean from a command line to delete old packages. I've done this with no results. Is there some other way to delete these packages?

---

### Post by ajgreeny on 2013-02-25
You probably need to remove old kernels.

The command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```will show all kernels on your system, and everything else that shows in the grub menu (even if you don't see that menu at boot)

The easiest way to remove old kernels, I think, is to install and use synaptic which let's you search for the kernel packages by number, eg for Precise 12.04, **linux-image-3.2.0-36** and you can then remove all of them except the two most recent, ie the one you're using and one previous as a backup.

---

### Post by omart on 2013-02-25
Sorry. It's not old kernel problem.

---

### Post by ajgreeny on 2013-02-25
> **omart said:**
> Sorry. It's not old kernel problem.
So how is it that /boot is full?  Did you mean **boot** or should you have said **root**?

If **sudo apt-get clean** did not show an error then it worked, and there should be no .deb packages left in **/var/cache/apt/archives**.

---

### Post by omart on 2013-03-18
Sudo apt-get clean or autoclean does not remove old pacage, what has  to be done to remove them?

---

### Post by plucky on 2013-03-18
> **omart said:**
> Sudo apt-get clean or autoclean does not remove old pacage, what has  to be done to remove them?

All "sudo apt-get clean" does is delete all the downloaded .deb files in /var/cache/apt/archives.

Try ```
sudo apt-get autoremove
``` which will remove all obsolete packages.

Good Luck

---

### Post by omart on 2013-03-18
Not working. Looks like it needs more space to work than is available. Is it possible to delete from terminal?

---

### Post by ibjsb4 on 2013-03-18
Hi omart, welcome to the forums :)

You can also take a look here for more ways.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+obsolete+packages&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+obsolete+packages&sa=Search&cof=FORID:9)

---

### Post by omart on 2013-03-18
Finally did it with synaptic package manager.

---

### Post by oldos2er on 2013-03-18
Threads merged. Please don't start more than one thread per issue, it's confusing and it dilutes community effort.

---

