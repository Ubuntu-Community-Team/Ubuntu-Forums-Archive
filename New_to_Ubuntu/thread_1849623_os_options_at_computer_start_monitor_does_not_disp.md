---
title: "os options at computer start monitor does not display these"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by carl speers on 2011-09-24
I just installed ubuntu 11.04 on my laptop w/ xp and on a desktop w/xp. The laptop install dual boot is flawless, however the newer desktop with larger monitor has one issue. When I start my computer I cannot see the os options, my monitor has a message that tells me the signal is not usable, then it starts ubuntu , runs fine. So I restart the computer and blindly when the message comes up, with some trial and error I hit my down arrow key 6 times and xp loads, so it appears it is there, and all works well. I just cannot see the os I'am blindly hitting. I installed both systems next to xp with 30 gigs of hard drive. I can see the os options on the older laptop( 5 yrs or so old ).What do I need to do so I can see the os options to pick at start up of the computer.

---

### Post by papibe on 2011-09-24
Welcome to the forums!

My guess is that your monitor doesn't support the resolution in which grub (the os menu) is presented. Research which low resolutions your monitor supports and then set grub to that resolution.

Check this [tutorial]("https://help.ubuntu.com/community/Grub2"), specially the section 'Configuring GRUB 2'. I think the key field is called GRUB_GFXMODE.

Hope it helps,
Regards.

EDIT: on second thoughts, you may try to use the GUI app Start-Up Manager (read about it [here]("https://help.ubuntu.com/community/StartUpManager")), it is much easier to change the boot resolution.

---

### Post by carl speers on 2011-09-24
Thanks, I will give this a try.

---

### Post by wildmanne39 on 2011-09-24
Hi, this is how I fixed mine and helped other people do the same.
```
gksudo gedit /etc/default/grub
```
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=800x600

Then save and exit the document.


Then do:
```
sudo update-grub
```

thank you

---

