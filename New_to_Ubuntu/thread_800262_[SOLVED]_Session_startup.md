---
title: "[SOLVED] Session startup"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by NaF on 2008-05-19
I'm trying to make a VLC playlist run at startup. I've put a reference to the file in the session-app. Under the command just added /home/naf/desktop/Movies.m3u - but when I restart the computer nothing happens - not even an error. How do I open the playlist at startup, if this is the wrong way to do it?

---

### Post by NaF on 2008-05-20
anyone? :(

---

### Post by neurostu on 2008-05-20
```

/home/naf/desktop/Movies.m3u

```
This isn't a program its a file.  This would be like trying to run myDocument.doc in windows, when what you really want to do is **OPEN** myDocument.doc with MS Word. What you need to do is identify the command used to open your media player and identify the command line arugments required for it to open a playlist.

to open mplayer in a terminal you can just type
```

mplayer

```
to figure out the command line arguments you can type:
```

mplayer --help


```
which out puts:
```

MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *

```
Did you notice the :-playlist <file> specify playlist file argument
So to open a playlist w/ mplayer the following command will work:
```

mplayer -playlist /home/naf/desktop/Movies.m3u

```
Simply replace what you currently have with that command and it should work.  

Also if you're using a different media player you will have to figure out the commands for that player... what player are you using (if you don't use mplayer)?

---

### Post by NaF on 2008-05-20
> **neurostu said:**
> ```

/home/naf/desktop/Movies.m3u

```
This isn't a program its a file.  This would be like trying to run myDocument.doc in windows, when what you really want to do is **OPEN** myDocument.doc with MS Word. What you need to do is identify the command used to open your media player and identify the command line arugments required for it to open a playlist.

to open mplayer in a terminal you can just type
```

mplayer

```
to figure out the command line arguments you can type:
```

mplayer --help


```
which out puts:
```

MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *

```
Did you notice the :-playlist <file> specify playlist file argument
So to open a playlist w/ mplayer the following command will work:
```

mplayer -playlist /home/naf/desktop/Movies.m3u

```
Simply replace what you currently have with that command and it should work.  

Also if you're using a different media player you will have to figure out the commands for that player... what player are you using (if you don't use mplayer)?

Ahh, see - in Windows you CAN run a file. If you put m3u file in the startup folder, it will simply run that with the default application. I had hoped it was like that on Linux too. I'm trying to launch it with VLC :) Any idea on how to do that?

---

### Post by drs305 on 2008-05-20
Start, Sessions, Preferences,Startup Programs, Add:

The command is simply 'vlc /locationofplaylist/playlist'

---

### Post by NaF on 2008-05-20
> **drs305 said:**
> Start, Sessions, Preferences,Startup Programs, Add:

The command is simply 'vlc /locationofplaylist/playlist.m3u'

If I put ```
VLC /home/naf/Desktop/Movies.m3u
``` in the terminal I get the response:
```
bash: VLC: command not found
```?

---

### Post by drs305 on 2008-05-20
> **NaF said:**
> If I put VLC /home/naf/Desktop/Movies.m3u in the terminal I get the response:
```
bash: VLC: command not found
```?

In ubuntu, everything is case sensitive. It must be typed as 'vlc' ;-)

---

### Post by NaF on 2008-05-20
> **drs305 said:**
> In ubuntu, everything is case sensitive. It must be typed as 'vlc' ;-)

Wow, that's embarrassing :oops: 
Also, it wont load if I put the .m3u on there, so just refer to the name of the file without extension, if someone else finds this at some point ;)

Thanks for the help :)

---

### Post by drs305 on 2008-05-20
Glad it worked. I will go back and modify the command in the previous post to eliminate the .m3u extension.

---

### Post by rraj.be on 2008-05-20
Its better to create a a startup script. For example, the file '/etc/init.d/ntpdate' causes Ubuntu to synchronize it's hardware clock with the ububtu.com timeserver (you might have noticed this during your OS's boot). The file itself is just a script written in the BASH shell scripting language. Creating a new script, saving it in /etc/init.d/ and creating a symlink to one of the runlevel directories (eg /etc/rc2.d/) would be the preferred way to solve your problem.

If you're not comfortable editing system scripts, you could use GNOME's session utility to make Firestarter start when GNOME loads

---

### Post by NaF on 2008-05-20
> **rraj.be said:**
> Its better to create a a startup script. For example, the file '/etc/init.d/ntpdate' causes Ubuntu to synchronize it's hardware clock with the ububtu.com timeserver (you might have noticed this during your OS's boot). The file itself is just a script written in the BASH shell scripting language. Creating a new script, saving it in /etc/init.d/ and creating a symlink to one of the runlevel directories (eg /etc/rc2.d/) would be the preferred way to solve your problem.

If you're not comfortable editing system scripts, you could use GNOME's session utility to make Firestarter start when GNOME loads

wat?!

---

### Post by drs305 on 2008-05-20
> **NaF said:**
> wat?!

NaF,

Don't worry about it. You are in the Absolute Beginner Talk forum. You aren't meant to understand it, but hopefully some day you will ;)

---

