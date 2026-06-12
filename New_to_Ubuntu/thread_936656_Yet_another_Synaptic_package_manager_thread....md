---
title: "Yet another Synaptic package manager thread..."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by darisk on 2008-10-03
After searching and finding many threads with the following problem (which I suffer from as well):

> When i try to start Synaptic Package Manager i get this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

it seems there are many reasons as to why it happens but I haven't found one identical to mine.

So, I run dpkg config as I should (with sudo and everything) and get the following:

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

```

I tried running apt-get clean, install, update, etc... but I always get the same "dpkg interrupted" error, except when running the config as instructed...

Any ideas? It seems it's looking for /lib/modules/2.6.24-16-generic, so I tried re-installing the linux-ubuntu-modules-2.6.24-16-generic package (dunno what that means, but quoted from here: [http://ubuntuforums.org/showthread.php?t=818397](http://ubuntuforums.org/showthread.php?t=818397)) but I _always_ get the "dpkg intterupted"

Cheers guys!

---

### Post by iaculallad on 2008-10-03
If you're not using the -16 kernel, try removing removing the postrm scripts that prevents the package from being removed.

```
sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm
sudo rm /var/lib/dpkg/info/linux-backports-modules-2.6.24-16-generic.postrm
sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic
sudo apt-get remove linux-backports-modules-2.6.24-16-generic

```

---

### Post by darisk on 2008-10-03
Unfortunately that doesn't work either:

$ sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm
rm: cannot remove `/var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm': No such file or directory

I checked to see what was wrong and those files are indeed missing...

HOWEVER there is a '...24-12-generic.postrm' and '.list' file. Is it safe to remove that? There are no linux-backports files either...


EDIT: The 'linux-ubuntu-modules-2.6.24-12-generic.list' file is 0kb, and the only -16 files are: 
'linux-headers; .list, .md5sums, -generic.list, -generic.md5sums, -generic.postinst. 

these are also in 24-19. The rest is the above mentioned -12 ones, and a pair of 'restricted-modules -12' ones.

I have a feeling I'm missing some fundamental files...

---

### Post by darisk on 2008-10-06
No ideas? :confused:

---

