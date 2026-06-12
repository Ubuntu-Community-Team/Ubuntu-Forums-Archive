---
title: "some persistent problems in my hardy-installation"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by hypertonic on 2008-05-24
Hi,
last month, I installed ubuntu with a few bugs and problems, that with searching and trying since then still haven't gone. I very much hope some of you take the time to see what these problems are and suggest an solution. I ordered them by seriousness (in my opinion).

1. I can't shut down properly.
Every time I want to log off, shut down, switch user,... my desktop freezes with only the desktop background and my mouse showing. The only way I can continue is to manually _shut down_ by pressing the power button on my computer, which isn't really healthy for my hardware. I've been doing this for a month now, and I'm starting to feel the impact on my laptop (programs not working properly, having to reboot because something crashes...), so I really need a solution.

=> What I've tried:
- First of, I had that network-manager-bug, described [here]("http://ubuntuforums.org/showthread.php?t=603054"). I tried everything they said there, but nothing worked. I then removed network manager and replaced it with WICD. The whole networkmanager-error-list, is gone, but it still freezes.
- Now, when I want to shut down, it still freezes, and when I push the power-button, it just show some commands, ending with 'running .../.../rc.local', after which it jumps to ubuntu splash screen with the progress bar. Note that it only continues with the shutdown after I push the powerbutton!

2. Firefox just shuts down with every streaming media website.(youtube-like websites)
I installed ubuntu, went to youtube and installed Shockwave Flash. Not a problem, accept that it just shuts down firefox after 1, maybe 2, sometimes even loading the first video I want to see on youtube. It's just unable *not* to shutdown firefox while I want to watch, say, a 4-part top gear special (awesome program by the way) on youtube.

=> What I've tried:
Everything that comes up when searching google for "ubunty hardy firefox shutdown youtube shockwave".

3. Soundcard multitasking
Now, this isn't really a bug, I was just hoping to find away past it. It always bothered me that ubuntu is unable to divide attention between two or more sound-producing programs. When I'm listening to music in Rhythmbox, and I want to watch a video on youtube (given that that works :-p), I can't just pause Rhythmbox, leave it running and start youtube. I really have to shut down every program that *might* be using the soundcard, before I can do something else, which is just, annoying actually.

=> What I've tried:
Nothing, since nobody else seems to have a problem with it, I can't find any solutions!

---

### Post by alienexplorers on 2008-05-24
For number 2 do you have the plugin symbolic link installed in the plugins folder in /home/yourname/.mozilla...  The symbolic link should look like this:
> libflashplayer.so

For number 3 if I am listening to mp3 music in Rhythmbox and go to you tube to view videos the sound comes out interlaced.  I get my music and the sounds from the videos coming out of the speakers at the same time.

---

### Post by hypertonic on 2008-05-24
libflashplayer.so is there, and in my case, rhythmbox doesn't want to start playback (giving an unknown error) when youtube is open.

---

### Post by BC7333 on 2008-05-24
[http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)

might explain your flash problems.  Have experienced similar here.  The browser just seems to closeout and that's it.

Regarding shutdown, I've noticed this too.. sometimes can take 30 seconds after the 'freeze' you describe for the shutdown window to open.  Still looking for a solution.  Sometimes works, sometimes not.

---

### Post by hypertonic on 2008-05-25
I tried last night to see if it is a stall or a freeze. I shut down my computer and went to bed without manually shutting down. It's now 8 hours later, and it was still frozen...

---

