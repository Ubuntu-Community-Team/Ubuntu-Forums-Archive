---
title: "Installed 8.04 with Wubi - now 2 boot loaders?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by mustang90 on 2008-05-14
Hey guys,

Unfortunately my first post is a sorta problem, may be easy to fix; so here it is.

I have Windows XP Pro installed on my "C" partition (35 gb) and the rest of the disk as my "D" partition just for data (40 gb). About a month or two ago I had my "D" drive as a dedicated Ubuntu partition (7.10) with grub as the boot loader. I just let it install and do its thing. Long story short, I did not like not having a data only partition, so I temporarily removed Ubuntu and used the "fixmbr" command to restore the windows boot loader for the time being.

So yesterday I installed Ubuntu 8.04 in windows using Wubi and everything worked fine. My only problem is that when the computer boots, it uses the Wubi boot loader (whatever Wubi does to the windows one) followed by grub. So basically I have two separate boot loader menus and two separate timer count downs, lol.

I see that in the boot folder there is a grub folder with 3 files, one which has the grub info to edit. (I'm at work right now, computer is at home, sorry for vagueness) My temp fix was going to be to try to set the grub countdown real short so I don't notice it, but there should be a better way to solve this I would think. I haven't done this yet.

Is there a way to shut grub down, or a way to use grub and disable the Wubi modified bootloader? Thanks in advance. Hopefully this go around will keep me with linux for a bit longer! Any help is greatly appreciated!

-Brian

---

### Post by Paqman on 2008-05-14
You can edit the Grub options in /boot/grub/menu.lst

I'd just set the Grub timeout to 1 sec. I wouldn't choose zero in case you need to use Grub in the future. Another option in there is to uncomment "hiddenmenu", which would mean you wouldn't see the Grub list (I believe you have to hit Esc to bring it up)

If you migrate your Ubuntu installation to it's own partition later (using LVPM) you'll be able to just use Grub, in the meantime you're stuck with two bootloader lists.

---

### Post by mustang90 on 2008-05-14
> **Paqman said:**
> You can edit the Grub options in /boot/grub/menu.lst

I'd just set the Grub timeout to 1 sec. I wouldn't choose zero in case you need to use Grub in the future. Another option in there is to uncomment "hiddenmenu", which would mean you wouldn't see the Grub list (I believe you have to hit Esc to bring it up)

If you migrate your Ubuntu installation to it's own partition later (using LVPM) you'll be able to just use Grub, in the meantime you're stuck with two bootloader lists.

Yea, right now the list is hidden. Ok, well then I'll probably just do that for a quick fix. I was surprised that grub came back though. I knew it was somewhere but I thought the "fixmbr" removed it from anywhere it was referenced. If I do decide to install Ubuntu on its own partition would it be easy to make grub take over from the windows boot loader again? Thanks for the help by the way.

---

### Post by Paqman on 2008-05-14
> **mustang90 said:**
> If I do decide to install Ubuntu on its own partition would it be easy to make grub take over from the windows boot loader again?

Yep, dead easy.

If you migrate your current Wubi install to it's own partition you'd use [LVPM](http://lubi.sourceforge.net/lvpm.html), which will reinstall Grub to where it needs to be.

If you do a fresh install, then it's business as usual.

---

### Post by mustang90 on 2008-05-14
> **Paqman said:**
> Yep, dead easy.

If you migrate your current Wubi install to it's own partition you'd use [LVPM](http://lubi.sourceforge.net/lvpm.html), which will reinstall Grub to where it needs to be.

If you do a fresh install, then it's business as usual.

Awesome, Thanks man!

---

