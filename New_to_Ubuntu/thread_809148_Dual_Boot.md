---
title: "Dual Boot"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by oldtom on 2008-05-27
Hello All,

I have installed Ubuntu 8.04 on my ntfs partition using the Wubi installer and it works fantastically. The Wubi installer created a dual boot login screen that allows me to choose XP or Ubuntu. 

But have just tried Freezy Ubuntu and I'm leaning a bit to this distro. It does everything I need and the look and feel is IMHO a bit more pleasing than the plain Ubuntu. The jury's still out though as I love both of these distros. IMHO the best out there.

My question(s).
Can I install Freezy Ubuntu the same way as I did with Ubuntu using the Wubi installer so it just sits as a folder on my main drive. Freezy does not appear to have the Wubi installer included, so how would I go about this. Would Wubi then create a third boot option to allow me to choose XP, Ubuntu or Freezy.
I'm thinking that maybe I need to run Freezy from the CD then install Wubi then install to the HDD using Wubi which I just installed to the CD, if that makes sense.
Is this even possible or am I completely off the track.

I also have a D:\ drive formatted as fat32 which has no files on it. If the above cannot be done (my preferred option), could I install Freezy to my D:\ drive just using the inbuilt installer. If this is my only option would the installer create a third boot option.

Can you gurus push me in the right direction. Are there any gotchas.

Cheers

---

### Post by forestpixie on 2008-05-27
If it doesn't have a wubi installer then you will I think have to install it the other way.

Yes you could use that partition and it will install a bootloader- grub - but it will need to change the filetype, it's likely that it will only show up itself and your windows as the wubi ubuntu is only inside windows not an install in it's own right. To get to ubuntu you would need to boot into windows I suspect.

Hope that helps some.

---

