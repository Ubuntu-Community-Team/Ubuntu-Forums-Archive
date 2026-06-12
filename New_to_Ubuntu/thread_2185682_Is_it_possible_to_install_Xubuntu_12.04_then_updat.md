---
title: "Is it possible to install Xubuntu 12.04 then update to kernel 3.11?"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by Remten on 2013-11-03
Sorry for such a basic question, but I still don't quite understand how things in Linux work.

If I install Xubuntu 12.04 LTS and it comes with, say, linux kernel 3.8, is there a way for me to upgrade the kernel to the latest kernel (3.11 or 3.12)?
And if I do it, will that cause a problem with how functioning of the rest of the current 12.04 installation or with getting future updates on the 12.04 installation?

---

### Post by pqwoerituytrueiwoq on 2013-11-03
only issue to be expected is breaking virtual-box and and proprietary drives (say nvidia or amd GPU drivers)
i would recommend xubuntu 12.10 it is supported till 14.04 comes out and you can upgrade directly to it
you can always use 13.04 and apply a couple bug fixes yourself and it will be good to go
this makes using newer kernels easy
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
if you wanted the 3.12 kernel on 12.04 you would run [FONT=courier new]KernelUpdateChecker -r saucy[/FONT] and it will make a installer for the 3.12rc7 kernel unless rc8 or 3.12 comes out by the time you run it

---

### Post by Remten on 2013-11-03
Thanks for the reply, and the suggestion.

Actually, the reason I want to try this is to be able to use some of the latest nvidia drivers, so if you meant there is a risk of breaking any previously installed nvidia drivers, that isn't my worry at all. What I would be worried about is not being able to use the newer nvidia drivers installed after doing the kernel update.

The problem with using 13.04 is that there's no alternate installer for it, and I need the alternate installer.

---

### Post by ian-weisser on 2013-11-03
From your description, a semiannual release (like 13.10) may be more appropriate for you than LTS (12.04).

Regardless of the install, virtualbox will continue to work smoothly as long as:
1) You are using the Virtualbox from the Ubuntu Repositories, not the VB website or some other source.
2) The dkms package is installed.

Proprietary drivers may or may not break with kernel upgrades.
- Drivers you obtain from the Ubuntu Repositories won't break - they will be updated with the kernel.
- Drivers you obtain from some other source or PPA or compile yourself must be reobtained or recompiled and reinstalled after each kernel upgrade.

Why do you need the alternate installer?

---

### Post by pqwoerituytrueiwoq on 2013-11-03
i would suggest the xorg edgers or the xswat ppa if you want a newer nvidia driver
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=precise](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=precise) stable 319.49
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise) unstable 331.17

---

### Post by Remten on 2013-11-03
> **ian-weisser said:**
> From your description, a semiannual release (like 13.10) may be more appropriate for you than LTS (12.04).

Regardless of the install, virtualbox will continue to work smoothly as long as:
1) You are using the Virtualbox from the Ubuntu Repositories, not the VB website or some other source.
2) The dkms package is installed.

Proprietary drivers may or may not break with kernel upgrades.
- Drivers you obtain from the Ubuntu Repositories won't break - they will be updated with the kernel.
- Drivers you obtain from some other source or PPA or compile yourself must be reobtained or recompiled and reinstalled after each kernel upgrade.

Why do you need the alternate installer?

I need the alternate installer because I want a dualboot hard drive with Windows and linux separately encrypted (Windows with TrueCrypt). I know how to use the alternate installer to set that up (I wouldn't say it's easy to install, but it's doable). In fact, I already have a copy of that backedup, so I can load it up in just a few minutes.
I have no idea how to use the regular installer for the same setup for 13.10, and I haven't seen any step-by-step explanations anywhere.

---

### Post by Remten on 2013-11-03
Here's what I did:

downloaded the latest mainline kernel parts from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) to my /Downloads folder

3 files  (since I have a 64-bit system, I got the amd64 ones):
[LIST]
[*]**generic headers** for amd64:   linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb 
[/LIST]
 
[LIST]
[*]**headers for all**:    linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb 
[/LIST]
 
[LIST]
[*]**image** for amd64:    linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb 
[/LIST]

I tried to install them by just clicking on their icons in the /Downloads folder, but my default package installer (Ubuntu Package Installer) balked, saying something about missing dependencies.

So I did the install a different way:

In the terminal I set the active directory to the /Downloads folder, which had no other files in it. Then I opened the packages, and finally updated the grub and rebooted:

```
cd /Downloads
sudo dpkg -i *.deb
sudo update-grub
sudo reboot now
```

As the packages were opened and installed, I did get some error messages about some missing NIC firmware:
[INDENT]"possible missing firmware /lib/firmware/rtl8168g-3.fw for module r8169"  (for example)[/INDENT]
 
But other than that, everything seems to have gone smoothly.
(Haven't tested extensively, but the bootup was smooth and no glaring problems as yet. My internet connection is working fine, despite the NIC firmware warning.)

Thanks to everyone for the replies and suggestions.

---

### Post by DuckHook on 2013-11-04
In my opinion, you are juggling with fire here, but hey, if you are fully backed up on both OSes and have your Windows install disks/licenses/activations handy, then why not? Part of the fun in Linux is the experimenting.

I must inform you that your install method will not give you kernel updates. Therefore, you will go unpatched and be at risk with new security exploits on your kernel unless you keep track of kernel updates manually and go through the same custom kernel rigmarole each time. I trust that you are aware of the fact that Ubuntu takes no responsibility for the security of PPAs. You must carefully research what you are doing and make sure that you trust the PPA. I posted [this]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") thread some days ago summarizing Linux security.

However, you are making your kernel installation process needlessly complicated. Just add the PPA to your software sources. If the PPA is well maintained, then this should give you automatic updates and you will have one less worry than your current method. [Here]("http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them") is a link showing you how this is done.

For what it's worth and speaking only for myself, I would never install a kernel that comes from anywhere outside the main Ubuntu repositories unless I compiled it from source myself. The reasons are in the link already alluded to, so consider yourself warned.

---

### Post by Remten on 2013-11-04
I am confused. I thought [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") contains kernels produced by Ubuntu, so they presumably wouldn't pose a threat of harboring intentionally malicious code.

---

### Post by DuckHook on 2013-11-04
> **Remten said:**
> I am confused. I thought [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") contains kernels produced by Ubuntu, so they presumably wouldn't pose a threat of harboring intentionally malicious code.
I did not read your link thoroughly. Just noticed the PPA part and not the URL. The caution still applies but in this case should be safe. Sorry for unnecessary confusion. PPA installation is still the way to go.

---

