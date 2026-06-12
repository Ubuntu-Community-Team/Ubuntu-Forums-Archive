---
title: "Ubuntu Live cd usplash"
date: 2006-07-03
forum: Programming Talk
---

### Post by dcstimm on 2006-07-03
Hi guys,

I am trying my best to customize the ubuntu live cd for ppc.  

I want to change the usplash artwork, so this is what I did:

chroot'd to the livecd filesystem.squashfs 
ran though all the steps in [https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)
but got stuck at the last command:

sudo dpkg-reconfigure linux-image-$(uname -r)

I couldnt do this one because I was chrooted into the filesystem and it was running a different kernel.

So I tried to boot the ubuntu live cd, and run it in there which works, so now I want to copy the modified files back to my own filesystem.squashfs but I am not sure what was modified by the dpkg-reconfigure command.

Does anyone have any idea how I can get this done?

is there a way to do it in chroot?

do I need the contents of /boot /var/lib and /lib/modules?

What files are modified?

What does dpkg-reconfigure linux-image-$(uname -r) really do?

Thanks guys, any help would be greatly appreciated!

---

