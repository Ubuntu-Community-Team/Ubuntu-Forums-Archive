---
title: "idea: xtools - cli and gui x config tools"
date: 2007-07-10
forum: Programming Talk
---

### Post by Choad on 2007-07-10
i love the way linux does stuff in text files, it makes it very easy to see what's going on and easy to change stuff and easy to fix stuff... but this is no good for joe user who is wondering why s/he can't get his/her monitor to display at it's native resolution or whatever

so heres my idea for a useful project.

firstly, create a cli program that edits the xorg.conf file for you. instead of going in to the text file and hacking about, the program will retrieve information for you and spit it out to the console, and also can add or edit individual parts of the xorg.conf file

my reasons for this are that there is no standard way of interfacing with this most critical system file, and it doesnt have a very rigid structure. useful in that it doesnt throw errors if you have server layout at the beginning or the end, but not useful when a program wants to interface with it and *it* has to discover where the server layout is. it's obviously very possible for a program to do this (thats exactly what this program would do) but its a complete hassle when all you want to do is add an entry to the server layout without borking the file completely

the nvidia-settings tool, for example, completely disregards what you currently have and just overwrites everything with it's own stuff, which got rid of synaptics support for my mouse and therefor pissed me off. if the nvidia settings tool was re-written to use these xtools then it wouldnt have to be so ignorant of other modifications to the x config.

secondly, i was thinking to create a gui app that wrapped the cli app meaning joe user could finally add that 1280x800 resolution with a click click click


what do you people think? good idea? bad idea? already been done idea?

---

### Post by kidders on 2007-07-14
Hi there,

"Already been done idea", I think. Or at least sort of. You see, there's only *so* friendly & graphical such a program can be :-(

Having said that, I wonder if it would be possible to create a program (even a script) of some sort that could take a new (ie more intelligent than usual) approach to X configuration. For instance...

**Input devices:**

Take my box as an example. I'm using an Apple Bluetooth keyboard, bluetooth Mighty Mouse and a 10-button RF mouse. As you might imagine, it's taken quite some fiddling to get everything purring away the way I want it.[LIST]
[*]I had to set up new udev rules to have my keyboard & bluetooth mouse recognised reliably.
[*]I had to identify the appropriate axis mappings for my mice (mouses? I've never been quite sure!)
[*]I had to make manual modifications to various apps (eg compiz) to give my extra mouse buttons some useful functionality.
[*]I had to tinker endlessly with keyboard maps to get my rather odd US/Ireland/UK hybrid keyboard layout to behave sensibly, without upsetting a USB keyboard I also use on occasion too much.
[*]And so on...[/LIST]When I read your post, I got to thinking that surely it's not beyond the bounds of credibility to suggest that a lot of this could have been done *for* me by a smart enough configurator.

**Graphics:**

In graphics terms, I'm an easy job. EDID information sorts my monitor out, with almost no configuration at all, and I only have one of them, cutting out a whole minefield of unbridled horror. Having said that, I wonder if a clever configurator could be made to collect, say, ten possible monitor/card configurations that are likely to work, order them by preference, and test each one for a few seconds, until the user accepts one. Maybe by varying font resolutions, hinting, refresh rates, direct rendering support, and so on, it would be possible to ask users which setup *looks* best, without having to expose them to the specifics of xorg.conf at all.


The main problem with things like this is that none of them could depend on X to run, imo. What do you think of my ideas? Completely off the wall, I suspect lol.

---

