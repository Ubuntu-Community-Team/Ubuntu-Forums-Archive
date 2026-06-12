---
title: "2 different version of kernel!!! how to delete one"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by KingdomHeart on 2008-11-02
I updated ubuntu and now I have 2 different version of the kernel. They are:
ubuntu 8.04.1 kernel 2.6.24-21
ubuntu 8.04.1 kernel 2.6.24-19
I want to delete kernel 19. How can I do that?

---

### Post by handydan918 on 2008-11-02
> **KingdomHeart said:**
> I updated ubuntu and now I have 2 different version of the kernel. They are:
ubuntu 8.04.1 kernel 2.6.24-21
ubuntu 8.04.1 kernel 2.6.24-19
I want to delete kernel 19. How can I do that?

Well, first of all, why do you want to do that?

Once you have satisfied yourself that deleting a kernel tat takes up virtually no room is the best course of action, simply ```
sudo rm /path/to/kernel
```

And if you can't figure that out, you should probably read more before fiddling with kernels.

---

### Post by brandoncolorado on 2008-11-02
> **KingdomHeart said:**
> I updated ubuntu and now I have 2 different version of the kernel. They are:
ubuntu 8.04.1 kernel 2.6.24-21
ubuntu 8.04.1 kernel 2.6.24-19
I want to delete kernel 19. How can I do that?

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by coolbrook on 2008-11-02
On a couple of occasions I've resorted to logging into the old kernel to resolve issues with the new.  It's a good idea for you to keep -19 if -21 is your most recent.

---

### Post by zvacet on 2008-11-03
As **coolbrook** said it is good idea to have two kernels,just in case.But if you want to remove it go to the synaptic and in search box type **linux-image** and delete one you want.

---

### Post by KingdomHeart on 2008-11-03
Thanks. I will definitely read more on this

---

### Post by drs305 on 2008-11-03
> **KingdomHeart said:**
> Thanks. I will definitely read more on this

There are a few issues to deal with regarding removing kernels. Editing grub's boot menu can hide them without removing them from your system, whereas remvoing them via synaptic will take them off the menu as well as off your disk.

If you elect to modify your grub setting, here is a link to StartUp-Manager use, which will allow you to safely modify grub settings via a gui-based app. Section 5 discusses removing kernels from your system.

[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by akiratheoni on 2008-11-03
Generally I keep the multiple kernels until I am sure the newer one works. On my EeePC I installed Ubuntu on it and updated; the newer kernel didn't work, but the older one did. So I stayed on the older one until I was able to download and correct the problem in the newer one. Just an example of why you might want to keep your older kernels.

---

### Post by Paqman on 2008-11-03
There's a few different ways:

[list]
[*] If using Intrepid, use the "cruft remover" to get rid of the old kernels.
[*] On any version, use Synaptic to remove the kernels (linux-image packages), both these methods also clean up the Grub menu automatically.
[*] Use startupmanager to clean up /boot/grub/menu.lst. Very good tool.
[*] Edit /boot/grub/menu.lst manually. This is the old-school way to do it, and like startupmanager doesn't remove the actual kernels.
[/list]

---

### Post by philinux on 2008-11-03
> **Paqman said:**
> There's a few different ways:

[LIST]
[*] If using Intrepid, use the "cruft remover" to get rid of the old kernels.
[*] On any version, use Synaptic to remove the kernels (linux-image packages), both these methods also clean up the Grub menu automatically.
[*] Use startupmanager to clean up /boot/grub/menu.lst. Very good tool.
[*] Edit /boot/grub/menu.lst manually. This is the old-school way to do it, and like startupmanager doesn't remove the actual kernels.
[/LIST]


The cruft remover is borked and was removed as a default install for the final release. It still is in synaptic though.

---

### Post by Paqman on 2008-11-03
> **philinux said:**
> The cruft remover is borked and was removed as a default install for the final release. It still is in synaptic though.

Cheers, i'll stop using and recommending it then. What's the nature of the borkage?

---

