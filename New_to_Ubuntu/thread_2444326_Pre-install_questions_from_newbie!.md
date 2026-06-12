---
title: "Pre-install questions from newbie!"
date: 2020-05-28
forum: New to Ubuntu
---

### Post by ndc320linux on 2020-05-28
Hello Ubuntu Forums!

I have a HP Elitebook 830 G6, running Windows 10 (latest build) with the BIOS running as-is. I believe Secure Boot is enabled, but I have disabled Fast Boot within Windows. I also have the Bitlocker drive protection running, but I am not required to enter a code when I switch on the computer. 

I wish to install Ubuntu 20.04 on my machine, to run alongside Windows 10 - however I want to ask do I need to disable the Secure Boot? I am able to boot the Live USB I prepared successfully, but I haven't proceeded with the install yet. 

Ideally, I would like to keep the secure boot on - but I can switch this off if this is required. I haven't found much guidance on whether this is needed, other than it should be fine to proceed with it on ... but I don't want to brick the install on the first go without seeking help and guidance. Interestingly, I see the HP Secure Start screen with the Ubuntu logo when booting the USB drive which suggested to me it would be fine. This is the screen I have when booting into Windows - the HP Secure Start with the spinner. 

Please could anyone confirm if I am safe to proceed with my system set up as-is?

Please forgive my very basic Linux skills, I am very new - last used Ubuntu in around 2010 when the Gnome panel had Applications - Places - System at the top! Long before the new interface. Back then I was dual booting with ease with Win XP and Win 7. Looking forward to returning.

Thank you very much, any and all help is greatly received and much appreciated.

---

### Post by dino99 on 2020-05-28
A recent howto to guide you [https://www.itzgeek.com/post/how-to-install-ubuntu-20-04-alongside-with-windows-10-in-dual-boot/](https://www.itzgeek.com/post/how-to-install-ubuntu-20-04-alongside-with-windows-10-in-dual-boot/)
an other too [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

First be sure of  the settings into your bios/uefi

[https://askubuntu.com/questions/1103852/how-to-install-ubuntu-18-10-to-an-uefi-system-with-windows-10](https://askubuntu.com/questions/1103852/how-to-install-ubuntu-18-10-to-an-uefi-system-with-windows-10)

---

### Post by grahammechanical on 2020-05-28
My experience of Microsoft Windows ended with Win98. My motherboard is a BIOS board so I have no personal experience of dual boot with Windows and UEFI and secure boot. I was around when Microsoft came out with secure boot> I remember the fuss it created in the Linux community and the steps that Ubuntu developers took to comply with secure boot. This wiki page has been updated to 2020. So, I suppose it is still relevant.


[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)


Secure boot should not be an issue.

> On Ubuntu, all pre-built binaries intended to be loaded as part of the  boot process, with the exception of the initrd image, are signed by  Canonical's UEFI certificate, which itself is implicitly trusted by  being embedded in the shim loader, itself signed by Microsoft.

Regards.

---

### Post by CatKiller on 2020-05-28
I know absolutely nothing about bitlocker, so I can't say anything helpful there.

> **ndc320linux said:**
> I wish to install Ubuntu 20.04 on my machine, to run alongside Windows 10 - however I want to ask do I need to disable the Secure Boot? I am able to boot the Live USB I prepared successfully, but I haven't proceeded with the install yet. 

Ideally, I would like to keep the secure boot on - but I can switch this off if this is required. I haven't found much guidance on whether this is needed, other than it should be fine to proceed with it on ... but I don't want to brick the install on the first go without seeking help and guidance. Interestingly, I see the HP Secure Start screen with the Ubuntu logo when booting the USB drive which suggested to me it would be fine. This is the screen I have when booting into Windows - the HP Secure Start with the spinner. 

As you probably already know, Secure Boot works by cryptographically signing the things that run, and the UEFI Secure Boot refuses to run anything that's not been signed by a key that the UEFI knows about. Motherboards ship knowing about Microsoft's keys, because the hardware manufacturers would be crazy to sell things *not* able to run Windows: that's just a market reality. There's no reason (as far as they're concerned) for them to ship their devices knowing about anyone else's keys, which would be a problem for users installing a non-Microsoft OS. So what Canonical and Red Hat (and maybe some others, I don't know) did was to get their own signing keys signed by Microsoft using Microsoft's keys; the UEFI trusts Microsoft's keys, so it trusts Canonical & Red Hat's keys, and so Secure Boot carries on working. All good.

The problem comes when you're installing something that needs a kernel module from a source *other than* Canonical or Red Hat, such as Nvidia's driver from a PPA, or Oracle's thing to make VirtualBox work: they can't have been signed by Canonical or Red Hat, because they've never been near Canonical or Red Hat, so they won't work with Secure Boot. The way to deal with that is to sign those parts yourself, and to tell your UEFI that you trust your own key: a process known as "enrolling a machine-owner's key." It's not *hard* to do that, but it is a bit fiddly, and is an extra hurdle that you'd need to do for using stuff from outside the standard repositories.

So the upshot is that Secure Boot will be perfectly fine as long as you're only using software from the repositories, and there are extra steps if you want to use other software. Because of those extra steps some people recommend turning off Secure Boot for an easy life.

---

### Post by ndc320linux on 2020-05-28
Hi All

Just a quick update, I'm writing this from Ubuntu 20.04 running on my laptop! RESULT! It might sound like a small and tiny step - but I accepted that in order to learn if I do it wrong, I will just have to risk losing my Windows 10 set up and if the worst comes to the worst - I will reinstall Windows later and give up on my dream to return to Linux... thankfully that didn't happen and I have both OS running.  

The install went well, and I selected the optional extras and created the secure boot password for Ubuntu - so far I haven't been asked for this... I have made a note of it just in case. 

I have been successful in booting into Windows 10 and also Ubuntu. Bitlocker didn't pose an issue in the end - I took the risk and left it running, and Ubuntu installed around it. My Windows drive remains encrypted as per my wishes! Although for the first boot into Windows I needed to enter the recovery key to verify myself - this worked fine. Subsequent boots don't require this.

The HP Secure Start screen still appears with the Ubuntu logo when booting into Linux - for the first two boots, it didn't boot. However, 3rd time lucky and inexplicably Linux boots and I was able to log in. Not sure why that is... hopefully that doesn't happen again. 

I will now get my set-up configured with the snaps I want and get all my accounts set up. Really happy this worked out! 

Thanks again for all your help.

---

