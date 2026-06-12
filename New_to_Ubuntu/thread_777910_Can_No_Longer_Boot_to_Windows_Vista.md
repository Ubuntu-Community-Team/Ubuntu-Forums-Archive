---
title: "Can No Longer Boot to Windows Vista"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Mattnz on 2008-05-01
Hi,

I installed Ubuntu 8.04 onto a dual boot with Windows Vista as I have done in the past.

However this time, when I go to restart my computer, I get only 3 options to boot, and they are all for Ubuntu. 

It seems the Ubuntu boot manager has overwritten the Windows boot loader, and I can find no way to get it back. I've read a few tutorials on it on the internet, but none seem to work for me. 

Can someone please provide me with some steps that I can try to get this working with Vista again?

Thanks,
Matt :)

---

### Post by PinkFloyd102489 on 2008-05-01
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You can use that CD image to boot and restore the Vista bootloader, if that's what you're wanting. Otherwise, there are numerous guides for adding Vista back to GRUB.

---

### Post by mormor on 2008-05-01
heh. I have that problem to. But I think I might have "chosen" it. As I chose to totally wipe my hd for the 8.4 install. (dualbootet 7.10 and vista before this.) Im not missing vista anymore tbh. Even pealed off the vistasticker from my comp now. Need to find a ubuntusticker for the migthy ole laptop. ^^, Hope you work it out.

---

### Post by Mattnz on 2008-05-01
Can you please provide a link on how to add Vista back to the GRUB? I've tried a few ways, but none worked...

Would it work if I reinstalled Ubuntu?

---

### Post by agim on 2008-05-01
This should help
[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

Be sure to read ALL directions carefully, whenever doing something like this, especially for the first time.

---

### Post by Aurora@FleetBuzz on 2008-05-01
> **Mattnz said:**
> Would it work if I reinstalled Ubuntu?
It might, but if you want to bypass GRUB and get VISTA up and running first, try this:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Then you can try to re-install Ubuntu.  At least you'll know that Vista is safe and sound.

---

