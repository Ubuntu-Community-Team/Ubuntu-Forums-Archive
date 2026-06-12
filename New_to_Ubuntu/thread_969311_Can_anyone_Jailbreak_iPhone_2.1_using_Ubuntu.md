---
title: "Can anyone Jailbreak iPhone 2.1 using Ubuntu?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ubunt2guy on 2008-11-03
has anyone done this yet?  I'm thinking I could use ZiPhone soft.are through Wine.  Will this Work?

cheers

---

### Post by jbrown96 on 2008-11-03
I don't think so. I have an iphone, and there doesn't appear to be anything you can do with it besides downloading pictures. From what I understand, the iphone uses a non-standard (thanks apple...) method to connect via usb (not the phsyical cord, but the device communications). It basically means that there's no way to sync it. It's easy to jailbreak on any windows/mac computer though, even ones where you don't have any priveleges. Ziphone doesn't need to be installed (just itunes), so it's fairly painless.
If you don't have any apps that you can't live without, I would recommend downgrading below 2.0. The has for the itunes library is cracked, and you can sync music (I use amarok) wirelessly. It's pretty awesome, allbeit slow.

---

### Post by BlackDragonBE on 2008-11-03
It works together with iTunes I think, so no.
You could do it at a friend with a windows pc and iTunes installed or someone with a mac.
You can also install a minimal XP on your PC as a dual-boot, then install iTunes on that and jailbreak.

---

### Post by emshains on 2008-11-05
Well, I think that it would be a bad idea to dual-boot in windows just because of that. You should rather virtual-box it, but still you'd need a license of XP to do that.

---

### Post by jbrown96 on 2008-11-05
Since Linux is handling the USB connection, virtual machines won't work. However, Virtualbox is supposed to have a USB pass-through feature, which may work. If you are using <2.0 software on it, you won't need windows except to jailbreak. It would be much easier to find someone with a mac or windows to let you jailbreak it, but if you can't, I'd recommend a temporary dualboot

---

### Post by ntetreau on 2008-11-10
I have a very small 8gb windows partition that I use just for that.  Although you can get sync working with itune through virtualbox, it is still impossible to jailbreak the iphone that way since virtualbox doesn't handle the iphone in DFU mode.

---

### Post by miatawnt2b on 2008-11-16
I've done it using the newest QuickPwn under Virtualbox running XP.  It is a bit flaky though.  You need to manually connect and disconnect the USB connection by using the pulldown Virtualbox menu at certain times.  Pretty much it was trial and error.  The QuickPwn software has pretty long timeouts for the steps, so it was easy to tell if the Jailbreak was hung.  I would let it sit 2-3 min, and if there was no activity with the software, I would disconnect/reconnect the USB using the VBox pulldown menu, at which point QuickPwn would automatically proceed.

So it can be done.

-J

---

### Post by dima338 on 2008-11-16
You can in fact jailbreak your iPhone using a command-line utility called xPwn ([http://github.com/planetbeing/xpwn/tree/master]("http://github.com/planetbeing/xpwn/tree/master")) but it doesn't work with 2.1 as of yet, however it's fully compatible with Linux.

---

### Post by ghimus on 2009-02-07
I've done it and like miatawnt2b said, it's flaky, you must manually disconnect the iPod/iPhone at some point, and there's the small possibility of a kernel panic while doing it. Other than that it works. Details here: [http://www.squidoo.com/iPod-Jailbreak-via-VirtualBox](http://www.squidoo.com/iPod-Jailbreak-via-VirtualBox)

---

### Post by musikgoat on 2009-06-06
I would like to confirm miatawnt2b's comment that Jailbreaking the iPhone can be done through ubuntu.  

I'm running Jaunty, with a vBox install (Sun Virtualbox version 2.2.4) running Windows 7 RC1 currently). I have an iPhone 3G on firmware version 2.2.1

I only use windows for itunes to manage my podcasts and iphone. 

I was able to successfully jailbreak the iphone in windows 7 using quickpwn 2.2.5 with a couple of caveats pointed out in ghimus's blog link.  

Note that the link references the first gen iphone, however, the steps suggested match in line with what I did, and my result is a jailbroken iphone!

yey, now on to downgrading the baseband (hopefully I have the 5.8 baseband bootloader) and unlocking the iphone.

-tim

---

