---
title: "Can Ubuntu do this..."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Durandall on 2008-04-23
Hello everyone.  I've upgraded from XP to Hardy Heron on my old PC... and I like it so much, I'd consider upgrading from Vista to Heron on my new PC!  Thing is... I don't know if Ubuntu... or Linux period is ready to do the things I bought the new computer to do.

I need it to:

~Playback Blu Ray discs.
~Run some type of "Media Center" clone.
~Utilize Remote Control input in said Media Center.

and... not a top priority... but, the new PC i bought is a Dell XPS 420, with that handy little LCD on the PC Tower itself.  Currently, I use that to display system temps, and change songs or whatever (When the TV is turned off)  I'd like to use that function in Linux, too.

Another question... if you already know, great - but I can always wait and see.  The official release tomorrow... ubuntu.com says I  can install Ubuntu just like it's a program - inside windows.  I'm curious if it will run like the Live CD, or if it's more like an installed OS.  I mean... can I save things to the Home Folder?

Thanks everyone.  I love the community, and love the OS - it's all fantastic.

---

### Post by SunnyRabbiera on 2008-04-23
Well right now blue ray support is out of our control, there is a way to get blueray working yes but its not easy (yet)
there is a media center like app called mythtv
as for remote, there I cant help you.

---

### Post by timcredible on 2008-04-23
as always, if you're used to windows, the best way to start out and learn/test linux is to install it alongside windows.  put the ubuntu cd in while running windows and let the wubi installation do it's thing, then you can play around with ubuntu while still having windows - no reason to not have both available.

---

### Post by hellomoto on 2008-04-23
Im not sure about blue ray disks.

But good media software for Ubuntu is MythTV:
[http://mythtv.org/modules.php?name=MythFeatures]("http://mythtv.org/modules.php?name=MythFeatures")

---

### Post by Dark Aspect on 2008-04-23
> **Durandall said:**
> Hello everyone.  I've upgraded from XP to Hardy Heron on my old PC... and I like it so much, I'd consider upgrading from Vista to Heron on my new PC!  Thing is... I don't know if Ubuntu... or Linux period is ready to do the things I bought the new computer to do.

I need it to:

~Playback Blu Ray discs.
~Run some type of "Media Center" clone.
~Utilize Remote Control input in said Media Center.

and... not a top priority... but, the new PC i bought is a Dell XPS 420, with that handy little LCD on the PC Tower itself.  Currently, I use that to display system temps, and change songs or whatever (When the TV is turned off)  I'd like to use that function in Linux, too.

Another question... if you already know, great - but I can always wait and see.  The official release tomorrow... ubuntu.com says I  can install Ubuntu just like it's a program - inside windows.  I'm curious if it will run like the Live CD, or if it's more like an installed OS.  I mean... can I save things to the Home Folder?

Thanks everyone.  I love the community, and love the OS - it's all fantastic.

To be safe I'd say use Dual boot,How ever here is some documentation about blu ray:

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")

As for the Linux inside windows I am assuming thats like a virtual machine which means you could have a Home folder but you wouldn't be able to use 3D graphics.

I am kind of curious to know if that feature is a virtual machine and if you can use network drives to see the windows data,like in Vbox.

---

### Post by ivze on 2008-04-23
I have some ideas about HD content from blueray disks. As far as i know, the stuff is highly encrypted to prevent us from copying it. 
(see [http://en.wikipedia.org/wiki/BlueRay](http://en.wikipedia.org/wiki/BlueRay) || Digital rights management (DRM))

Vista has all the means to protect the content (or content decryption key) from us, even Vist administrator can't do some things. (By the way, that's why it is so slow :)). 
Ubuntu, as every other GNU/Linux, is completely transparent to it's administrator, so i doubt that playing DRM Protected video from Buleray disks is possible on it. 

I may not be right, but that's what i know. Folks, correct me, if i am not right.

---

### Post by wannadumpwindows on 2008-04-23
Depending on the remote you have, it might be possible with some tinkering. Some models work, others don't. It looks like the others know a lot more about blue ray than I, can't really help you there. But everything else should be possible, I can use my palm pilot for an extra display, so I see no reason you shouldn't be able to use your LCD, once you figure it out. LoL. Wish I could point you in the right direction a little better, but I haven't gotten that far yet.

---

### Post by Rinzwind on 2008-04-23
BluRay: at the moment playback is not possible.
With UDF-Filesystem2.5 you can mount a BD and use it to read (and write with a burner) data from (to) it. So if you have a burner you can save about 25 Gb of data on 1 disc and load software from it (anything you can do with a cd or dvd except watch a movie you bought on BD).

But if it's a BluRay with a known serial (just as some info: if it's a version 3 BD or lower you can rip it) you can use a programm called
HDDump and
AACSKEYS with some keys and
UDF2.5
to rip the dvd and make a file you can play in VLC.
(we used to do that with dvd too before the dmca was found.
(I used it as a test to rip the bond movie Casino Royal and got a directory about 25 Gb big just for the movie but it worked ;) )

Remote: I have a remote with my dell and it worked out of the box.
All a remote does is emulate the buttons on your keyboard. So if it doesn't work you are more than likely to make your own keyboard shortcuts.

Installing: you can run a live cd or install it inside a virtual machine (like vmware/virutalbox/virtual machine) on windows.

---

### Post by mlentink on 2008-04-23
> **Durandall said:**
> 
Another question... if you already know, great - but I can always wait and see.  The official release tomorrow... ubuntu.com says I  can install Ubuntu just like it's a program - inside windows.  I'm curious if it will run like the Live CD, or if it's more like an installed OS.  I mean... can I save things to the Home Folder?


Yes, you can save things to your home directory. The method uswed is called Wubi, and you may be able to find some more info [here]("http://wubi-installer.org/"). It installs a 'virtual partition' by reserving a part of your ntfs drive as a wrapper to install the ubuntu filesystem in. then it adapts your your sequence to allow you to boot directly into ubuntu. No virtual machine, the real thing. Advantage: if you decide to get rid of ubuntu, the only thibg that happens is the deletion of a file within windows. Disadvantage: no precise control over your partitions.


btw, there's even a [Mythbuntu]("http://cdimage.ubuntu.com/mythbuntu/releases/8.04/rc/"), as far as I remember.

---

