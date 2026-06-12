---
title: "nvidia easy tvout"
date: 2006-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by SL0MO on 2006-01-08
Yesterday I was looking for a one-click solution for cloning display on tv (as easy as possible) 
so my girlfriend can use it to watch Sex and the City.
i.e. like this:

[[IMG]http://img302.imageshack.us/img302/9826/screenshot6ft.png[/IMG]](http://imageshack.us)

Clicking on the green tv : output to tv (and monitor, so she can start the episode with the mouse and then go to the tv) 
Clicking on the red tv : only output to monitor + turn tv off.

No further commandline or GUI are involved. Just two buttons.
My tv is too far away from my pc so "twinview" or "switch screen" was not an option.
These steps work for me, but are in no way a general "how-to" for your system.
Maybe it works, maybe not. Maybe you'll find some usefull info and make it work on your system too.
PLEASE don't just copy/paste the commands, you need to change them according to your own system/needs.

my setup:
-os: Ubuntu 5.10
-video card :NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]
-drivers : nvidia-glx 1.0.7667-0ununtu25.1 (from synaptic)
-tv : old JVC (PAL)
-connection : S-VIDEO

steps:

1. remove nvtv if installed 

2. install nvidia-glx (synaptic)
Maybe opensource drivers "nv" works, I just took the official nvidia one from the repos.

3. download nvtv source and untar ([http://sourceforge.net/projects/nv-tv-out/](http://sourceforge.net/projects/nv-tv-out/))

4 open nvtv-[version]/src/nvtv.c and find the line
 "static OptIntDecl opt_set_list []" and add

  {"TV_Hoffset",      min: -50, max: 50, SET_FIELD(tv_hoffset)}, 
  {"TV_Voffset",      min: -50, max: 50, SET_FIELD(tv_voffset)},
  {"Monitor_Hoffset", min: -50, max: 50, SET_FIELD(mon_hoffset)}, 
  {"Monitor_Voffset", min: -50, mash "/home/bert/documents/scripts/starttv"x: 50, SET_FIELD(mon_voffset)},

  just before "{NULL}" to the array.

-> this way you can specify offset parameters via command line because
on my tv part of the image was not visible and I don't wanted to use the nvtv GUI.

5. save the file

6. compile and install nvtv 
-> see nvtv-[version]/INSTALL for instructions
(configure,make,.. you will need to install some extra packages maybe)

6. make nvtvd to start at boot:
   sudo echo "nvtvd" >> /etc/init.d/nvtvd
   sudo chmod +x nvtvd
   sudo update-rc.d nvtvd start 50 2 .
   Don't know if this is the right way but works for me.
   Maybe you have to check that position 50 is after position of nvidia-glx.

7. Create a file called "starttv" with contents
	xrandr -s 800x600 -r 60
	nvtv -t -r 800,600 -s Medium -S PAL -C SVIDEO --set Monitor_Hoffset:-4

->change resolution and refreshrate so (my) tv can handle it and
start nvtv with parameters needed for your tv, check "nvtv --help" for options.
I used Monitor_Hoffset and not TV_Hoffset for some reason that only works.

8. Create a file called "stoptv" with contents
	nvtv -m
	sleep 1
	xrandr -s 1280x1024 -r 75

->turn off tvout and restore resolution + refreshrate of pc,
"sleep 1" otherwise my screen is not responding.

9. Download my two icons and save them somewhere.
[[IMG]http://img313.imageshack.us/img313/466/tvon2ny.png[/IMG]](http://imageshack.us)
[[IMG]http://img305.imageshack.us/img305/3199/tvoff1ch.png[/IMG]](http://imageshack.us)

10. Add two shortcuts to startv and stoptv together with the icons
on your gnome taskbar. (i.e. sh /home/username/scripts/starttv)

11. Done

PS : On my system I have to leave the s-video cable unplugged
until Gnome has booted, otherwise I have no tvout for some reason.

---

### Post by Bazon on 2006-03-27
Puh, at least one other person realized editing the xorg.conf is not necessary to produce TV-Output! :)

Anyway, **in many cases this How-To can be shortend IMHO**:
*(I discovered it independend from this Howto, if I saw this before, it would have been easier for me, but I only could find it after knowing what to search for....)*

You only have to compile nvtv yourself if you need a TV or monitor offset by parameter!
Because nvtv is in the universe repositories and you can easily install it be Synaptic.
Adding a autostart isn't neccesarry, too, because if you install nvtv by Synaptic, a service nvtvd is automatically started when booting.

**So all I had to do were the following steps:**
[list=1]
[*]**Install *nvtv*** (universe Section) with Synaptic
[*]***optional:*** Play with nvtv to see what setting fits best: Start it with *nvtv* in the terminal and play with the gui. You get command line options with *nvtv -h*. For me, "X-Mode" was neccesarry. Also changing the resolution to 800x600 makes Fullscreen Options (started after resizing!) easier...
[*]**Create two sripts**:
*/usr/local/bin/tv-on* with:
```
#!/bin/sh
#######################
# tv-on changes resolution + switches tv on

xrandr -s 800x600
nvtv -r 800,600 -s Normal -X -t
nvtv -r 800,600 -s Normal -X -g
```(in contrast to the one from SLOMO this provides a GUI Interface, too, so you can readjust if you want...)
and */usr/local/bin/tv-off* with:```
#!/bin/sh
#######################
# tv-on changes resolution + switches tv off

nvtv -m
sleep 1
xrandr -s 0
```*(sleep was neccesarry for me, too.)*
[*]**Add two starters to you panel**:
One with command *tv-on*, the other one with *tv-off* as command. (The icons from SLOMO fit good for this of course....)
[/list]

This was all it took for me, which is really easy I think. *(And anyway safer than editing xorg.conf which also didn't work for me...)*

greetings,
Bazon

---

### Post by keenwerkz on 2006-04-10
i tried working out my twinview to no avail, so i tried nvtv... unfortunately it cant detect my video card.. :(
help

my system:
ubuntu 5.10
amd64 3000
1gig ram
pci-e nvidia gforce 6600
ecs nforce4-a939 k8ht2000 nforce4 mobo

=====
edit - have successfully made my twinview to work an hour after this post (after weeks of trying), i can select clone & rightof.... 

still having thought that nvtv's function is relative to xorg.conf i thought nvtv would be working fine already.. unfortunately still the same error message... "can't find a video card"..  :(

btw... i didn't compile from source i just used the .deb from the repositories... could that be the prob? Would there be settings in the source files that could make this one work? cos i was thinkin' it could probably be pci bus id settings is the cause that nvtv can't detect my card (pci-e)... hmmmm.... hope im right... can sum1 verify.. tnx.. :D

---

### Post by zenwhen on 2006-07-10
This thread needs more love. I am going to be trying it out tonight.

---

### Post by Vlatko on 2006-08-11
when i run nvtv i get the following error:
```
vlatko@vlatko-desktop:~$ nvtv
Fatal: No supported video card found.
```

i have a gainward 6600gt. is there a list of supported cards? maybe a newer version of nvtv on the web, which might support my card?

---

### Post by alienseer23 on 2006-08-15
I have the same problem, GeForce 6200 and nvtv does not for some reason recognize my card.
I use dual monitors, and have the tv connected, all to the same card, to use tv I told nvidia-xconfig to --separate-x-screens, and went into my xorg file and added the tv info. To switch I have to restart x with the 2nd monitor off, and the tv just springs right in. Just restarting x with the 2nd monitor on goes right tot he monior. I would love a way to switch from my 2nd monitor to my tv, without having to restart x, will this how towork for that? I am unclear.

---

### Post by zorkerz on 2006-11-16
Same here "Fatal: No supported video card found."  I have a geforce go 6800 came in my gateway 680.  It is not supported by the main nvidia driver so I have always had driver problems. Gah!

---

### Post by Foxmike on 2006-11-20
Pretty nice work!  I has been added to UDSF [http://doc.gwos.org/index.php/Nvidia_easy_tv_out](http://doc.gwos.org/index.php/Nvidia_easy_tv_out).

Thanks again!

-FM

---

### Post by Temis on 2006-11-24
Hi Slomo, I tried you suggestion but I get also no supported video card(Geforece MX 4000) found. Anything missing? Repositories?

---

### Post by Temis on 2006-11-24
Correction I tried Bazon's procedure.

---

### Post by Sandsound on 2006-12-07
This is SO cool, except for just one little detail... It doesn't work on my "tv" pc :-(
All i get when I run tv-out in a console is :

Defaulting to PAL TV system.
Fatal: Cannot find 'Normal' mode 800 x 600
Please specify as e.g. -r 800,600 -s Large
Defaulting to PAL TV system.
Segmentation fault (core dumped)

It does change resolution thou (from 1024x768 to 800x600) and I can switch back with the command tv-off.

It's an Edgy clean install with Envy-Nvidia driver and a Gforce4200, and I can use the "Nvidia X server settings" to change from monitor to tv, but I would much rather use this method.

---

