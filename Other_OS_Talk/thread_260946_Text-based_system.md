---
title: "Text-based system"
date: 2006-09-19
forum: Other OS Talk
---

### Post by K.Mandla on 2006-09-19
After tinkering with [this machine]("http://www.ubuntuforums.org/showthread.php?t=259901") for a few days, and seeing how miserable it was laboring under X but how perky it was without it, I began to wonder how much can be accomplished without a graphical system.

As far as I can see, so long as you're not into photo editing or digital rendering, there are quite a few things that you can still get done without X and a GUI. [mpd]("http://packages.ubuntu.com/dapper/sound/mpd") and/or [mpc]("http://packages.ubuntu.com/dapper/sound/mpc") and/or [ncmpc]("http://packages.ubuntu.com/dapper/utils/ncmpc") come to mind, for purposes of audio playback. There are [links]("http://packages.ubuntu.com/dapper/web/links") and [w3m]("http://packages.ubuntu.com/dapper/text/w3m") and the like for Web access -- sans images, of course. But that should be enough to check your email or read the news. 

So anyway ... the queestion is more or less distro-independent. If you have ideas for a text-based system and what you'd use on it, I would like to hear them.

---

### Post by croak77 on 2006-09-19
irssi, fetchmail, procmail, msmtp, mutt, snownews, rtorrent, cmus, wget, mc, nano, vi, elinks, and hnb. All are in the repo's accept cmus which is here but mpd/ncmpc-svn is great too.

Also if you use framebuffer you can use mplayer, image viewers like fbida and links with images.

---

### Post by skymt on 2006-09-19
^^ What he said, plus slrn. ^^

---

### Post by croak77 on 2006-09-19
I forgot a couple I use, cdrecord, abcde, giftcurs, naim, lftp and netris.

---

### Post by 3rdalbum on 2006-09-20
You can use a program called MPlay, which gives you an Ncurses interface to Mplayer.

Links2 gives you graphics through the framebuffer:

sudo links2 -g -mode 1024x768x32K

---

### Post by K.Mandla on 2006-09-20
> **3rdalbum said:**
> Links2 gives you graphics through the framebuffer. ...
Now that's slick. Any ideas on how to get the mouse to work? I'd hunt it down myself, but I have to get some sleep ... :(

---

### Post by croak77 on 2006-09-20
Mouse should work if you have GPM running.

---

### Post by Rhapsody on 2006-09-20
After finding that I liked Irssi, I've thought about installing some others apps to work from a terminal (partly just for fun) and found that IRC (with [Irssi](http://en.wikipedia.org/wiki/Irssi), of course), web browsing (with [w3m](http://en.wikipedia.org/wiki/W3m) - which is actually capable of displaying images in a suitable terminal - or others), and even BitTorrent (with [rTorrent](http://en.wikipedia.org/wiki/RTorrent)) were quite doable.

I don't know about others since that's most of what I'd want to do (except music, but I can do basic operation of Amarok with keyboard shortcuts).

---

### Post by croak77 on 2006-09-20
You should check out mpd and ncmpc it really pretty good. Has a great feature list.

```

Features
Plays MP3, Ogg Vorbis, FLAC, MP4/AAC, Mod, and wave files
Remotely control MPD over a network (IPv4 and IPv6 supported)
Play MP3 and Ogg Vorbis streams
Easy to Install
Stores ID3 (id3v1 and id3v2) tag information (MP3s, FLAC's, and AAC's)
Stores Vorbis Comments information (Ogg's and FLAC's)
Stores MP4 metadata information (MP4/AAC's)
ID3/Vorbis information can be searched
Easy to import new songs
Buffer support for playback (prevents skipping due to high load or network latency)
Gapless playback (great for live albums)
Crossfading support
Seeking support
Save, Load, and Manage Playlists (in m3u format)
Volume control (OSS, Alsa, and software mixers)
Wide range of audio devices supported (OSS, Alsa, Sun, esd, arts, and more)
Minimal hardware requirements
```

 There's even a lastfm plugin too.

---

### Post by K.Mandla on 2006-09-21
Hey, this links2 -g with gpm is AWESOME. 

But isn't it kind of, sort of, maybe ... cheating on a text-based system?

What other framebuffer apps are there?

---

### Post by fuscia on 2006-09-21
i've done it (for the fork of it) using elinks, pine, nano and mp3blaster. in my view, this is what pc use should be like for inmates.

---

### Post by croak77 on 2006-09-21
> **K.Mandla said:**
> 
What other framebuffer apps are there?

Well, mplayer works. There some image viewers, mythtv works with qt-embedded in directfb, dfbpoint a presentation program and there is/was a GTKfb but I think that project is dead.

---

### Post by era86 on 2006-09-22
Can someone explain more on the framebuffer deal? Is there a howto on how to get all that stuff working?

---

### Post by K.Mandla on 2006-09-23
> **era86 said:**
> Can someone explain more on the framebuffer deal? Is there a howto on how to get all that stuff working?
It's new to me and it doesn't seem very commonplace around here. I installed links2 and got libdirectfb as well. That seems to be what got it going. Beyond that, I'm in uncharted territory. ;)

---

### Post by superatrain on 2007-02-09
I just set up and configured a text-only ubuntu system - my P2 laptop.

to get it to run at a resonable resolution:
add vga=313 to the grub kernel line

Im using nano, links2, lynx (for gmail), mpg321(not alot of multimedia needs) ssh (to get to my files)

I am also having some issues with links2. I had to chmod a+rwx /dev/tty0 for full color to work, but then gpm stopped working. any ideas? otherwise it runs in 16 color mode and it looks awful.

Also, what do you use for a .doc editor, eg: word documents? I have yet to find a nice editor.

And should I even consider doing wifi in terminal? is there any interface other than iwconfig?

----

DirectFB: its a library that can draw graphics on the terminal. there are a couple of ways to do this, such as svgalib, but this method seems to be the most common. 
It may be picky sometimes, but usualy if you have standard hardware and all the necessary packages it should work like a charm.
It can also be used by apps such as mplayer for video playback...

---

### Post by 3rdalbum on 2007-02-09
There's also a kind of window manager for consoles that you can run without an X server. It's in the repos - it's called twin.

Interesting stuff, but I think it's probably useless really :-)

---

### Post by bonzodog on 2007-02-09
I would add screen to this setup. Screen you would find to be an invaluable tool.

---

### Post by xabbott on 2007-02-09
> **K.Mandla said:**
> It's new to me and it doesn't seem very commonplace around here. I installed links2 and got libdirectfb as well. That seems to be what got it going. Beyond that, I'm in uncharted territory. ;)

I think you'll have fun with it if you explore. As others have pointed out there are functioning image viewers, movie players, etc. I believe set top linux boxes do the entire ui in framebuffer. There was/is a distro out there without X that used a framebuffer to render everything too.
Just learn how to use screen and you should be up to do anything. Also for communication I recommend irssi + bitlbee so you have everything in one.

Here is a screen shot of my console.
[[img]http://xs512.xs.to/xs512/07066/fbgrab.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs512&d=07066&f=fbgrab.png)

Now I don't typically split it this much. I just wanted to show you that you could. I have private messages at the top, then irc, rtorrent downloading, midnight commander, then a "task bar" at the bottom with the time and system load. There is also another shell open (but not visible) that you can see in the screen taskbar.

---

### Post by xabbott on 2007-02-09
oops i just noticed that last fbgrab was using the default terminal colors. here is a better one.
[[img]http://xs512.xs.to/xs512/07066/fbarchlinux.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs512&d=07066&f=fbarchlinux.png)

I read how to change the terminal colors [here]("http://phraktured.net/linux-console-colors.html").

---

### Post by tbroderick on 2007-02-09
> **superatrain said:**
> 
Also, what do you use for a .doc editor, eg: word documents? I have yet to find a nice editor.


Did you try antiword?

---

### Post by 3rdalbum on 2007-02-11
> **xabbott said:**
> There was/is a distro out there without X that used a framebuffer to render everything too.

GeeXBox and the Movix distros do that, and it works quite well.

---

### Post by superatrain on 2007-02-11
antiword will have to do, but i was hoping for something that used FB and could edit the files as well...
I hope to try out twin soon... as soon as I get networking back working :S

btw: how do you split the screens, and how do you control which half is active?

---

### Post by Takmadeus on 2007-03-17
you could use midnight commander as a file manager (sorry for the revival... it was an interesting thread)

---

### Post by derjames on 2007-03-18
I've just submit a HowTo which includes info from thise thread and which will apprear soon... (some sort of summary). I been working in Command line mode for a couple of weeks (no X, just simple and plain text) and the experience has been great... the computer is so responsive (ultrafast boot time and instantaneous response) in a Laptop with Core 2 Duo T5600 and 1 GB RAM. Music and Video working fine etc.. etc..

---

### Post by 3rdalbum on 2007-03-19
> **derjames said:**
> I've just submit a HowTo which includes info from thise thread and which will apprear soon... (some sort of summary). I been working in Command line mode for a couple of weeks (no X, just simple and plain text) and the experience has been great... the computer is so responsive (ultrafast boot time and instantaneous response) in a Laptop with Core 2 Duo T5600 and 1 GB RAM. Music and Video working fine etc.. etc..

I'd love to see the Howto; when it's up on the Ubuntu wiki, please reply with the URL.

---

### Post by K.Mandla on 2007-03-19
> **3rdalbum said:**
> I'd love to see the Howto; when it's up on the Ubuntu wiki, please reply with the URL.
[http://www.ubuntuforums.org/showthread.php?t=387598](http://www.ubuntuforums.org/showthread.php?t=387598)

---

### Post by igknighted on 2007-03-20
> **derjames said:**
> I've just submit a HowTo which includes info from thise thread and which will apprear soon... (some sort of summary). I been working in Command line mode for a couple of weeks (no X, just simple and plain text) and the experience has been great... the computer is so responsive (ultrafast boot time and instantaneous response) in a Laptop with Core 2 Duo T5600 and 1 GB RAM. Music and Video working fine etc.. etc..

No offense, because I think that the end result of what you have achieved is well worth it... but on that system?  I would be willing to bet that nearly anything you do on that system (aside from compile) I could do just as quickly on my 1ghz Athlon machine from 6 years ago.  It would seem to me that that if you wanted to just work in CLI mode, why not use older hardware?  I feel like I waste the capabilities of the system listed in my sig... even running beryl/gnome.

---

### Post by andrew.46 on 2007-07-22
Hi,

 I would partly disagree:

> **skymt said:**
> ^^ What he said, plus slrn. ^^

 The best text-based system would _only_ have slrn :-)

         Andrew (slrn fan-boy)

---

### Post by jseiser on 2007-07-23
saw this back up top, and k mandlas blog gave me the info to get a text system, which after a while of playing with was fun.  Couldnt figure screen how really so i went with X + evilwm. then used xbindkeys to bind alt+F# 2-12 to have gmrun, links2, mc, gentoo, vim, leafpad, cplay, rtorrent ( loads onto second desktop and it watches a folder for new/deleted torrents and adjusts automaticly + encryption) gksu+synaptic,htop and k3b (wish i new how to burn mp3 cd's from command line).  My computer is a amd 64 3000 200g HD 1 g ram, and even xubuntu seemed a bit sluggish, this just flies.  I changed default terminal to urxvt, and just bringing up a terminal is as easy as ctrl+alt+enter.  alt tab between full screen windows.  You can use left click to move window, middle click to re-size, right click  to lower window.  ctrl+alt+x maxes window out verticly, cltr-alt+= totally maximises it.  The key bindings, make you open and close programs very fast.  ctrl+alt+ hjkl will resize your windows, so you can be completely mouse free.  I imagine this would be amazing on a laptop, even and old one.  I know this was about a text based system but if you must have some sort of x running, i havent seen anything that compares to the useability of evilwm+xbindkeys.

---

### Post by init1 on 2007-07-24
> **3rdalbum said:**
> There's also a kind of window manager for consoles that you can run without an X server. It's in the repos - it's called twin.

Interesting stuff, but I think it's probably useless really :-)
Yeah. It's useless. Cool, but useless.

---

### Post by fistfullofroses on 2007-07-30
I would say go with Slackware. You get a high console resolution, and for small console programs the installer is amazingly easy.

SC - Spreadsheet
Emacs - Word Processor
w3m - Console browser with image support
naim - Instant Messager
the list continues.

---

### Post by toupeiro on 2007-08-01
90-95% of my administration at work is done without a GUI across several blends and breeds of UNIX and Linux.  Solaris 8, 9, and 10,  IRIX, RHEL3, RHEL4, HP/UX etc etc..  Heck, even some of my very best windows tools were commandline scripts I wrote to make registry changes to over 700 machines at the same time with a little for/do logic. (do not attempt this with a workstation version of a Microsoft OS!)

For UNIX/Linux, the biggest godsend to console administration is a command called screen.   I have screen configured with a .screenrc settings file that lets me very easily open several terminals within a terminal, label them, detach them with whatever program I was running in it still running, and reattach to them whenever I want with simplified hotkeys, and a session reattach script that lets me list my named sessions and attach to them in whichever sequence I want.  That enables multitasking without a GUI.  Then between wget, scp, vim, pico, cpio, iostat, sar, some nice broad environment variables, and some quick aliases to keep the keystrokes down, a powerful shell like tcsh or zsh, and a little bit of scipting knowledge, the only time I ever need a GUI is to troubleshoot a GUI application a user is having a problem with.

If you've never heard of, or used screen before, read its man page in ubuntu or whatever flavor you're running.  Once you start playing with it, you'll really dig it.  You can even set it up so that other people can connect to your 'screen' session in view only mode or interactive mode (if you are trying to show someone how to do something, for example)

---

### Post by fistfullofroses on 2007-08-01
I must say that I am impressed with your wide range of system experience.

---

### Post by toupeiro on 2007-08-01
> **fistfullofroses said:**
> I must say that I am impressed with your wide range of system experience.

hehe thanks man! :-)  I appreciate the compliment.   I am just a hobbiest who turned his hobby into his job about ten years ago.  I had to support some pretty interesting environments in that time.  I learned what I know by either not having an alternative but to figure it out, or by working with some pretty cool people throughout the time, so although I'm no expert, I do like sharing whenever I can.

---

### Post by fistfullofroses on 2007-08-01
I am hoping to attain a job similar when I am done with college. Main problem is a lack of knowledge on what step to take next.

---

### Post by toupeiro on 2007-08-01
> **fistfullofroses said:**
> I am hoping to attain a job similar when I am done with college. Main problem is a lack of knowledge on what step to take next.

not to get too far off topic, but it is a good time for you then.  Something like close to 70% + of the IT workforce will be retiring within the next 5-7 years.  

There are two approaches companies take when they hire techs.  1. Degree required.  This will most likely guarantee you a higher salary but from what I've seen companies will often times fast-track those people into management because of lack of industry experience unless they've  done some workforce internships during college, or some impressive project work.  The vanilla computer science majors that I have met usually have a hard time adapting to a high demand technical job, because without interning, they usually aren't prepared for the diversity of technology most companies utilize, or the fact that some companies IT needs are for  24x7 operations, and you will have to respond at 3:30AM if required to.  Prepare yourself now for things like that and you will do just fine.

Number 2 is experience required.   In this career route, you usually start off getting paid crap and a lot of the grunt work will fall on you in the beginning, but it never lasts that way.  Its much harder to find work if you find yourself in between jobs at a 4-5 year experience range without a degree.  

When I started, I could have made as much money working at in-and-out burger, but when my company got short-staffed during a time they were wanting to upgrade Novell Groupwise to Microsoft Exchange 5.5, I was available, and that was the first step towards the kind of technical lead position I have now.  It's harder to make the leap into management without the degree, but not impossible.  For me, it gives me the best of both worlds right now.  While I am not a manager, as a technical lead role I can make the IT decisions I want, and implement them, and not have to worry about the budgeting and staff problems as much.  I have the trust of the managers, and they will back my play pretty strongly almost every time I've needed them to.

My advice is talk to your college counselor about interning at companies for experience and credits.  If you apply yourself at these internships, those IT managers will remember you when its time to staff up.

If UNIX or linux support is where you would like to end up, then beefing up at your console knowledge, and script knowledge such as perl, will take you far.  Administratively, most of what you will do will be text based.

---

### Post by fistfullofroses on 2007-08-01
WOW. Thank you so much for this response. Mostly what I have heard from every place I have applied is that they want people who've got degrees. So I said "sh-- I need to go to college." Now, I am in college, and I am think that an internship would be a good next move (due to your advice). I have some experience with Unix/Linux support, but nothing on the scale that you are talking about. Most of my experience was helping people with their home businesses. Some of them got large enough that they clanceled the web hosting with whomever, and bought servers. Umm, good for them but they had no clue how to run a server. Enter young Linux kid... It was easy enough for someone who needed a really small database, web page, and whatnot. But that let me know where I wanted to go. I really enjoyed that type of work (even if it was only for my folks wealthy neighbors).
Any good how tos for scripting out there?

---

### Post by Factory on 2008-02-06
> **fistfullofroses said:**
> I would say go with Slackware. You get a high console resolution, and for small console programs the installer is amazingly easy.

SC - Spreadsheet
Emacs - Word Processor
w3m - Console browser with image support
naim - Instant Messager
the list continues.

[http://bsflite.sourceforge.net/](http://bsflite.sourceforge.net/) BSFlite is another option for AIM cli.

---

### Post by lespaul_rentals on 2008-02-06
[QUOTE=superatrain]Also, what do you use for a .doc editor, eg: word documents? I have yet to find a nice editor.[/QUOTE]

Nano! :p

---

### Post by chris4585 on 2008-02-06
this is really interesting, i think i will try screen, and i just learned that you could view images and video in a terminal, i will definitely try this once i can get time, there's tons of apps that can be used

**mc** - *GNU Midnight Commander is a text-mode full-screen file manager. It uses a two panel interface and a subshell for command execution. It includes an internal editor with syntax highlighting and an internal viewer with support for binary files.*
**mutt** - *e-mail*
**weechat** – *chat*
**irssi** – *chat*
**finch** - *pidgin in a terminal pretty much*
**rtorrent** - *the name should be enough*
**links2** - *internet browser*
** [abcde]("http://lly.org/~rcw/abcde/page/")** - *a better cd encoder*
**moc** - *music player*
**scrot** – command line – *nice command line screen shot capturing program*

these are just some programs i know of, does anyone know of a cli distro that has a livecd? or is that possible

---

### Post by lespaul_rentals on 2008-02-06
> **chris4585 said:**
> these are just some programs i know of, does anyone know of a cli distro that has a livecd? or is that possible

FreeNAS.

---

