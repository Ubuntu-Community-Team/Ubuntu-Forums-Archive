---
title: "Playing movies in Ubuntu 8.04"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by JC65 on 2008-11-20
Hello everyone, 

I've decided to fully install ubuntu 8.04 on my Dell D430 Latitude (intel core2duo U7600 1.2 ghz, 2 gb RAM, 80 GB HDD, intel graphic card) and it has been running for three months now. Although everything is well, there is a minor problem whenever I play a movie in MPlayer. Can anyone help with the following issue. Thanks for taking your time and effort to solve this issue.  

 Every time I play a movie file, a small blue square appears in the window. It wont go away, even if minimize the window and bring it up again. If I maximize, almost the whole window turns blue, just a bit of the movie is visible in a corner of the window. The peculiar thing is, if I initially open the movie file with Totem it gets an error message ("invalid argument") so I close the app. Then I open the same file Mplayer again and the problem disappears. 

cheers, 
John

---

### Post by shifty_powers on 2008-11-20
have you tried using vlc? it plays everything knwon to man, apart from realplayer files, and they can bugger off :D

```
sudo apt-get install vlc
```

---

### Post by hyper_ch on 2008-11-20
you don't have the codecs.

If you want to play movies, install
```

sudo apt-get install ubuntu-restricted-extra

```

if you want to play DVDs then you have
(1) add the medibuntu repos --> you'll find a howto on their homepage and
(2) install the libraries
```

sudo apt-get install libdvdcss2 w32codecs

```
replace w32 with w64 if you run a 64bit os.

---

### Post by JC65 on 2008-11-20
> **shifty_powers said:**
> have you tried using vlc? it plays everything knwon to man, apart from realplayer files, and they can bugger off :D

```
sudo apt-get install vlc
```

Thanks for the suggestion Shifty_Powers, will look into it.

cheers

---

### Post by shifty_powers on 2008-11-20
don't forget hyper-ch suggestion. the ubuntu restricted extras are usually one of the first packages i install...

---

### Post by JC65 on 2008-11-20
[QUOTE=hyper_ch;6216290]you don't have the codecs.

If you want to play movies, install
```

sudo apt-get install ubuntu-restricted-extra

```

Thanks for the reply Hyper_CH. I've read about getting codecs from Ubuntu restricted sources, however it is stated that codecs are copyrighted and the user should check the legality of installing such codecs in their system. I would prefer to have a computer with only open source and general public license components. Searching on the Ubuntu documentation site, there's a tip on how to convert all media files (avi, mpeg, etc) to .ogg which I take as an open source standard. In your opinion, would it be better to go for such conversion or just install the codecs? Thanks again.

---

### Post by Dedoimedo on 2008-11-20
Hello,

Try starting mplayer from the command line and then see what error, if at all, it throws up. Then post here, if you feel like.

Other good suggestions, as already stated, try installing codecs and using vlc.

Dedoimedo

---

### Post by JC65 on 2008-11-20
Dedoimedo:

Try starting mplayer from the command line and then see what error, if at all, it throws up. Then post here, if you feel like.

Hi Dedoimedo, this might sound down right embarrassing. What is the command line to run an app in the terminal. I'm really a novice to linux. I just typed "mplayer" in the terminal and got info about the app. Thanks.

---

### Post by philinux on 2008-11-20
It's 

gmplayer

---

### Post by Dedoimedo on 2008-11-20
Hello,

To learn more about application, here's a few tips:

man <name> gives you a full manual page with details.

info <name> gives you similar to above

<name> --help you get a brief usage overview and some extra details.

which <name> tells you where the executable is located.

<name> click tab twice, you'll get a list of all executables that contain <name> in their ... name.

Next, don't forget google, like: "mplayer run file command line" or "mplayer command line options"

In this case, what you want to do is:

mplayer filename

Ex: mplayer music.mp3 or mplayer movie.avi

Dedoimedo

---

### Post by JC65 on 2008-12-01
hi Dedoimedo, 
Sorry for the late reply, been out of town and incommunicado. here is what came up on the terminal window.

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Is there anything wrong in that output? Thanks.

---

