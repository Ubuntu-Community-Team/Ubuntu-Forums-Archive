---
title: "DPKG issue"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Taters on 2008-10-01
When I was updating my fresh install of Ubuntu from 8.04 to 8.04.1, I received this error:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report./QUOTE]

So, the next natural step was to run this:

[QUOTE]sudo dpkg --configure -a


Yet, the information I got back was far more interesting:

> Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.28[size=2])[/size] ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1



I am rather surprised. My / directory is a 60gig EXT3 partition, I know a little update couldn't consume this much space. 

I checked to see if perhaps Ubuntu was mis-reading the partition, but the Disk Analyzer states otherwise:

[[IMG]http://img239.imageshack.us/img239/4836/screenshotjw6.th.png[/IMG]](http://img239.imageshack.us/my.php?image=screenshotjw6.png)

(According to the Gparted live-cd)
[IMG]http://i204.photobucket.com/albums/bb211/tnemcod/gparted.jpg[/IMG]

Also, whenever I turn off/put the computer in hibernate I receive errors about daemons failing to close.

(On a side note, is it possible to manually add daemons in Ubuntu? I miss that convenience coming from Arch.)


I'm really lost. DPKG has failed me before, but I was always able to fix it. Google/other posts haven't shown any similar issues...

What should I do?

---

### Post by shifty_powers on 2008-10-01
according to that picture, your / directory is 2.7 gig....

---

### Post by Taters on 2008-10-01
> **shifty_powers said:**
> according to that picture, your / directory is 2.7 gig....

When I boot into gparted, It says the / directory is 60gb. Also, it states I have 261.5gb free.

---

### Post by shifty_powers on 2008-10-01
are you sure the / mount point was 60gb? because / is definitely not 60gb according to ubuntu there...

why there is the discrepancy, couldn't say...

maybe you could boot into gparted and post a screenshot?

---

### Post by Taters on 2008-10-01
> **shifty_powers said:**
> are you sure the / mount point was 60gb? because / is definitely not 60gb according to ubuntu there...

why there is the discrepancy, couldn't say...

maybe you could boot into gparted and post a screenshot?


[IMG]http://i204.photobucket.com/albums/bb211/tnemcod/gparted.jpg[/IMG]


/ SHOULD be /dev/sda6

---

### Post by shifty_powers on 2008-10-01
ok, try this

```
sudo apt-get install xdiskusage
```

run it from command line

```
xdiskusage
```

pick / and post a screenie...

---

### Post by Taters on 2008-10-01
I received the same error.

---

### Post by shifty_powers on 2008-10-01
interesting. well i checked mine with xusage and got the right size...

gonna have to pass onto someone more experienced here, as i really don't know why it is...

---

### Post by houbysoft.xf.cz on 2008-10-01
Hi, most likely, you have more than one partition on your harddrive. You have a separate partition for "/" and "/boot". The /boot partition is probably too small. Just make it bigger, run the dpkg again, it should work.

---

### Post by houbysoft.xf.cz on 2008-10-01
Btw, could you post your fdisk info?

---

### Post by houbysoft.xf.cz on 2008-10-01
Oh, I did not see the picture. It seems clear to me. /dev/sda2 probably is your boot partition, and it is very small. Just make it bigger (mine is ~100 MB)

---

### Post by shifty_powers on 2008-10-01
doh!

lloking at that, the update was trying to write to the /boot partition, (kernel update), and it only has 1 meg space left...

---

