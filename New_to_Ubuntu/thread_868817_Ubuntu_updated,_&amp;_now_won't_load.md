---
title: "Ubuntu updated, &amp; now won't load"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Al-Saeed on 2008-07-24
I'm new to the world of Linux. I've got a recent installation of Ubuntu 8.04 LTS Desktop Edition. Everything seemed to be running nicely. Until today, when I got this alert message telling me that I need to update some stuff. I've had this happen before a few times, and I did as I normally do, which is to update whatever Ubuntu want's to update. However in this instance I was told that my laptop needs to be restarted, and it's never loaded up again after that. It only goes as far as the black starting up screen, and then switches off completely.

I've tried booting from the disc, and even there it'll just switch off. I don't really want to go back to windows, but if it's not working then I really don't have any choice.

Is there any way I could get this fixed?

Thanks

---

### Post by philinux on 2008-07-24
Reboot and press esc when you see the grub menu.

Choose a previous kernel see if that works.

---

### Post by Al-Saeed on 2008-07-24
Thank you so much Phil, I've now got it running on a previous Kernel:

ubuntu 8.04.1, kernel 2.6.24-20-generic [COLOR="Red"][Not Working][/COLOR]
ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode) [COLOR="Red"][Not Working][/COLOR]
ubuntu 8.04.1, kernel 2.6.24-19-generic [COLOR="Red"][Working][/COLOR]
ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
ubuntu 8.04.1, kernel 2.6.24-16-generic
ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)

I do have one problem though, every time I switch on my laptop I have to select the previous kernel. Is there a way to permanently set it up so it automatically loads with the kernel that actually works?

My other concern is why has this happened? And will it be a cause for concern in the future when new kernels are released?

I do appreciate your help. Thanks again.

Kind regards

---

### Post by stevoo on 2008-07-24
i installed my self .20 just aminute ago. havent restarted yet, so i have no idea if i have the same problem :)

What you can try is to remove the installed newer one from the synaptic restart, and try and re install it. 
See what happens

---

### Post by avtolle on 2008-07-24
[https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344) is a bug report on what you have encountered.

---

### Post by Troll_the_Great on 2008-07-24
You can set the default kernel in System-Administration-StartUp Manager.If you don't have StartUp Manager search in Synaptic and install it, or type this code in a terminal:
```
sudo apt-get install startupmanager
```
If you want you can remove the new kernel from synaptic.Search for "linux headers" or "linux images" and remove everything that looks like 2.6.24-20.Be careful not to remove your old kernel though (2.6.24-19) 
Hope this helps.
Cheers!

---

### Post by avtolle on 2008-07-24
[http://ubuntuforums.org/showthread.php?p=5447759#post5447759](http://ubuntuforums.org/showthread.php?p=5447759#post5447759) is another thread on this problem.

As pointed out there (or in another thread I've read) this kernel upgrade came from the proposed repository. To avoid problems like this, disable the proposed repository in software sources, as the packages are there for (lack of a better term) "testing". There will be bugs with some of them, this being an example.

---

### Post by philinux on 2008-07-24
> **avtolle said:**
> [http://ubuntuforums.org/showthread.php?p=5447759#post5447759](http://ubuntuforums.org/showthread.php?p=5447759#post5447759) is another thread on this problem.

As pointed out there (or in another thread I've read) this kernel upgrade came from the proposed repository. To avoid problems like this, disable the proposed repository in software sources, as the packages are there for (lack of a better term) "testing". There will be bugs with some of them, this being an example.

+1 Never use proposed on your main machine. 
[https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security](https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security)

---

### Post by silkstone on 2008-07-24
+2 :)

A lot of people are having this problem - don't enable Hardy Proposed unless you are a developer or enjoy taking risks!

---

