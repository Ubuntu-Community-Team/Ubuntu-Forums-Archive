---
title: "Video problems with Warsow"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Rodmiester on 2008-06-09
Hi all!
I've just installed Warsow and was eagerly about to start playng but after I launched it the screen went black and got an error message from the monitor itself, not the PC saying "Input Not Supported". My video card is a GeForce FX5500 and the driver is installed.
Any help would be appreciated.
Cheers:)

---

### Post by aeiah on 2008-06-09
sounds like warsow is trying to launch its self in a resolution that your monitor doesnt support. can you set warsow to launch in a window instead of fullscreen, or set the resolution from a config file before launching the game?

what resolution is your monitor normally displaying at?

---

### Post by Hospadar on 2008-06-09
It could also be a refresh rate issue, launching in a window should let you change these settings (if you can) try poking around hidden directories in your home directory, there's probably a seperate one for warsow.  There might also be a command-line option to make it launch in a window.

---

### Post by 16777216 on 2008-06-09
To set Warsow to window mode by config file go to ```
~/.warsow/basewsw
``` and open config.cfg with gedit or any other text editor and find ```
seta vid_fullscreen
``` it should be set to 1 by default.
Set this to 0 and save to make Warsow start in a window.
Once Warsow is started in a window you can set it's options to something your monitor can handle.
I would also sugest you google your monitor model number to find it's specifactions so as to help you set up this game and other future software to beter match your hardware.

---

### Post by Rodmiester on 2008-06-11
Thanx for your help guys. I acutally found the code in acid.cfg. I changed the value to 0 but it didn't work. Oh well, I'll just keep pluggin' away :)

---

### Post by 16777216 on 2008-06-11
```
/home/your-user-name/.warsow/basesw/config.cfg
``` (note the dot in front of warsow) is the file with the active value you are looking for.

```
seta vid_fullscreen 1
```Change that to
```
seta vid_fullscreen 0
```To get it out of fullscreen.

---

### Post by NoTownKasper on 2009-10-17
Sorry for the forum necromancy, but this was the most recent post anywhere I could find with this particular problem...I'm having the same 'input not supported' problem, but in my ~/.warsow/basewsw folder there is no config.cfg file...and yes, I'm showing hidden files as well...anyone know of a command-line switch to kick it up into windowed mode long enough to set things properly?

---

### Post by OpenTangent on 2010-07-06
Answer:

in this folder:
**/home/YourUserName/.warsow-0.5/basewsw/**

Create the file:
**config.cfg**

Add the following to the empty file:
**seta vid_fullscreen 0**

save and run ;)

---

