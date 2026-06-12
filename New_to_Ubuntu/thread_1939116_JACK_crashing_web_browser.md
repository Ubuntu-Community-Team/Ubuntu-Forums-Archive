---
title: "JACK crashing web browser"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by acimi66 on 2012-03-11
Has anyone run across JACK crashing their web browser, when it's streaming?
I thought it might be the IDJC software but some testing has shown it's the JACK audio connection kit.
I am running 11.10 and I have tried removing it and re loading it.

Would love to know what you know about this.

---

### Post by cryptotheslow on 2012-03-12
Which browser?

You could try starting your browser from a Terminal window and seeing if it gives any sensible error information there when it crashes.

---

### Post by acimi66 on 2012-03-12
I am using Firefox, but I had the same results with chromium, and three other repos web browsers.

I did the terminal start up and it didn't pick any problems...

---

### Post by acimi66 on 2012-03-13
Actually when I started firefox W/terminal I got this:
(firefox:2547): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

When I started JACK I got this...and the browser still crashes

(plugin-container:2633): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:2654): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Any thoughts?

---

### Post by cryptotheslow on 2012-03-13
I quite often see similar theme engine "pixmap" messages - but when applying updates on a 12.04 install, not when starting firefox. Odd it should happen with every browser as well.

Firefox can be started in debug mode with:
```
firefox --debug
```

You need a debugger like gdb installed (might be installed by default).

I've not delved into it at all other than to work out that from the (gdb) prompt you need to enter *run* at which point firefox pops up. The help command in gdb gives a myriad of command options. I'd have thought it should be possible to work out why it is exiting from debug mode - but I have no clue how to go about it :(

---

### Post by acimi66 on 2012-03-13
The page in question is :
[http://www.endeavoracademy.com/online-classes](http://www.endeavoracademy.com/online-classes)

when I hit reload player with JACK running it freezes up.
debug shows this
(gdb) run
Starting program: /usr/lib/firefox-10.0.2/firefox 
[Thread debugging using libthread_db enabled]
[Inferior 1 (process 2172) exited normally]

I went to the site and tried to search the bug number..no luck.

Thanks for the debug idea.

At what point do I just get rid of JACK?

---

### Post by cryptotheslow on 2012-03-14
That:
[Inferior 1 (process 2172) exited normally]

message appears in gdb as soon as the firefox instance starts and doesn't seem to relate to the firefox process itself.

You can't get rid of JACK if you want to run IDJC. How are you starting JACK? Using the JACK patchbay graphical tool? There is no need to have JACK running at all unless you are actually running IDJC at the time.

And when you say this:
*when I hit reload player with JACK running it freezes up.*

What freezes up - firefox or JACK?


The player on that particular page is a Flash based player (JW Player) so will be run in a /usr/lib/firefox/plugin-container process. There may be something JACK doesn't like about the way it accesses sound functions, or maybe something that conflicts with IDJC use of JACK.

And finally - are you running 32 or 64bit Ubuntu 11.10?

---

### Post by acimi66 on 2012-03-14
Hey Crypto,
Thanks for the response.
Firefox freezes up JACK never freezes.
The guys at JACK web DEV suggested I try this:
[http://jackaudio.org/routing_flash](http://jackaudio.org/routing_flash)

but when I tried I only got this message from terminal.,

"me@here:~$ git clone git://repo.or.cz/libflashsupport-jack.git 
fatal: destination path 'libflashsupport-jack' already exists and is not  an empty directory. 
me@here:~$ cd libflashsupport 
bash: cd: libflashsupport: No such file or directory 
me@here:~$ make 
make: *** No targets specified and no makefile found.  Stop. 

I am thinking of doing a re-install and starting fresh. What do think?

---

### Post by cryptotheslow on 2012-03-14
It really depends what you are trying to achieve. What the JACK devs are suggesting is routing flash audio through the JACK sound server (rather than PulseAudio as used by default in Ubuntu). Shouldn't really be necessary as they are just different means to get sound out to ALSA which takes care of handling the actual sound hardware output.

Unless - Do you want to stream the output of that player using IDJC?

Also do any other flash based players cause the same problem? e.g. do the JW Player demos on this page: [http://www.longtailvideo.com/open-video-ads/demos/](http://www.longtailvideo.com/open-video-ads/demos/)  cause the same problem in all browsers? And which Flash plugins are you using in each?

This is useful information to help understand the sometimes confusing nature of Linux sound architecture:
[http://www.tuxradar.com/content/how-it-works-linux-audio-explained](http://www.tuxradar.com/content/how-it-works-linux-audio-explained)

I know on older versions of Ubuntu on a PC I used mainly for internet radio broadcasting I ended up stripping out PulseAudio altogether and having the desktop applications just use ALSA directly. I can't remember what the problems were back then but getting rid of PulseAudio solved my headaches with JACK at the time. I've not found it necessary since using Ubuntu v10.04 though. Oh - and I also ended up having to use the realtime kernel and forcing the use of the hpet timer to overcome a weird sound chip oddity that reported its sampling rate as 40999Hz in JACK thanks to a weird rounding error - also long since past thanks to that particular PC killing itself in a dramatic cloud of smoke.

---

### Post by acimi66 on 2012-03-14
[QUOTE=cryptotheslow;11766209]
Unless - Do you want to stream the output of that player using IDJC?

No, I just want to check the sound that is coming FROM that flash player.

I'll check those links, do some reading and get back to you. Thanks!

p.s.I just did a quick check with first link to the video site and YES it was playing audio and video fine. I started JACK and it crashed.

---

### Post by grandmoss on 2012-03-18
Hi 

I was having the same horrendous jack problems that it seems you are having.  Sadly, the solution that worked for me was the libflashsupport fix that wasn't working for you.

I didn't have any issues getting the git sources though.  Maybe create an empty directory (ie ~/git) and try again from there. So:

```

cd 
mkdir git 
cd git 
git clone git://repo.or.cz/libflashsupport-jack.git

```to start.

Actually, do you have git-core installed?  Maybe that's part of the problem?

There are several dependencies you will probably have to install, and they are listed on [http://jackaudio.org/routing_flash](http://jackaudio.org/routing_flash)
plus one of the headers libflashsupport-jack needs is out of date, so I created a symbolic link to the replacement
I had to:

```
sudo apt-get install automake libsamplerate0-dev libv4l-dev
cd /usr/include/linux/
sudo ln -s /usr/include/libv4l1-videodev.h videodev.h
cd ~/git/libflashsupport-jack/
./bootstrap.sh
make
sudo make install
```

I restarted Firefox and jack, and sure enough, there's a "flash" output in my qjackctl connection window.

Hope this helps

---

