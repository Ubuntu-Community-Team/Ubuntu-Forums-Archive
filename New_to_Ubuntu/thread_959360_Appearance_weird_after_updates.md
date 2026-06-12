---
title: "Appearance weird after updates"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Lakeside on 2008-10-26
I sure would like help with this! I`m not sure what happened,(it was getting really late and I was tired, so I`m trying to remember exactly what I did.) There was some sort of `update` option I enabled from a synaptic package list, I think. I had a normal looking desktop, sizewise (the websites had the normal size on the desktop).  I turned the computer off, and in the morning when I powered on, the websites were so big (text etc.) and I coulld not see the whole site without using the scroll bar at the bottom, and scrolling to the right.  I tried system..appearance,fonts and putting the fonts down to 8 (was at 14 before, because I had the opposite problem before, everything was so tiny). How do I get a `normal` looking appearance..oh yah, I got a different desktop wallpaper (some sort of stylized bird I think, and burnt orange bg colour. And I tried changing the screen resolution, but
it only had two options: 800 x 600 or 640 x 480, and not the larger one (1200 or something).

---

### Post by drewcoon on 2008-10-26
You likely updated your kernel version, and now your graphics drivers are no longer working.

As a temporary fix you could just restart your computer, and pick an older kernel version from the GRUB list at boot-up (the second newest should work best). If you want to use the new kernel I think you'll have to reinstall your drivers.

---

### Post by Lakeside on 2008-10-26
I forgot to mention...I only just installed Hardy Heron like 2 days ago
and am just learning about Linux..could you please tell me how to install new drivers..I don`t know that much :)  thanks for any help

---

### Post by drewcoon on 2008-10-26
Do you know what kind of graphics card/chip your computer has? If not, try looking for a sticker on your computer case (an ATI or nVidia one especially), or you could open up a terminal (Applications > Accessories > Terminal) and type in

```
sudo lspci
```

This will list all of your computer's hardware, try looking for the name of your card in there. for example my card looks like this:

```
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT
```

if you are having trouble finding your card, you could just copy and paste the output for us to find it :)

---

### Post by Lakeside on 2008-10-26
Thanks. As i become more familiar with the terminal commands, I guess I will have less questions (have been reading some of them) My computer was built for me by someone else, and didn`t know which things he put in it but, lspci shows almost all  `VIA Technologies Inc.` components.

---

### Post by drewcoon on 2008-10-26
> **Lakeside said:**
> Thanks. As i become more familiar with the terminal commands, I guess I will have less questions (have been reading some of them) My computer was built for me by someone else, and didn`t know which things he put in it but, lspci shows almost all  `VIA Technologies Inc.` components.

I've never heard of VIA Technologies before, all I can really do is steer you towards their Ubuntu driver downloads,

[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)

See if you can match up a name on the lspci list with a graphics chip there. Hopefully they are easy to install, because I don't have a VIA graphics chip, or any experience with setting one up. Sorry! I see that the drivers come with readme files and stuff which (hopefully) can walk you through without any problems.

Good luck :)

---

### Post by Lakeside on 2008-10-26
Thanks, I`m off to do some work now I guess :)
*edit*  Everything seems back to normal now.(for now..) I stumbled around, found this site ( [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy) ), went down to `Keeping the system up to date, and did this:   sudo apt-get dist-upgrade.
After that, under system, preferences, screen resolution, I suddenly had more choices and was able to pick a much higher res. (1280x1024) so sites fit normal on the page. I still have to fix keyboard (or try another keyboard..).
Thanks all.

---

