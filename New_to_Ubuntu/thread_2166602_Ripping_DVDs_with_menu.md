---
title: "Ripping DVDs with menu"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by joetait on 2013-08-10
Hi

I want to backup my dvd collection, without losing subtitles, deleted scenes, etc.


I have found articles such as this - [http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html](http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html)


It seems that only one of these is still available with the features I want - that program is dvd::rip


However, it is ripping the main film on the dvd in to roughly 22 minute sections (this is not related to where the chapters appear in the film), and not in avi format (it is .vob).


Does anyone have any ideas either for

[LIST=1]
[*]an alternative program
[*]how to fix the issues with dvd::rip
[*]an easy way to convert and combine the .vob files to one .avi file
[/LIST]


Thanks in advance for any help :)

---

### Post by gordintoronto on 2013-08-10
Handbrake is considered the gold standard for DVD ripping. [http://handbrake.fr/](http://handbrake.fr/)

---

### Post by bootedguy on 2013-08-10
I have had very good results with [http://www.makemkv.com/download/](http://www.makemkv.com/download/) It always seems to be in beta, but don't that fool you.

---

### Post by nerdtron on 2013-08-11
When I want to preserve a DVD with menus and other extras, I'll just make a clone of it. I mean I copy the whole thing and make an ISO file. It will always play with VLC.

dd if=/dev/cdrom of=/path/dvd.iso

It will take the same space as the DVD itself so be sure that the DVD is worth the space.

If you really want to rip, lifehacker has a very good step by step guide for combining the power of makemkv and handbrake.
[http://lifehacker.com/5559007/the-hassle+free-guide-to-ripping-your-blu+ray-collection](http://lifehacker.com/5559007/the-hassle+free-guide-to-ripping-your-blu+ray-collection)

---

### Post by joetait on 2013-08-11
> **nerdtron said:**
> When I want to preserve a DVD with menus and other extras, I'll just make a clone of it. I mean I copy the whole thing and make an ISO file. It will always play with VLC.

dd if=/dev/cdrom of=/path/dvd.iso


That looks great, am currently trying it, thanks 


In case other people come here, then I also used this link - [http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/](http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/) - to check what path I had to replace /dev/cdrom with.



Thanks very much

---

