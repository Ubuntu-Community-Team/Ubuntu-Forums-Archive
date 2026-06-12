---
title: "Lubuntu 21.10 nice analog clock with second hand?"
date: 2022-03-27
forum: New to Ubuntu
---

### Post by nginmu on 2022-03-27
Lubuntu 21.10, looking for a nice analog clock with a second hand.

I tried buici-clock from muon, it was perfectly good for the purpose (helping me set a wall clock) but wasn't too configurable (wanted to make it a little bigger)

Ideally something I can bring up easily on the desktop via a launcher.

Any recommendations?

Thanks

---

### Post by DuckHook on 2022-03-27
```
duckhook@Zeus:~$  apt show cairo-dock-clock-plug-in
Package: cairo-dock-clock-plug-in
Version: 3.4.1+git20201022.a0d3415c-1build1
Priority: optional
Section: universe/x11
Source: cairo-dock-plug-ins
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Cairo-dock Maintainers <team+pkg-cairo-dock-devel@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 315 kB
Depends: libc6 (>= 2.7), libcairo2 (>= 1.8.0), libdbus-glib-1-2 (>= 0.78), libgl1, libglib2.0-0 (>= 2.14.0), libgtk-3-0 (>= 3.9.12), libical3 (>= 3.0.0), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), librsvg2-2 (>= 2.14.4), cairo-dock-plug-in-data (= 3.4.1+git20201022.a0d3415c-1build1)
Breaks: cairo-dock-clock-plugin (<< 2.4.0~2-1)
Replaces: cairo-dock-clock-plugin (<< 2.4.0~2-1)
Homepage: http://www.glx-dock.org/
Download-Size: 77.4 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: Clock plug-in for Cairo-dock
 A collection of official plug-ins and applets for cairo-dock.
 .
 This plug-in displays time and date in your dock.
 Two views are available : numeric and analogic, based on Cairo-Clock.
 This is compatible with the Cairo-Clock's themes, and you can detach itself to
 be a perfect clone of Cairo-Clock.
 And this supports alarms, and a basic calendar, and allows you to set time
 and date.

```
Cairo-dock is a dependency though. That's a lot of overhead just to run a clock, but you were willing to put up with muon, so I figured you wouldn't mind. It's been more than a decade since I ran it. Don't remember much of the details. It was pretty though.

---

### Post by nginmu on 2022-03-27
Don't mind the overhead of Cairo-dock at all, quite enjoying exploring it. The clock looks great & it's configurable very closely to what I want. Thanks :-)

---

### Post by mIk3_08 on 2022-03-28
> **nginmu said:**
> Lubuntu 21.10, looking for a nice analog clock with a second hand.
I tried buici-clock from muon, it was perfectly good for the purpose (helping me set a wall clock) but wasn't too configurable (wanted to make it a little bigger)
Ideally something I can bring up easily on the desktop via a launcher.
Any recommendations?
Thanks

> **DuckHook said:**
> 
duckhook@Zeus:~$  apt show cairo-dock-clock-plug-in
Package: cairo-dock-clock-plug-in
Cairo-dock is a dependency though. That's a lot of overhead just to run a  clock, but you were willing to put up with muon, so I figured you  wouldn't mind. It's been more than a decade since I ran it. Don't  remember much of the details. It was pretty though.
I agree with DuckHook I already use cairo-dock-clock-plug-in for so long now. And I haven't change it yet since then because I'm comfortable with it. Regards and cheers.

---

### Post by DuckHook on 2022-03-28
Please don't enclose large graphics in posts. It is difficult to read for those using small screens, and some members are still on limited bandwidths. An attachment will suffice.

---

### Post by him610 on 2022-03-28
> wasn't too configurable (wanted to make it a little bigger)
Try this...```

alias bclk='buici-clock -geometry =320x320+724+324'

```
then run *bclk* from terminal
If the clock is not large enough for you, change '320x320' to '640x640'
You can define the alias permanently in .bash_aliases once you decide on the size that suits

[https://imgur.com/9TWrx4f.png]("https://imgur.com/9TWrx4f.png")

---

### Post by nginmu on 2022-03-28
That also works well for me. Is there a way to build - in 'undecorate' from the alias command?

At the moment I only know how to bring it up, then manually right-click and select 'undecorate' from the menu, to remove the title bar and just have the clock itself showing.

Edit.. ooh hang on.. from the readme..

```

 3.1  Borderless Clock

  There is a command line option to suppress the window manager's
  ornaments.

    ./buici-clock --no-ornaments

```

But, I can't seem to get it to work..

```

me@skully:~$ alias bclk='buici-clock -geometry =320x320+724+324 --no-ornaments'
me@skully:~$ bclk
buici-clock: unrecognized option 'no-ornaments'
Try 'buici-clock --help' for usage information.
me@skully:~$ alias bclk='buici-clock -no-ornaments -geometry =320x320+724+324'
me@skully:~$ bclk
buici-clock: unrecognized option 'no-ornaments'
Try 'buici-clock --help' for usage information.
me@skully:~$ alias bclk='buici-clock --no-ornaments -geometry =320x320+724+324'
me@skully:~$ bclk
buici-clock: unrecognized option 'no-ornaments'
Try 'buici-clock --help' for usage information.
me@skully:~$ buici-clock --no-ornaments
buici-clock: unrecognized option 'no-ornaments'
Try 'buici-clock --help' for usage information.
me@skully:~$ buici-clock --help
usage: buici-clock [options]
  -geometry =WIDTHxHEIGHT+OFFSETX+OFFSETY
                       Toolkit option to set size and position of window
  --as-desktop          Set window type to DESKTOP via EWMH
  --as-toolbar          Set window type to TOOLBAR via EWMH
  --as-dock             Set window type to DOCK via EWMH
  --no-override Suppress window manager control by
                       inhibiting override-redirect
  --show-second-hand=0|1 Hide or show the second hand.  Overrides resource.
  --version, -V        Display version and copyright
  --help, -h           Usage message
me@skully:~$ buici-clock --as-desktop
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Value in failed request:  0x40
  Serial number of failed request:  48
  Current serial number in output stream:  49
me@skully:~$ ./buici-clock --as-desktop
bash: ./buici-clock: No such file or directory
me@skully:~$ buici-clock -as-desktop
buici-clock: unrecognized option 'as-desktop'
Try 'buici-clock --help' for usage information.
me@skully:~$ buici-clock -V
buici-clock version 0.4.9 -- Copyright (C) 1997,2007 by Marc Singer
me@skully:~$  

```

Strange.. I had a look through the source code and couldn't see any obvious references to the --no-ornaments command line switch. But it's mentioned again here (from v0.4.8 on?): [https://launchpad.net/ubuntu/+source/buici-clock/0.4.9.2](https://launchpad.net/ubuntu/+source/buici-clock/0.4.9.2)

I'm now quite torn between the simplicity and lightweight of buici, and all the extra goodies that come with cairo-dock! Both are good. But buici seems to use cairo.. does that mean it's actually not that much smaller than cairo-dock, than it first seems?

---

### Post by him610 on 2022-03-29
```

$ buici-clock --help
usage: buici-clock [options]
  -geometry =WIDTHxHEIGHT+OFFSETX+OFFSETY
                       Toolkit option to set size and position of window
  --as-desktop		Set window type to DESKTOP via EWMH
  --as-toolbar		Set window type to TOOLBAR via EWMH
  --as-dock		Set window type to DOCK via EWMH
  --no-override	Suppress window manager control by
                       inhibiting override-redirect
  --show-second-hand=0|1 Hide or show the second hand.  Overrides resource.
  --version, -V        Display version and copyright
  --help, -h           Usage message

```

No mention of 'no-ornaments'
By the way, what you are doing by adding to your original wish list (analog clock) is known in the government as ***requirements creep. ***Requirements creep adds untold billions of dollars to systems developments projects.

---

### Post by mIk3_08 on 2022-03-29
> **DuckHook said:**
> Please don't enclose large graphics in posts. It is difficult to read for those using small screens, and some members are still on limited bandwidths. An attachment will suffice.
Thanks DuckHook. I'll be more watchful the next time I post with photo. Thanks for the reminder. Regards and cheers.

---

### Post by ajgreeny on 2022-03-29
If I run **buici-clock** on my Xubuntu 20.054 system simply using command **buici-clock** with no options I see the clock face without any window-decorations at all, so perhaps this is a difference between gtk and qt libraries that is less simple to overcome on a qt DE like lxqt

---

### Post by yetimon_64 on 2022-03-29
> **him610 said:**
> Try this...```

alias bclk='buici-clock -geometry =320x320+724+324'

```...
This being the first time I've heard of buici-clock I tried this as a session startup entry command and it works like a charm. I've sized and positioned it to replace my "dodgy" cairo-clock set up which was installed from a deb package off the debian repos (as it was no longer included in ubuntu repos). It works so well in conjunction with a devilspie2 lua script that I will now be able to get rid of cairo-clock altogether.

Being on Xubuntu, as ajgreeny notes, I have no decorations to worry about. However other aspects such as opacity, sticking to all workspaces, hiding from both the pager and tasklist etc are looked after with a devilspie2 lua script. Maybe a devilspie2 script with the "undecorate_window" option would remove the windows decorations for the OP.

My startup entry command on Xubuntu ...
```
buici-clock -geometry =232x232+1665+625
```

My devilspie2 lua script for buici-clock, "~/.config/devilspie2/buici-clock.lua" ...```
if get_window_name()=="buiciClock" then
    debug_print "Buici Clock window"
    set_window_below()
    set_skip_tasklist(true)
    set_skip_pager(true)
    set_window_opacity(0.44)
    stick_window()
end
```
If I needed to remove window decorations like the OP needs I'd add the next line to the above lua file ...
```
    undecorate_window()
```
My end result for buici-clock is attached.

---

### Post by nginmu on 2022-03-29
Never heard of devilspie2 till now, but I will definitely investigate. I found a good tutorial on it.. thanks!

---

### Post by him610 on 2022-03-29
@yetimon_64
The reason I settled on buici-clock - I have a system down in my basement along with some exercise equipment. I wanted a large analog clock display to be able to see the clock while I was using my rowing machine. 
To use it, I bring up a terminal, type the alias 'bclk', and begin rowing.

---

### Post by yetimon_64 on 2022-03-29
> **him610 said:**
> @yetimon_64
The reason I settled on buici-clock - I have a system down in my basement along with some exercise equipment. I wanted a large analog clock display to be able to see the clock while I was using my rowing machine. 
To use it, I bring up a terminal, type the alias 'bclk', and begin rowing.
I like it, it is the best replacement option I've seen for cairo-clock so far. It is very similar to the face I was using on cairo-clock so this is a perfect replacement for my usage. I tend to like an analog clock permanently on screen as reading the tiny clock on the top panel is near impossible for me, which is why I am running it from a startup entry. I tend to "lose myself" at times when on the computer, having a clock clearly visible is often a good idea :-).

> Never heard of devilspie2 till now, but I will definitely investigate. I found a good tutorial on it.. thanks!
@OP, it is very handy for all sorts of window manipulations but can be a bit of a handful to get started with. Once you set up an autostart entry for it, setting up rules is as simple as writing a script like I posted above and storing it in the devilspie2 config folder "~/.config/devilspie2". 

Cheers, yeti.

---

### Post by ajgreeny on 2022-03-29
Just as an alternative which may now be totally unnecessary, have you considered using conky for a desktop display showing date and time as I have been for some years now.

I actually have two separate conky displays, one with date and time, the second showing a lot about my system and its resource usage, as shown in the screenshot.

---

