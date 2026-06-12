---
title: "Error when using update manager"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by TwinMomma on 2008-06-17
Hi,
I'm an extremely new user to Ubuntu when it comes to more than just using the operating system.  I've been doing the suggested updates that pop up on my status bar and lately I've been getting the following errors.

E: linux-image-2.6.24-19-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-19-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-19-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

It seems to be affecting my ability to install programs from synaptic package manager as well.

Any help?

TwinMomma

---

### Post by avtolle on 2008-06-17
Would you please post the output of ```
df -h
```

---

### Post by alienexplorers on 2008-06-17
try typing in terminal:
> sudo dpkg -configure -a

---

### Post by avtolle on 2008-06-17
That last command from the terminal ought to be```
sudo dpkg --configure -a
```

---

### Post by alienexplorers on 2008-06-17
Thanks for correcting my error.  I have to be the worst two finger typer.

---

### Post by avtolle on 2008-06-17
No problem; I'm not that great at it myself, and as a result have to make corrections all the time.

@Twinmomma: Just reread your first post. To get to the terminal, click on Applications, then choose Accessories at the menu, then select Terminal. At the prompt, type in either the command I posted or, if you prefer, the "corrected" one that alienexplorers posted. Then hit return. It will then ask you for your password, type in the password you use to log on (there will be no visual feedback, that's how it is set up to work), hit Enter (return, whatever your keyboard says). You will then see some visual feedback, whether just a return to the command prompt, or some other information. Post your questions after that.

---

### Post by TwinMomma on 2008-06-17
here's what df -h gives me:


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              55G   14G   42G  24% /
varrun                248M  236K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   44K  248M   1% /dev
devshm                248M   12K  248M   1% /dev/shm
lrm                   248M   38M  210M  16% /lib/modules/2.6.24-18-generic/volatile
/dev/sda1              96M   96M     0 100% /boot

---

### Post by TwinMomma on 2008-06-17
and here's what sudo dpkg --configure -a gives:

Setting up linux-image-2.6.24-19-generic (2.6.24-19.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

---

### Post by avtolle on 2008-06-17
> **TwinMomma said:**
> here's what df -h gives me:


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              55G   14G   42G  24% /
varrun                248M  236K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   44K  248M   1% /dev
devshm                248M   12K  248M   1% /dev/shm
lrm                   248M   38M  210M  16% /lib/modules/2.6.24-18-generic/volatile
/dev/sda1              96M   96M     0 100% /boot
That's what I thought; your boot partition is full. Quick and dirty "fix", delete the oldest kernel from it, and try to run the updates again. The real "fix" is to make this partition larger, but let's not worry about that right now.

---

### Post by avtolle on 2008-06-17
A bit of explanation on why the /boot partition is full; each kernel update, with the associated files, takes ~20 mb (sometimes a bit more, sometimes a bit less) space. Older kernels are not automatically deleted on update, thus it is necessary to either a)delete the oldest kernel before updating to a newer kernel, or b) resizing the /boot partition to enlarge it.

---

### Post by mikebravo on 2008-06-17
Avtolle,
Thanks for this info, I have the same problem. wish I had known this a few months ago, I could have given it a 2 gig boot partition but nooo, everything I read said how few resources Linux needed so I skimped. Please tell me where to find the old kernels and how to recognize the oldest, and how to delete it. Please use noob speak.  

Would also like to be pointed toward a tutorial on non destructive partition resizing. 

Mike

---

### Post by avtolle on 2008-06-17
For removal of old kernels, the easiest way (if you are truly a "noob" as you say) is to go to Synaptic to remove them completely. The oldest ones have the lower numbers after their description. Let me take a look for a moment, and then I'll be back with hopefully better, more clear, direction.

As to "non destructive" partitioning, well, I guess I've been doing this so long (only a bit >2 years on Ubuntu and Linux) that I really don't know of a tutorial. In general, however, you need to get a Live CD, be it an Ubuntu one or one from Gparted (don't have a link right now to their web site), and boot it up. You would then, if using the Ubuntu Live CD, hit Alt+F2, and at the box, type in```
gksudo gparted
``` which will start the gparted GUI. Find your boot partition, be sure it is unmounted, and see if you can resize it. Here's where it may get a bit awkward. In Linux, you can only add or subtract space from the end of the partition, so if there's another partition "right next door", you'll not be able to resize to make it larger. Anyway, take a look, ask questions, etc., and I'll be back in a bit.

---

### Post by avtolle on 2008-06-17
Back. Go to Synaptic, do a search for "linux-image" (w/o the quotation marks). Wait a bit, and you should be presented with a list of possible candidates. Mark the older one or ones for complete removal, e.g., those ending with something less than .18, for example. After marking, Synaptic will likely also want to mark some of the associated files; accept this. Then, once all the marking is done, hit "apply", and give it a bit of time to work. When you are back at the general Synaptic screen, it has done its thing. Be aware that if you are dual booting, there is likely to be a need to edit your Grub file to remove references to the older kernels that were removed. There are several threads on the forum about this procedure, and, as I don't dual boot, I've not paid a lot of attention to them.

EDIT: Forgot this, which may also help. Once the older kernel(s) are deleted, go to the terminal and do this```
sudo apt-get clean
``` which will clear the cache. I just did this after removing a very old kernel from a prior installation, and picked up 0.1 GB space.

---

### Post by avtolle on 2008-06-17
@mikebravo, [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) while discussing how to create a separate /home partition provides instructions on post-installation partitioning resizing as a part of it, which I have found to be generally understandable and, BTW, a very good guide to the techniques which are generally applicable to post-install partitioning actions. HTH.

---

### Post by TwinMomma on 2008-06-17
Thanks for all the help guys.  My husband is helping me to remove the oldest kernel and free up some space since I don't want to accidentally make my computer unusable.

---

### Post by avtolle on 2008-06-17
> **TwinMomma said:**
> Thanks for all the help guys.  My husband is helping me to remove the oldest kernel and free up some space since I don't want to accidentally make my computer unusable.
Good luck.

---

### Post by mikebravo on 2008-06-19
Take noob observations with a grain of salt, but it seemed to me like it is necessary to delete old images one at a time starting with the oldest one. I started by trying to do them all at once and got an error message that I can not remember now.  All is well that ends well, I now have only version 2.6.24-19 and some room for more on my boot partition.

A couple of questions occur to me, first since I do not have to log in as administrator to use Synaptic package manager, does that mean that Linux would save me from myself if I tried to delete the currently running image?  and second,what is the difference between "mark for removal" and "mark for complete removal"? In the later case it said something about including configuration files. Naturally, as a noob I have not intentionally done any kernel configuration, but the larger question is, for what programs are configurations carried over into updated versions and for what programs are configurations flushed with the old program. I was faced with this choice when I updated from Gutsy to Hardy and said to myself, what the hell, lets go for the new.

---

