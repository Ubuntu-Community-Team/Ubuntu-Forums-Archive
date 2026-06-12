---
title: "libppt (my opensource implementation of the ppt standard) - HELP needed ;-)"
date: 2006-12-24
forum: Programming Talk
---

### Post by Coldbird on 2006-12-24
Hello Fellow Ubuntu Users...

Im currently reverse engineering a File-Format for Textures called Playstation Portable Texture - or short... .ppt

I already did 99% of the work and can export most Images to .bmp... (I reverse engineered 32bit True Color Image Processing and Palette Indexed Image Processing using .ppc - Playstation Portable Color Table)...

But now Im sorta stuck... before I release all of this - I wanna code a Gimp Plugin that will allow me to directly open the Files in Gimp and also save them...

As the Fileformat is similiar to BMP - except the real alpha layer, i wanted to know if there is a C Source of the BMP Plugin for Gimp... That way I could save myself quite some Time...

PS. just for reference... .ppt is used in many Playstation Portable Games - Disguised as .bin Files often... ^_^
Also they are often packed into a EZBIND .arc Archive, I know how EZBIND Archives work, and once I finished this library I will probably do a EZBIND Archiver of some sort...

Greetings, Coldbird

---

### Post by po0f on 2006-12-24
Coldbird,

You can download the source directly from [GIMP's web site](http://www.gimp.org/downloads/).

---

### Post by Coldbird on 2006-12-24
All I can find is libjpeg, libpng, etc. in source download... and gimp itself - nothing to be seen of the bmp plugin

---

### Post by po0f on 2006-12-24
Coldbird,

Is [this](http://registry.gimp.org/plugin?id=239) it?

[EDIT]

Nevermind, just realized it's for GIMP 1.0.  Still might be useful, who knows...

---

### Post by Coldbird on 2006-12-24
Thank you very much - Its a old Release... but it doesnt matter - It should be good enough to base my Plugin on it... :D

Thanks Bud! :D

---

