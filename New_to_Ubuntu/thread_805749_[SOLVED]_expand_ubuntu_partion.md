---
title: "[SOLVED] expand ubuntu partion"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Tibco on 2008-05-24
[http://img529.imageshack.us/img529/6838/partitionswm9.jpg](http://img529.imageshack.us/img529/6838/partitionswm9.jpg)

Thats what my computer looks like. I want to add the 10g unpartitioned space on to my 20g linux space. When i click on my linux partition, there are no options to expand it..is it not possible?


EDIT: READ BOTTOM TO SEE HOW I SOLVED IT, IF YOU HAVE THE SAME PROBLEM!

---

### Post by carloslosgrande on 2008-05-24
[FONT="Comic Sans MS"]I think you may need to select sda3 - extended - and expand it first, as sda5 sits inside it.[/FONT]

---

### Post by Tibco on 2008-05-24
but i can't though. the option is grayed out! do i have to do this in windows (my 120 gb partition) or from a live cd? Is it possible to expand the partition that is currently mounted?

---

### Post by tom56 on 2008-05-24
You can't resize or move a partition when it is mounted. Boot into the LiveCD and resize it from there.

---

### Post by carloslosgrande on 2008-05-24
[FONT="Comic Sans MS"]Hey Tibco, sorry I didn't realise you weren't using the GParted live CD. I saw the GParted screen and assumed wrongly.[/FONT]

---

### Post by Tibco on 2008-05-24
Yeah, i tried the LIVE cd, but even when i boot from safe graphics mode, i have a problem and well...Gpartred wont start up. As a noob, i was wondering...is there anyway to do this from Windows? I would feel much safer that way, i tried the disk manager thing that comes with vista, and it shrunk the vista partition, but couldnt expand the ubuntu partition. Is there any way to get gparted in windows?

---

### Post by tom56 on 2008-05-24
> **Tibco said:**
> Yeah, i tried the LIVE cd, but even when i boot from safe graphics mode, i have a problem and well...Gpartred wont start up. As a noob, i was wondering...is there anyway to do this from Windows? I would feel much safer that way, i tried the disk manager thing that comes with vista, and it shrunk the vista partition, but couldnt expand the ubuntu partition. Is there any way to get gparted in windows?

A LiveCD with gparted on is your best bet. They have one on their website:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

EDIT: Just realised there may be some confusion going on here. I assumed before that we were talking about the Ubuntu LiveCD. Either way, try which ever LiveCD you haven't use yet :)

---

### Post by Tibco on 2008-05-24
Allright!! I got my linux partion 10g bigger! I ended up using [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php") , which HAD the latest Gparted on it + other awsome features. It took like an hour, but everything in ubuntu seems to work fine, havn't tried windows yet, but since i havent touched it with PartedMagic, there should be any problem!

Thanks for your help!! :guitar:

---

