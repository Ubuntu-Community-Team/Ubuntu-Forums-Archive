---
title: "Unetbootin install to hard drive: getting stuck at Installation Type screen"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by yocally on 2013-08-18
I'm rather new to Ubuntu and Linux in general, I've been using Windows for years and recently I got an old Dell that was running windows 2000 and I'm hoping to get Ubuntu installed.
Now, the BIOS is pretty old so it can't boot from USB and the disk drive is broken, no idea why, so I can't boot from externally. After searching around the internet, I found Unetbootin, was told that it can install Ubuntu on the computer that it's run from, great. Got that downloaded, selected an ISO for Ubuntu 12, 32 bit. After running the installer on windows, I rebooted the computer and booted from the Unetbootin option. Everything booted up nice, on the live session user and clicked the "Install Ubuntu 12.04.2 LST" icon. Everything was going good until I got to the Installation Type screen, none of the buttons work and the fields are all blank. There's a drop down button for "Device for boot loader installation: " but the only option I have is "/dev/sda".
I can press the Install Now button but it gives me the "No root file system is defined. Please correct this from the partitioning menu." error.
I've tried booting to Windows, re-installing Ubuntu through the Unetbootin program a few times but it doesn't seem to change anything. I want to completely wipe the computer and start fresh from Ubuntu, no dual OS's, just Ubuntu when I'm done, but I can't get past this point.
Is there something that I missed, another tool that I can use, anything?

Thanks!

---

### Post by NM5TF on 2013-08-18
when you say "the disk drive is broken", do you mean the Hard Disk is broken??
if so, how can it run Windows or Unetbootin???

maybe you meant the CD drive is broken???

---

### Post by ahmad3 on 2013-08-18
he ment the CD thing try to install Ubuntu using a Wubi its alot easier to do that then remove windows from ubuntu :)

---

### Post by Boab1993 on 2013-08-18
Hi there yocally,

Can i ask what your hardware specifications are?

I think the problem your having is you can't partition the hard drive as the entire drive is taken up by your windows install, im no expert on 2000, i havent used it since i was knee high, but you might be able to shrink your current partition and format a new primary partiton for ubuntu.

@NM5TF i think he means his optical drive for DVD/CDs (digital video disk/compact disk) or 'disk drive'

Edit: ahmad3 has a point, just checked, WUBI is compatible with 2000, you should check it out : [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by yocally on 2013-08-18
Thanks for the responses!
NM5TF: Yes, the CD Drive is broken, so I'm not able to create a bootable CD
ahmad3: I'm downloading Wubi right now, thanks. Though it appears to be a .iso file, do you mean run that through Unetbootin or through a CD or flash drive? Going to try it on Unetbootin tomorrow when it's finished loading.
Boab1993: All I really know is that it's a Dell Dimension 8200 32-bit i386, I can probably find out more if you give me specifics. As for partitions, I haven't seen an option so far that actually lets me change them, and I do believe that it is possible to partition the drive as it gives me a choice to boot either to Windows 2000 or Unetbootin when I get past the BIOS screen, so I think that means that the drive can be split, but maybe not.

Anyway, I've got Wubi downloading and I'll try it later tomorrow. Thank you!

---

