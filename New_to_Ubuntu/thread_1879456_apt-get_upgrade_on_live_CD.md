---
title: "apt-get upgrade on live CD"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by rattskjelke on 2011-11-11
If you boot from a live CD or DVD (non-rewriteable) and then run
*sudo apt-get update* and *sudo apt-get upgrade* or tried to install a package that isn't already on the CD what would happen?
Would it actually change anything?
What if you used a USB thumb drive?

---

### Post by drs305 on 2011-11-11
You can update existing apps on the LiveCD and install new packages, but they are not persistent - they will not 'survive' a reboot of the CD.

If you wish to boot a LiveCD and make permanent changes on an existing installation already on a partition, you can 'chroot' and then run the commands. In this manner, the changes will be made to your actual Ubuntu partition (if you have installed Ubuntu).

To view one thread which describes how to 'chroot', click the 'Chroot' link in my signature line. The thread is devoted to reinstalling Grub, but the chroot procedure would apply for other operations as well (mounting the Ubuntu partition, copying the system files, and chrooting into the partition).

---

### Post by Mark Phelps on 2011-11-12
The LiveCD actually creates a RAM Disk -- disk simulated in a chuck of memory.  Any updates you do are applied to that RAM disk.  Which is why they do not survive rebooting.

So while you CAN make updates -- actually a good way to test them -- the next time you boot with the LiveCD, those updates will be gone.

---

### Post by Rubi1200 on 2011-11-12
The chroot method mentioned by drs305 can be a very effective tool when diagnosing and fixing system problems.

It is not as scary, or complicated, as it might seem.

For example, once you have a chroot into the filesystem you can do some housecleaning with the following commands:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

Let us know if you need further assistance with any of this.

---

### Post by Paqman on 2011-11-12
> **rattskjelke said:**
> 
What if you used a USB thumb drive?

Depends. If you used one of the tools for putting an Ubuntu image onto a USB stick to boot from, then it would work the same as a CD. It is possible however to boot up into an install disk/USB and choose a USB stick as the target for an install just like if you were installing to a hard drive. In that case it would be just like a hard drive install and package updates would work like normal. You'd need to use a 4GB stick for this, minimum.

---

### Post by rattskjelke on 2011-11-12
I just want to try some of the other distros without installing them
Whenever I download the latest CD/DVD they are never really current and after I install them they spend a long time installing updates. That sucks when you have a slow internet connection.

Why can't the .ISO images on the web sites be kept up to date so you don't end up downloading it twice?

---

### Post by rattskjelke on 2011-11-12
> **Paqman said:**
> Depends. If you used one of the tools for putting an Ubuntu image onto a USB stick to boot from, then it would work the same as a CD. It is possible however to boot up into an install disk/USB and choose a USB stick as the target for an install just like if you were installing to a hard drive. In that case it would be just like a hard drive install and package updates would work like normal. You'd need to use a 4GB stick for this, minimum.

I tried installing to a USB thumbdrive and it wouldn't boot but when I used UNetbootin to install the CD image with a persistent file it booted, but I wanted all the updates and I don't know if that is the same thing or if you can even do that.

---

