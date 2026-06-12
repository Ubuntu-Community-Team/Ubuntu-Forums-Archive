---
title: "GRUB changed after fresh install"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by smitty_1616 on 2013-12-03
Hi there, pretty new to the linux system in general and this community.  I just upgraded from 10.04 -> 12.04 and I noticed a change in my systems GRUB after, not just the look, but it seems that it is missing many of my windows components such as the recovery startup program (which i currently need pretty bad due to a bad virus on my vista client(no surprises there))... anyways is there some sort of command or file to edit that would just kinda bring it back to the way it was? To be clear, there used to be an "XP" option in the GRUB which would take me straight to my vista recovery client and now there is not, ever since the update a few days ago.

---

### Post by rburkartjo on 2013-12-03
you could try this. download the iso burn to disk and boot from the live cd. follow the instructions. note if you get the option to upgrade boot repair you dont have to still works fine. 
[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

good luck!

---

### Post by fantab on 2013-12-03
Have you tried:
```
sudo update-grub
```

... from Ubuntu?

---

### Post by squakie on 2013-12-05
Also, previously I believe you would have edited grub.cfg.  That is no longer done and that file is overwritten automatically.  So, did you have some custon entries in your 10.04 grub.cfg file?  If so, these need to be put in configuration files now.  Let us know if that's what you need.

---

### Post by amjjawad on 2013-12-05
> **smitty_1616 said:**
> Hi there, pretty new to the linux system in general and this community.  I just upgraded from 10.04 -> 12.04 and I noticed a change in my systems GRUB after, not just the look, but it seems that it is missing many of my windows components such as the recovery startup program (which i currently need pretty bad due to a bad virus on my vista client(no surprises there))... anyways is there some sort of command or file to edit that would just kinda bring it back to the way it was? To be clear, there used to be an "XP" option in the GRUB which would take me straight to my vista recovery client and now there is not, ever since the update a few days ago.

Hi,

Could you please tell us what exactly do you have on your GRUB menu? 

Thanks!

---

### Post by philinux on 2013-12-05
In Ubuntu download and run the bootinfoscript [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Poste back the resulting txt file as an attachement.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by smitty_1616 on 2013-12-05
> **philinux said:**
> In Ubuntu download and run the bootinfoscript [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Poste back the resulting txt file as an attachement.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Wow first of all, thank you to everyone who took the time to answer... 5 answer in just over a day, sweet deal it's nice to know that people are looking. I will attatch the results here.

*Edit* I also just ran sudo update-grub , and after looking at the text file I just attatched, I'm going to restart right now and see if it's there... I wish I was as good as you guys with this stuff cause then I would just delete windows all together but I need it to play my games

---

### Post by fantab on 2013-12-05
Try 'purging grub' and reinstalling it...
You can do this either with [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") from a Live DVD/USB (Boot-Repair will also create a '*BootInfo Summary*' note the LINK and paste it here).
Or
You can use ['chroot' from Live DVD/USB]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd"). (later Use BootInfo Script and post the output here).

---

