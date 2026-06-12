---
title: "Replacing Vista with XP without harming Ubuntu"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by leoblack9 on 2008-05-01
Well I currently have a pc with Vista/Ubuntu on it. But I've had enough with Vista already, its sluggishness and errors are enough for me to hate it and I now use ubuntu most of the time.

But it got me thinking how could I do that? Should I remove ubuntu first then reformat? Or could I reformat without removing Ubuntu first? Besides, I'm worried that the technicians that would reformat my computer would have trouble reformatting ubuntu.

Any help?

---

### Post by mikeyphi on 2008-05-01
Hi there and welcome!
If you want to install XP (instead of only using Ubuntu!) you can replace Vista but you will have to reinstall GRUB using a LiveCD or a Grub CD.

If you also intend to upgrade or reinstall Ubuntu - then install XP first, followed by Ubuntu and all will be OK!
Remember to store personal data elsewhere first!!

---

### Post by Paqman on 2008-05-01
> **leoblack9 said:**
> Or could I reformat without removing Ubuntu first?

You sure could. Just treat it like a fresh install of XP. The XP installer will ask you which partition you want to install to. Pick your NTFS partition. It'll complain about there being an OS on it already, but that's fine, just let it go ahead and do a quick format.

Windows will nuke your Grub bootloader. You can [restore it](http://linuxbraindump.org/2007/08/17/restoring-grub/) pretty easily though.

---

### Post by leoblack9 on 2008-05-01
So that means I have to remove ubuntu first? The only problem I have is that I have to install gutsy all over again and upgrade to hardy again. I had to stay up all night until it finished. Thanks anyway for the reply

---

### Post by Kopiermeister on 2008-05-01
I have the same configuration. I also hat a Vista/Ubuntu System. I just installed XP instead of Vista (Vista really made me angry) and reloaded the grub with the "super grub disc". Worked very well for me!
I just had to edit the menu.lst a bit. Cause the old grub was loaded, i just had to write XP instead of Vista into the grub.

That's it!

---

### Post by Paqman on 2008-05-01
> **leoblack9 said:**
> So that means I have to remove ubuntu first?

Nope. It'll be completely untouched. Once you restore Grub you'll be able to boot into Ubuntu.

EDIT: Unless you installed Ubuntu through Wubi, of course. In which case you would have a problem.

---

### Post by sayakb on 2008-05-01
No, you don't have to remove Ubuntu. Just install XP, and that would remove GRUB. Then you could restore your grub.
 
EDIT: Paqman beat me to that :)

---

### Post by leoblack9 on 2008-05-01
Thank you for all of your replies! Now I guess I would just hide grub when the technicians are reformatting it.

---

### Post by Paqman on 2008-05-01
> **leoblack9 said:**
> Thank you for all of your replies! Now I guess I would just hide grub when the technicians are reformatting it.

You can hide Grub by editing /boot/grub/menu.lst and uncommenting the "hiddenmenu" line. I believe that it shows a blank screen instead and you hit ESC to show the menu.

---

