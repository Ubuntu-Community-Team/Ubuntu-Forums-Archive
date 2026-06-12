---
title: "[SOLVED] CLI alternatives and minimalistic WM"
date: 2008-01-27
forum: Other OS Talk
---

### Post by sujoy on 2008-01-27
I already have ubuntu in my laptop and wanted something different for the desktop.Hence, after a long day of many installations, I am now going for an arch setup :)

I just want to give it a minimalist bare look. So I am looking for a lot of CLI applications.
[LIST]
[*]music player (mp3,ogg,wav,etc..)
[*]video player (avi, mpeg, vob, mp4, etc)
[*]chat client (for use with gmail account)
[*]file browser
[*]torrent client
[*]cd/dvd burner
[/LIST]

and a lean browser (cant do with links or lynx because of youtube ), a simple graphical login screen (any option other than gdm ?)
also what terminal to use?

as for window manager, i have heard a lot about fluxbox, openbox and awesome thesedays, which one would be better for me?:confused:

my only requirement for the WM is that it should allow me to add/remove panels, icons and menu as and when i need to.

sorry if I am asking too many questions :)

---

### Post by Tenken on 2008-01-27
Music - MPD + NCMPC or MPC
Video - mPlayer works from the command line
Chat - Finch (a command line version of pidgin)
Filesystem - cp, mv, rm, etc
Torrent client - transmission
Browser - Swiftfox is nice, an does flash with no problems.
Terminal - rxvt-unicode (urxvt) is a popular choice, I use xfce-terminal because it can use tabs.

As far as WM's, most don't come with panels or the ability to use desktop icons. You can install a separate panel like pypanel or fbpanel to work with your WM, and iDesk to create desktop icons. Openbox has a nice menu editor called Obmenu.

---

### Post by mssever on 2008-01-27
[LIST]
[*]For a light window manager, I prefer IceWM.
[*]For audio, play can handle most anything. I don't remember what package it's part of, but if you type play at the command line, command-not-found will tell you.
[*]Browser: elinks for non-graphical stuff (much better than links) and epiphany (package: epiphany-browser) when you need YouTube.
[*]For a terminal, I use Gnome Terminal, but there are others. If you're adventurous, you might even be able to make xterm do what you want.
[*]File browser: bash
[*]CDs and DVDs: The only clients I know are GUI. Of course, the GUIs call CLI programs, but I don't know those commands, and it can be tedious to type those commands all the time. Look through Synaptic and see if there's anything like that available.[/LIST]

---

### Post by sujoy on 2008-01-27
bash and the cp, mv commands are good enough, but maybe i can still find a light weight file-browser.

epiphany will bring in the gnome libs i guess? i really want to keep it simple. :)

also, what login manager do we have other than gdm, thats minimalistic in approach?

---

### Post by Lord Illidan on 2008-01-27
file browser? rox or pcmanfm

web-browser - lynx

---

### Post by urukrama on 2008-01-27
**Login manager**: Slim. 
**File Manager**: mc
**Audio**: mpd + ncmpc
**Torrents**: rtorrent

The window manager really depends on your tastes. I prefer Openbox or Pekwm, but you may prefer Icewm or dwm. Why don't you try them out and then decide which you like best?

If you like graphical clients, here is my list:

**File Manager**; Thunar, PCManFM, Xfe, rox-filer or Emel2fm
**Audio**: mpd + gmpc
**torrents**: rtorrent :-)
**Browser**: epiphany or kazehakase

---

### Post by mali2297 on 2008-01-27
Torrent client: rtorrent
File browser: midnight commander (or just the shell)

---

### Post by sujoy on 2008-01-27
wow! thanks for all the response

mc looks like just the thing i was hoping for. :) 
will try out and report back.

---

### Post by RedSquirrel on 2008-01-27
> **sujoy said:**
> also, what login manager do we have other than gdm, thats minimalistic in approach?

minimalist: don't use a display manager at all. I just login on the console and run startx from there (I run 'x', which is my handy alias). Setup a nice ~/.xinitrc and you're done. ;)

For a terminal, I use uxterm.

For burning, you can use the tools directly (wodim).

If you're trying to keep it light, I would recommend staying away from anything tied to a desktop environment. Check dependencies very carefully before installing anything.

---

### Post by sujoy on 2008-01-27
yes i agree
however, i would like to login to x by default, rather than having to do a startx everytime.

---

### Post by mali2297 on 2008-01-27
> **sujoy said:**
> yes i agree
however, i would like to login to x by default, rather than having to do a startx everytime.

That's easy, add this to the end of **~/.profile**:
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
  startx
fi

```

---

### Post by Tenken on 2008-01-27
I would agree with urukrama's recommendation of SLiM. It only has a few dependencies and supports (experimentally :)) logging into multiple desktop environments/window managers.

---

### Post by sujoy on 2008-01-27
> **mali2297 said:**
> That's easy, add this to the end of **~/.profile**:
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
  startx
fi

```

can u kindly explain the code snippet?

---

### Post by y-lee on 2008-01-27
You may be interested in reading [A day without X]("http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/")


> Would you be able to survive one full day without using the X server? Linux offers us a wide assortment of CLI based tools which use curses and/or framebuffer for functional user interfaces. There is no reason why you shouldn’t be able look up stuff online, read your email, look at pictures, watch movies and listen to music as you are trying to configure X.

---

### Post by mssever on 2008-01-27
> **sujoy said:**
> can u kindly explain the code snippet?

> **mali2297 said:**
> That's easy, add this to the end of **~/.profile**:
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
  startx
fi

```

First, it checks whether the environment variable $DISPLAY is set. If not, then X probably isn't running right now. If $DISPLAY is unset (literally, if the length of its value is zero), then it checks the output of the tty command (see the man page) to see if it's running on the first virtual console. If so, it runs the command startx.

---

### Post by kadath on 2008-01-28
BashBurn works well for burning CDs and DVDs.

[http://bashburn.sourceforge.net/](http://bashburn.sourceforge.net/)

---

### Post by Rumor on 2008-01-28
@sujoy:
You might be interested in perusing this thread in the Arch forums. It offers quite a variety of very lightweight, minimalist applications, several of which I use on my old P2/233 laptop that runs Arch.

[http://bbs.archlinux.org/viewtopic.php?id=41168](http://bbs.archlinux.org/viewtopic.php?id=41168)

---

### Post by sujoy on 2008-02-08
hey guys! 

i installed mpd+ncmpc

but when i go to browse i dont see any files :confused:
i have one mp3 in the music_directory, but nothing shows up

---

### Post by Tenken on 2008-02-08
Have you created the database yet?

```
mpd --create-db
```

---

### Post by dewey on 2008-02-08
Nice to see a fellow arch user.

I recently switched from xfce4 to fluxbox, and am in much the same situation.

Here's what I've personally chosen so far.

Music Player - mpd with Sonata front end
video player - mplayer
chat client - pidgin
file browser - Rox (You can even get it to control the desktop)
Torrents - Transmission
Web browser - firefox-nightly (firefox3 from AUR)

And for a login manager that's lightweight, try SLiM.
[http://slim.berlios.de/](http://slim.berlios.de/)

---

### Post by Nythain on 2008-02-09
i generally run fluxbox with cli apps in thier own transparent terminals... here's my setup:
Music - mpd + ncmpc (mpc works just as well)
Video - mplayer
Chat - centericq now called centerim (actually centerim is a fork, but its in the repos now instead of centericq)
File Browser - Midnight Commander (mc in the repos) ncurses file browser/manager with an old "commander" style interface
Torrents - rtorrent... THE BEST torrent client i've found to date
Web browsing - i cheat and use FireFox, but i've used all the cli ones before... i think its elinks or links2 that has image support too

there's other popular cli apps, in fact there's an entire thread on here or two dedicated to discussing the different cli alternatives to things :P

---

### Post by kerry_s on 2008-02-09
> **sujoy said:**
> I already have ubuntu in my laptop and wanted something different for the desktop.Hence, after a long day of many installations, I am now going for an arch setup :)

I just want to give it a minimalist bare look. So I am looking for a lot of CLI applications.
[LIST]
[*]music player (mp3,ogg,wav,etc..)
[*]video player (avi, mpeg, vob, mp4, etc)
[*]chat client (for use with gmail account)
[*]file browser
[*]torrent client
[*]cd/dvd burner
[/LIST]

and a lean browser (cant do with links or lynx because of youtube ), a simple graphical login screen (any option other than gdm ?)
also what terminal to use?

as for window manager, i have heard a lot about fluxbox, openbox and awesome thesedays, which one would be better for me?:confused:

my only requirement for the WM is that it should allow me to add/remove panels, icons and menu as and when i need to.

sorry if I am asking too many questions :)

music player = depends, if all you want to do is hear the music, "aplay" is enough to play it, it's part of alsa-utils, if your using alsa you most likely have it already, if you want a gui front end "alsaplayer"

video player = if you need a video player, than you should just get something that does it all, "vlc" is king, music, movies, all in 1 player

chat client = no clue, i use "meebo.com" in my browser.

file browser = "mc" is browser & editor, "rox & leafpad" if you need more

torrent client = just good old "bittorent"

cd/dvd burner = you can always command line it, but for ease "brasero"

lean browser = "firefox" is king, but i did try 1 recently thats fairly light and rendered web pages right. [http://tkhtml.tcl.tk/hv3.html](http://tkhtml.tcl.tk/hv3.html)
make sure you have libstdc++5. grab the tgz unpack and go. it's a single executable, so i hope you know how to do manual installs, i renamed it just hv3 for convenience. linked it to /usr/bin but left it in my ~/.hv3

graphical login screen = ditto, i don't use none. in debian auto log in is easy.
```
/etc/initab
1:2345:respawn:/sbin/rungetty tty1 --autologin user

~/.bash_profile
if [ `tty` = "/dev/tty1" ]; then
startx
fi
```

window manager = i'm "jwm" all the way, i just find it so very easy to get what i want.
> my only requirement for the WM is that it should allow me to add/remove panels, icons and menu as and when i need to.
yep, it does that, but you have to manually do it.

you just have to find your sweet spot, try many things, write down the things you like, that will make your custom install easier.
here's pics of mine, all done from 1 settings file(.jwmrc)->

---

### Post by sujoy on 2008-02-20
Finally, i have my minimal system all set up, 

Distro: Arch Linux
Window Manager: Openbox (with obmenu,mmaker and obconf)
File Manager: Thunar and mc
Web Browser:Opera and elinks
Music Player: Audacious and mpd+ncmpc/sonata
Video Player: VLC and mplayer
Editor: vim
Login Manager: Slim
Email: mutt (still need to set it up)
Chat: irssi + bitlbee
Torrent : rtorrent
Picture: gimp, ristretto, nitrogen and feh
Pdf: epdfviewer and fbg(for viewing pdf without xserver)

Any feedback?

Thanks everyone for helping me out :) Cheers.

---

### Post by kerry_s on 2008-02-20
sounds like you got a winner.
screen shot?

i'll show you mine. :)

jwm, setup in the gnome style

---

### Post by chris4585 on 2008-02-20
this is my list i came up with, i've not really finished it, but it does list a bunch of software

[http://ubuntuforums.org/showthread.php?t=684281]("http://ubuntuforums.org/showthread.php?t=684281")

---

### Post by jseiser on 2008-02-21
WM - Evilwm + dmenu
File Manager - Bash and MC
terminal - xterm 
music - cplay + mpg123
p2p - rtorrent
chat - irssi
volume - alsamixer
images and background setting - feh
web browser - kazehakase - set up a script to empty history

then just use screen to launch those programs, you can even tell screen to always launch those programs when u launch screen.  So you turn ur PC on, evilwm comes on, hit your keybind for screen and bam.  All you programs are open, do what you want, detatch screen, ssh in from work, detetch, re attatch at home.  I mean, you can do anything you want with those programs.  I don't see a need for a toolbar or panel or icons etc.  They are minimalist, they do not allow you to work better or faster.  They just waste resources imho.

---

### Post by RedSquirrel on 2008-02-21
> **sujoy said:**
> Finally, i have my minimal system all set up, 

...

Video Player: VLC and mplayer

...

Any feedback?

Thanks everyone for helping me out :) Cheers.

Looks pretty good. mplayer from [extra] hasn't been patched. See:

[http://bbs.archlinux.org/viewtopic.php?id=43461](http://bbs.archlinux.org/viewtopic.php?id=43461)

There's a link to the bug report in that thread as well.

---

### Post by chochem on 2008-03-02
Interesting thread... Does anyone know if rtorrent does rss downloads? Or is there a script setup for that? Possibly in conjunction with some cli torrent site parsing? It would be cool if the route from thinking about something you wanted to download and it actually being on its way was a matter of a command or two :)

And on another note: I like MPD+MPC but it does't seem like it's being actively developed, does it? At least MPC... You can always add a bit of functionality by bash scripting but they don't tend to be pretty (maybe that's just cause I'm a hack at bash scripting :) )

---

### Post by stream303 on 2008-03-03
Quick cli random note-taker:
HNB - a hierarchical notebook

Simple file / directory browsers AND app launchers:
Lynx
Elinks
ie
```
lynx /usr/share/doc
```

I always forget how useful this is when even midnight commander could be overkill.  They're not just for web-browsing! :)

I once tried to adapt a mua like Mutt or Pine just to collect notes to myself without turning it into a mailer, but just didn't have the knowledge to keep it from trying to actually mail something. :)

If anyone knows how to dumb-down mutt or slrn so that it becomes just an offline random searchable note-taker without becoming an active mua or newsreader, I'd be eternally grateful!

---

### Post by chochem on 2008-03-08
Oh well, I 'll try something else... I checked out the various chat clients mentioned in this thread and found that they were all more 'text interface' and less 'command line interface' - in short you 'enter' the program and it then occupies your terminal. I was wondering if there wasn't something more MPD-MPC-ish? You'd log on and the connection would stay in the background, only to be interacted with by commands, like "[send message] [recipient] [message]" or "[show buddy list]"?

---

### Post by sujoy on 2008-03-08
hmm.......that would be great. a real command based chat client .......

---

### Post by chochem on 2008-03-08
Actually I found [this thread]("http://ubuntuforums.org/showthread.php?t=121456") but I'm not really sure it's a complete chat prorgam as much as a solution to a more narrowly defined problem...

---

### Post by chris4585 on 2008-03-08
weechat > chat program

---

### Post by cardinals_fan on 2008-04-19
> **Tenken said:**
> xfce-terminal because it can use tabs.

Rxvt-unicode (urxvt) can use tabs too...

---

### Post by LaRoza on 2008-04-19
> **sujoy said:**
> hmm.......that would be great. a real command based chat client .......

Finch (IM). I use it. 

If you have Pidgin, it uses the same backend (purple) and will have all the settings of Pidgin (all the accounts)

For IRC, use irssi, great program.

---

### Post by sujoy on 2008-04-19
great, will install it right away :)

---

### Post by eriqjaffe on 2008-04-21
> **cardinals_fan said:**
> Rxvt-unicode (urxvt) can use tabs too...I use [mrxvt](http://materm.sourceforge.net/), personally, which also supports tabs.

---

### Post by chochem on 2008-06-09
I don't know if it's already been name dropped but the transmission-daemon has the speed of transmission (unlike rtorrent) and is really easy to use (also unlike rtorrent). Of course it doesn't have as many advanced features as rtorrent - on the other hand it's a daemon, not an ncurses app, which is probably my most wanted feature. 


In sort of a follow up on my own post ( yeah i know, talking to yourself means you're going crazy... ;) ), I also did a piratebay.org command line browser that allows me to browse, search and download, and then serve the torrent file to the daemon, so I don't need to wait for firefox to get started, just to start a torrent. I put it up [here]("http://bash.viharpander.dk/#pb") if anybody's interested.

---

### Post by unutbu on 2008-06-09
```
text editor:   	    emacs
image viewer:  	    emacs
terminal:      	    emacs (M-x shell)
file manager:  	    emacs (dired)
mail reader:   	    emacs (M-x rmail)
chat client:   	    emacs (M-x irc)
news reader:   	    emacs (M-x gnus)
web browser:   	    emacs (M-x w3)
rss feeder:    	    emacs (M-x newsticker-show-news)
calculator:    	    emacs (M-x calc)
url downloader:     emacs (url-retrieve)
manual reader:      emacs (M-x man)
spreadsheet:        emacs (M-x ses)
diff/merge:         emacs (ediff,ediff-directories)
date/time clock:    emacs (emacs mode line)

```
:lolflag:

---

### Post by sujoy on 2008-06-09
> **chochem said:**
> I don't know if it's already been name dropped but the transmission-daemon has the speed of transmission (unlike rtorrent) and is really easy to use (also unlike rtorrent). Of course it doesn't have as many advanced features as rtorrent - on the other hand it's a daemon, not an ncurses app, which is probably my most wanted feature. 


In sort of a follow up on my own post ( yeah i know, talking to yourself means you're going crazy... ;) ), I also did a piratebay.org command line browser that allows me to browse, search and download, and then serve the torrent file to the daemon, so I don't need to wait for firefox to get started, just to start a torrent. I put it up [here]("http://bash.viharpander.dk/#pb") if anybody's interested.

usefull piece of code :), haven't tried it yet though.

---

### Post by zmjjmz on 2008-06-12
If you want to be _really_ minimalistic you can eschew X altogether and use twin.
[http://twin.sourceforge.net](http://twin.sourceforge.net)

---

### Post by sujoy on 2008-06-13
> **zmjjmz said:**
> If you want to be _really_ minimalistic you can eschew X altogether and use twin.
[http://twin.sourceforge.net](http://twin.sourceforge.net)

twin would do great except that i like watching movies in X rather than framebuffer, i am quite happy now with my awesome,xmonad and openbox setup. yes, thats too many WMs but i like them all :)

---

