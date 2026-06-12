---
title: "Compiz plugins help"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by mantix on 2012-01-11
Hi all, I've been using Ubuntu for at lest a year now, totally hate windows now with a passion, so I'm very familiar with everything.
I'm using Ubuntu 10.10 x86_64
Intel core i7 CPU Q720 @ 1.60GHz
4GB RAM 500GB HDD 
every things up-to-date after a fresh install of ubuntu :P

so my story is I'm trying to install a plug-in by santamaxx called earth here's a youtube video of it [http://www.youtube.com/watch?v=_LEit10e_CE](http://www.youtube.com/watch?v=_LEit10e_CE)

  and from there I followed everything to a page to these GitWeb (git.compiz.org) thing :confused: no idea now
git://anongit.compiz-fusion.org/users/satamaxx/earth from git.compiz.org

what do I do from here, I attempted this here

user@pc:~$ cd /home/user/.compiz
[EMAIL="user@pc:%7E/.compiz"]user@pc:~/.compiz[/EMAIL]$ cd earth
[EMAIL="user@pc:%7E/.compiz"]user@pc:~/.compiz[/EMAIL]/earth$ make && make install
compiling : earth.c -> build/earth.loIn file included from earth.c:1:
earth.h:14: fatal error: curl/curl.h: No such file or directory
compilation terminated.
make: [build/earth.lo] Error 1 (ignored)
compiling : earth.c -> build/earth.lo
linking   : build/libearth.lalibtool: link: `build/earth.lo' is not a valid libtool object
make: [build/libearth.la] Error 1 (ignored)
linking   : build/libearth.la
install   : /home/user/.compiz/plugins/libearth.soinstall: cannot stat `build/.libs/libearth.so': No such file or directory
make: [install] Error 1 (ignored)
install   : /home/user/.compiz/plugins/libearth.so
install   : /home/user/.compiz/metadata/earth.xml
install   : build/compiz-earth.schema
install   : /home/user/.compiz/data/earth.frag
install   : /home/user/.compiz/data/earth.vert
install   : /home/user/.compiz/images/skydome.png
install   : /home/user/.compiz/images/clouds.png
install   : /home/user/.compiz/images/night.png
install   : /home/user/.compiz/images/day.png

and got that :confused: I'm stuck here, and I'm in over my head but really want to learn these things.
cheers:D

---

### Post by airplanesimen on 2012-01-11
> **mantix said:**
> Hi all, I've been using Ubuntu for at lest a year now, totally hate windows now with a passion, so I'm very familiar with everything.
I'm using Ubuntu 10.10 x86_64
Intel core i7 CPU Q720 @ 1.60GHz
4GB RAM 500GB HDD 
every things up-to-date after a fresh install of ubuntu :P

so my story is I'm trying to install a plug-in by santamaxx called earth here's a youtube video of it [http://www.youtube.com/watch?v=_LEit10e_CE](http://www.youtube.com/watch?v=_LEit10e_CE)

  and from there I followed everything to a page to these GitWeb (git.compiz.org) thing :confused: no idea now
git://anongit.compiz-fusion.org/users/satamaxx/earth from git.compiz.org

what do I do from here, I attempted this here

user@pc:~$ cd /home/user/.compiz
[EMAIL="user@pc:%7E/.compiz"]user@pc:~/.compiz[/EMAIL]$ cd earth
[EMAIL="user@pc:%7E/.compiz"]user@pc:~/.compiz[/EMAIL]/earth$ make && make install
compiling : earth.c -> build/earth.loIn file included from earth.c:1:
earth.h:14: fatal error: curl/curl.h: No such file or directory
compilation terminated.
make: [build/earth.lo] Error 1 (ignored)
compiling : earth.c -> build/earth.lo
linking   : build/libearth.lalibtool: link: `build/earth.lo' is not a valid libtool object
make: [build/libearth.la] Error 1 (ignored)
linking   : build/libearth.la
install   : /home/user/.compiz/plugins/libearth.soinstall: cannot stat `build/.libs/libearth.so': No such file or directory
make: [install] Error 1 (ignored)
install   : /home/user/.compiz/plugins/libearth.so
install   : /home/user/.compiz/metadata/earth.xml
install   : build/compiz-earth.schema
install   : /home/user/.compiz/data/earth.frag
install   : /home/user/.compiz/data/earth.vert
install   : /home/user/.compiz/images/skydome.png
install   : /home/user/.compiz/images/clouds.png
install   : /home/user/.compiz/images/night.png
install   : /home/user/.compiz/images/day.png

and got that :confused: I'm stuck here, and I'm in over my head but really want to learn these things.
cheers:D

First go into your file by typing 
```

cd earth

```

Show me the output of this afterwards: (just to see what files which is in there)
```

ls 
```
and post it here :)

---

### Post by mantix on 2012-01-11
user@pc:~/Downloads/earth$ ls
CMakeLists.txt  earth.c  earth.xml.in  Makefile     README
data            earth.h  images        plugin.info
 
in the data folder there is
earth.frag        earth.vert

there's a hidden folder called .git and in there is 
branches  description  hooks  info  objects      refs
config    HEAD         index  logs  packed-refs

and the README has got nothing useful in it.


# Compiz Earth plugin
#
# Copyright : (C) 2010 by Maxime Wack
#
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
##


This is a plugin for Compiz 0.8 branch that allows user to have a 3D earth inside the cube, with realtime day and night.
Cube must, of course, be enabled.
Configure using ccsm. You can set the center of the view to your location, specifying longitude and latitude.
Don't forget to set your timezone. Daylight Savings Time is automatic.

Installation :
libGLEW is required !

$make && make install

Read changelog about updating from the very first version.

skydome.png in data dir (installed to ~/.compiz/data/) is to be used as an animated skydome.
It's a view of all the outer space visible from earth.

You don't have to specify texture files anymore, the plugin will automatically retrieve a day.png file for the day texture in ~/.compiz/data/.
For smaller screens, or graphic adapters with a small amount of video memory, you can resize the texture to yet a smaller size (please use power of two factors, it will be easier for your video card).



Changelog :

2011/08/18
Rewrote the entire plugin to be cleaner, faster (or using less ressources), with correct comments in English and in line with the compiz coding style.
Now the plugin automatically retrieves its textures from ~/.compiz/data/.
Corrected a bug when loading the textures.
Hardcoded the sphere generation to get rid of the GLU dependency.
Translated the configuration in English.
Resized skydome.png, day.png and night.png (not used yet) to a smaller yet still detailed enough resolution.
If you are updating from the first version, you can clean ~/.compiz/data, as for now any other file than day.png and skydome.png is not used.

2011/08/20
Shader support !!! The plugin will determine itself if shader are supported and use them (earth.vert and earth.frag in the data dir)
New cool effects : multitexture with night texture. Per-pixel lighting and specular reflexion on oceans.
libGLEW is now required to build the plugin.

For future changes, check the git commit messages !

---

### Post by airplanesimen on 2012-01-12
> **mantix said:**
> user@pc:~/Downloads/earth$ ls
CMakeLists.txt  earth.c  earth.xml.in  Makefile     README
data            earth.h  images        plugin.info
 
in the data folder there is
earth.frag        earth.vert

there's a hidden folder called .git and in there is 
branches  description  hooks  info  objects      refs
config    HEAD         index  logs  packed-refs

and the README has got nothing useful in it.


# Compiz Earth plugin
#
# Copyright : (C) 2010 by Maxime Wack
#
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
##


This is a plugin for Compiz 0.8 branch that allows user to have a 3D earth inside the cube, with realtime day and night.
Cube must, of course, be enabled.
Configure using ccsm. You can set the center of the view to your location, specifying longitude and latitude.
Don't forget to set your timezone. Daylight Savings Time is automatic.

Installation :
libGLEW is required !

$make && make install

Read changelog about updating from the very first version.

skydome.png in data dir (installed to ~/.compiz/data/) is to be used as an animated skydome.
It's a view of all the outer space visible from earth.

You don't have to specify texture files anymore, the plugin will automatically retrieve a day.png file for the day texture in ~/.compiz/data/.
For smaller screens, or graphic adapters with a small amount of video memory, you can resize the texture to yet a smaller size (please use power of two factors, it will be easier for your video card).



Changelog :

2011/08/18
Rewrote the entire plugin to be cleaner, faster (or using less ressources), with correct comments in English and in line with the compiz coding style.
Now the plugin automatically retrieves its textures from ~/.compiz/data/.
Corrected a bug when loading the textures.
Hardcoded the sphere generation to get rid of the GLU dependency.
Translated the configuration in English.
Resized skydome.png, day.png and night.png (not used yet) to a smaller yet still detailed enough resolution.
If you are updating from the first version, you can clean ~/.compiz/data, as for now any other file than day.png and skydome.png is not used.

2011/08/20
Shader support !!! The plugin will determine itself if shader are supported and use them (earth.vert and earth.frag in the data dir)
New cool effects : multitexture with night texture. Per-pixel lighting and specular reflexion on oceans.
libGLEW is now required to build the plugin.

For future changes, check the git commit messages !

Okay.. this looks like a update for me. If it is only one file int the archive, it isnt any possible way to install it. are you sure it is the right file? (where did u find it, so i can check?)

---

### Post by mantix on 2012-01-12
I got the file by going in to terminal and typing
```
git clone git://anongit.compiz-fusion.org/users/satamaxx/earth
```
make sure to change directory to were you want it to download to.

---

### Post by airplanesimen on 2012-01-12
> **mantix said:**
> I got the file by going in to terminal and typing
```
git clone git://anongit.compiz-fusion.org/users/satamaxx/earth
```
make sure to change directory to were you want it to download to.

Watch this, maybe the new version will help.
[http://www.youtube.com/watch?v=Vk6xk5_XNAs&feature=mfu_in_order&list=UL](http://www.youtube.com/watch?v=Vk6xk5_XNAs&feature=mfu_in_order&list=UL)

Download: You can now find the plugin on the official compiz git repository : [http://git.compiz.org/~satamaxx/earth](http://git.compiz.org/~satamaxx/earth)

---

### Post by mantix on 2012-01-12
how do i go about doing an official compiz git repository

---

### Post by airplanesimen on 2012-01-12
(here is the direct download link: [http://git.compiz.org/~satamaxx/earth/snapshot/earth-eb5194ac6ee434a0153af22aec2cf94572c8df77.tar.bz2](http://git.compiz.org/~satamaxx/earth/snapshot/earth-eb5194ac6ee434a0153af22aec2cf94572c8df77.tar.bz2))

---

### Post by airplanesimen on 2012-01-12
> **airplanesimen said:**
> (here is the direct download link: [http://git.compiz.org/~satamaxx/earth/snapshot/earth-eb5194ac6ee434a0153af22aec2cf94572c8df77.tar.bz2](http://git.compiz.org/~satamaxx/earth/snapshot/earth-eb5194ac6ee434a0153af22aec2cf94572c8df77.tar.bz2))

Then you go in to the terminal, type cd /home/Username*/(File*), u just go in to the file, after you have extracted it to a folder. Type:

```

make

#then:
make install

```

---

### Post by mantix on 2012-01-12
convert   : earth.xml.in -> build/earth.xml
bcop'ing  : build/earth.xml -> build/earth_options.h
bcop'ing  : build/earth.xml -> build/earth_options.c
schema    : build/earth.xml -> build/compiz-earth.schema
compiling : earth.c -> build/earth.loIn file included from earth.c:1:
earth.h:14: fatal error: curl/curl.h: No such file or directory
compilation terminated.
make: *** [build/earth.lo] Error 1

thats the error i get when i make the file

---

### Post by airplanesimen on 2012-01-12
> **mantix said:**
> convert   : earth.xml.in -> build/earth.xml
bcop'ing  : build/earth.xml -> build/earth_options.h
bcop'ing  : build/earth.xml -> build/earth_options.c
schema    : build/earth.xml -> build/compiz-earth.schema
compiling : earth.c -> build/earth.loIn file included from earth.c:1:
earth.h:14: fatal error: curl/curl.h: No such file or directory
compilation terminated.
make: *** [build/earth.lo] Error 1

thats the error i get when i make the file

Hmmm, wierd.. i am going to try this myself now, wait..

Check here: [http://git.compiz.org/~satamaxx/earth/commit/?h=compiz-0.8&id=eb5194ac6ee434a0153af22aec2cf94572c8df77](http://git.compiz.org/~satamaxx/earth/commit/?h=compiz-0.8&id=eb5194ac6ee434a0153af22aec2cf94572c8df77)

---

### Post by raja.genupula on 2012-01-12
Hi actually one small thing i wanna ask , because i haven't seen that point in any post .I have seen that readme file which you have given in previous posts . There 
> libGLEW is required

so are you sure about this installation ?

---

### Post by mantix on 2012-01-12
that readme file was with the santamaxx earth folder, and in my synaptic package manager it says I have libGLEW installed to 1.5, i cant understand why it will not install, I do everything as per instructed and i get that error

---

### Post by airplanesimen on 2012-01-12
> **mantix said:**
> that readme file was with the santamaxx earth folder, and in my synaptic package manager it says I have libGLEW installed to 1.5, i cant understand why it will not install, I do everything as per instructed and i get that error

I know what the error is.. u are missing three different files, right? I do, so i did go to the last link i sent, and downloaded the updated files on the site, and placed them where they should. (in the extracted folder). then type the make install commando, and see if it works. the files where not included because they where "custom".

Wierd, i couldnt do it myself either, hmm, it must be something else -_-

---

### Post by youlina on 2012-01-12
hello everyone i am also come across this problem, i will try as all of you above suggustions,thank you very much!

---

### Post by mantix on 2012-01-12
you can try ```
make install -i
``` but for me i still got errors but it was progress

---

### Post by airplanesimen on 2012-01-26
i have asked him on youtube to help us with this problem, maybe he can? I commented on his video, and got a reply now, some days ago. I will keep you posted :P

---

### Post by satamaxx on 2012-01-26
Hello everyone !
The answer in your problem lies in the first error line : you need to install libcurl !
Sorry I forgot to add that to the requirements in the readme !
libcurl is used to fetch the realtime cloudmap, though it does sometime makes compiz crash (there seems to be a problem in the way compiz loads JPEGs). You might want to disable the realtime cloudmap in the plugin options to avoid that.

---

### Post by airplanesimen on 2012-01-28
> **satamaxx said:**
> Hello everyone !
The answer in your problem lies in the first error line : you need to install libcurl !
Sorry I forgot to add that to the requirements in the readme !
libcurl is used to fetch the realtime cloudmap, though it does sometime makes compiz crash (there seems to be a problem in the way compiz loads JPEGs). You might want to disable the realtime cloudmap in the plugin options to avoid that.

OH! Thankyou SOOOO much! It works :P IT WORKS!! :P Thanks a lot satamaxx :P (hope u add it to the readme for the next to download it ;)

---

