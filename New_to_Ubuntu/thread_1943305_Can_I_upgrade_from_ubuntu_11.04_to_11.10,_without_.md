---
title: "Can I upgrade from ubuntu 11.04 to 11.10, without upgrading kernel?"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by ratman1 on 2012-03-19
Hi

My laptop's touchpad works much better on the kernel shipped with ubuntu 11.04, and by upgrading to 11.10, the touchpad doesn't work as well due to the later kernel. It is hard to describe, but the later kernel does not seem to register the correct amount of pressure on the touchpad, and as such, I have to push quite hard to get it to register. I have confirmed this by booting live cd's of 11.04 and 11.10, and there is a very noticeable difference.

My question/s is/are: is there a way I can upgrade the distro from 11.04 to 11.10, without upgrading the kernel? If I do so, will all the packages still work, or will they depend on having the later kernel?

If it is too much of a trouble, I will be happy to leave it as 11.04.

Thanks

---

### Post by Frogs Hair on 2012-03-19
The Kernel will be upgraded . I don't know if you could install an earlier kernel and lock that version after the upgrade. There are differences between Gnome 2 and Gnome 3, but it may be possible though . You may have to wait for an answer from someone who has done it .

---

### Post by Paddy Landau on 2012-03-19
A better solution will be to solve the problem that you have.

If you have a working version of 11.10 on your system (perhaps dual-boot?), start a new thread to see if someone can help fix your touchpad.

---

### Post by Paqman on 2012-03-19
> **Paddy Landau said:**
> A better solution will be to solve the problem that you have.


I agree. It sounds like the touchpad is being detected by the new kernel and is working, but is not quite configured correctly. It'll probably be far easier to fix that than try to bodge the entire system.

I'd say go ahead and install 11.10 to a new partition so you can dual-boot 11.04 and 11.10 while you fault-find and get to the bottom of it.

---

### Post by tbhatia4 on 2012-03-19
> **ratman1 said:**
> Hi

My laptop's touchpad works much better on the kernel shipped with ubuntu 11.04, and by upgrading to 11.10, the touchpad doesn't work as well due to the later kernel. It is hard to describe, but the later kernel does not seem to register the correct amount of pressure on the touchpad, and as such, I have to push quite hard to get it to register. I have confirmed this by booting live cd's of 11.04 and 11.10, and there is a very noticeable difference.

My question/s is/are: is there a way I can upgrade the distro from 11.04 to 11.10, without upgrading the kernel? If I do so, will all the packages still work, or will they depend on having the later kernel?

If it is too much of a trouble, I will be happy to leave it as 11.04.

Thanks
i would suggest you not to upgrade if you are classic desktop lover
moreover configuring touch pad is another issue altogether

---

### Post by Paddy Landau on 2012-03-19
> **tbhatia4 said:**
> i would suggest you not to upgrade if you are classic desktop lover
That's not much of a solution, as 11.04 will be supported only until October this year. If you don't like Unity, use a different distro -- within the Ubuntu family (e.g. KDE, Xubuntu, Lubuntu); based on Ubuntu (e.g. Mint); or non-Ubuntu (e.g. Fedora, openSUSE).

---

### Post by raja.genupula on 2012-03-19
got something similar 
 [http://askubuntu.com/questions/109754/update-to-11-10-without-touching-the-kernel](http://askubuntu.com/questions/109754/update-to-11-10-without-touching-the-kernel)

---

### Post by radon7 on 2012-03-19
For the kernel question the best thing to do would actually just do a complete upgrade, then in the grub menu select the older kernel if that is what you want to run. 

The problem is not the kernel probably though, so what I would do is boot the 11.10 live cd and try to reconfigure the touchpad to get it working correctly then save the changed files to flash drive and upgrade. After you upgrade you can replace the files from flash drive. If you go to 'system settings' there is an icon to configure your mouse or touchpad and I would start there.

---

