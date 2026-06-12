---
title: "[SOLVED] Getting a file from old HD?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by A$h X on 2008-11-07
[FONT="Tahoma"]I installed my old HD into a new PC (as a secondary HD), then realized I need the bookmarks from my old firefox installation. Right now I'm booting Vista and will be installing ubuntu 8.10 very soon (on my first HD, separate partition). My old HD was setup so it has an XP partition and an hardy heron partition.

Will my new Intrepid Ibex be able to see the old firefox files (spefically the bookmarks.html file) on my old hardy heron partition, or do I need to put my old HD back into my old PC and manually save the bookmarks.html file to a USB or something?

Or as a long-shot seeing as the bootloader is still present on my old HD, could I boot from it by changing the boot order in my BIOS, and then exporting the file that way? Cheeky I know, but worth a try I suppose.[/FONT]

---

### Post by Sand Lee on 2008-11-07
The migration assistant currently doesn't work with firefox 3 so you won't be able to get them at install. However if you mount the second hard drive (after Intrepid is installed) then you can copy the files from there.

---

### Post by anystupidname on 2008-11-07
Yea, you'll be able to retrieve the bookmarks.html file with the old drive slaved. No need to boot from it. (probably a better idea NOT to)

---

### Post by bennachie on 2008-11-07
Vista should see the files on your old HD, and you might want to export them to a USB stick (just in case something goes wrong). However, once you have it installed, Intrepid should also see the files, and I have had no difficulty moving things around (I have three working hard disks at the moment, respectively booting to XP Pro, Intrepid and openSUSE).

---

### Post by A$h X on 2008-11-07
[FONT="Tahoma"]Well I thought "what the heck" and hit F12 on bootup to specify my boot device. Selected my second HD and up popped the good ol' GRUB loader. I chose the topmost kernel and lo and behold it actually booted! :guitar: With a completely different hardware setup and everything!

It threw me to the CLI upon boot, but I hazarded a guess and typed "gnome" followed by my username and pw and bang I was in like flynn. Obviously the screen resolution was real low, but that's to be expected as the gfx card were not installed.
Everything else was working fine, saved the bookmarks.html to my shared partition and thanked linux, GNU and everyone else involved with Ubuntu for making such an robust operating system. 

I was seriously impressed with the abilty to run on completely differnet hardware with hardly any errors, I'm not trying to flame microsoft, but I doubt windows could do that- actually I still have my old XP install on the secondary HD so maybe I'll give it a bash. Again I'd like to express my thanks for the greatest (IMO) OS in the world.

Ubuntu: We Da Best! :cool:[/FONT]

---

