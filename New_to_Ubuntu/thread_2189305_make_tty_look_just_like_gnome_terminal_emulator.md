---
title: "make tty look just like gnome terminal emulator"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by 7gwpwv3bed5c855k on 2013-11-21
I like the look and feel of gnome terminal emulator and was wondering if I could reproduce the same exact appearance on tty "serial" terminal without any GUI as if I were running gnome terminal emulator full screen ("CTRL+ALT+T" followed by "F11"). 

Thanks,

Eric

---

### Post by JKyleOKC on 2013-11-21
Unfortunately, no. The look and feel which you like are provided by the window manager, which in turn requires the X Windows server, and those aren't active when you're in the plain tty console. You could launch them, usually by the command "startx" after logging in, but this would be only a roundabout way of getting the same action that you're wanting to sidestep.

If you're simply wanting to avoid the two sets of keystrokes to get to a full-screen terminal emulator, you could create a small script to issue the keystrokes, and launch it from the autostart options. However I use Xubuntu rather than Gnome Classic, so cannot help with details of such a setup...

---

### Post by 7gwpwv3bed5c855k on 2013-11-21
Thanks for the clarification. In fact, I am trying to run minimal ubuntu  without any desktop environment/display server within a virtual  machine. I know a little about linux framebuffer and was wondering if it  could do the job. Anyway I could end up with gnome-terminal emulator-only desktop.

---

### Post by DuckHook on 2013-11-21
A terminal emulator and a tty are two very different beasts. There are a few ways to get more snazziness out of your typical tty, but they involve using the framebuffer, which is halfway to running X.

Most who work in a pure console are looking for functions other than eye-candy.

Basic apps like *ssh, sftp, lftp, nano, vim, rsync, htop, iotop, etc* are indispensable.

Try *byobu* or *dvtm* for a shell enhancement that tiles multiple screens and gives system info like path, free memory, cpu load and time with both header and footer panels that can be switched on or off.

Try *screen* or *tmux* for really powerful functions like detaching sessions, multiple sessions, etc.

Try *fbterm* for eye-candy like using truetype fonts in lieu of system fonts, rotating console, etc. It should be noted that the "fb" in fbterm stands for "frame buffer". In other words, you are already working in a quasi-graphical environment by invoking fbterm.

A final thought: I'm slowly working more on the console and I find that I'm actually preferring it over *any* terminal emulator. There's a stark simplicity to the console that is calming and zen-like, at least for me. And each discovery of a new/old console app that effectively substitutes for the functionality of a bloated GUI app is like unearthing a really cool gem or fossil. In addition to the apps already mentioned, you may wish to explore:

w3m, lynx, links or links2: web browsers (some with frame buffer graphics)
mutt: e-mail client
naim, Bitlbee: chat clients
fbi: pdf reader
mc: file manager
rtorrent: torrent client
CMus, MOC, mpg123, mplayer: music players (many others too)
vlc, mplayer, Mpv xine: video players (using framebuffer)
wget, curl: download managers

The console world is endless. After getting lost in it, you won't remember why you even wanted to constrain yourself to a terminal emulator.

---

### Post by 7gwpwv3bed5c855k on 2013-11-22
Thanks for your really helpful suggestions. Maybe fbterm is the best available option right now. However, despite all shell enhancements that may be derived from fbterm I am still not getting the same look and feel that I am looking for. So, I am thinking of running gnome-terminal emulator as the root window instead of gnome-shell but I am not sure if it is possible to do so.

---

### Post by DuckHook on 2013-11-22
> **7gwpwv3bed5c855k said:**
> ...I am thinking of running gnome-terminal emulator as the root window instead of gnome-shell but I am not sure if it is possible to do so.I wouldn't know how to do it even if it were possible. Even if achieved, it seems like such a waste of resources though. Like opening up and running a restaurant just so you can have lasagna. You would have to drag in all of X, then all of Gnome--just to run a terminal emulator? If you did a PS, you would find your graphical processes dwarfing your core processes by ten to one. I suppose that it offends only minimalists like me. Most modern computers have room to spare.

Out of curiosity, I simulated such an install on my minimal console-only VM:

xorg pulls in 88 packages
gnome-terminal then pulls in another 122

That's a minimum of *210* dependencies and who knows how much in memory/services/drivers to run a terminal emulator. But hey... Linux is about choice... so let us know how it goes.

---

