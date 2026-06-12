---
title: "Using VLC, Movie Player, or basic video player, how can i play until X time?"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by hanzj on 2012-07-16
Hello,

Using one of the media players installed on my linux computer (I have VLC, Movie Player, Banshee media player, Gnome MPlayer), how can I play a media file but make playback stop at X time?
For instance, there is a 1minute:58 second movie (We have wmv and mov versions of the same movie) and we want playback to automatically stop at 1 minute, 44 seconds. 

I prefer to use VLC, because we plan on playing the clips on a Windows computer. I prefer to use a free program that is available for both Windows and Linux.

Thank you so much!

---

### Post by glennric on 2012-07-17
Using vlc:
```
vlc --stop-time N filename
```
where N is in seconds.

With mplayer:
```
mplayer -endpos hh:mm:ss filename
```
where hh:mm:ss is the number of hours, minutes, and seconds that you want to file to play for.

---

### Post by hanzj on 2012-07-17
glennric,

I ran the following VLC command
>  vlc --stop-time 104 '/home/[myusername]/Downloads/life.mov' 

The mov file is 1 minute and 58 seconds long. I wanted VLC to stop playback at 1 minute and 44 seconds (I had 104 in the terminal command because 1 minute plus 44 seconds equals 104 seconds). But VLC played the mov file until the very end (1:58).

What am I doing wrong?

---

### Post by hanzj on 2012-07-17
> **glennric said:**
> Using vlc:
```
vlc --stop-time N filename
```
where N is in seconds.


Glennric,
I think your command is correct for Windows 
(According to [http://www.videolan.org/doc/play-howto/en/ch04.html:](http://www.videolan.org/doc/play-howto/en/ch04.html:) 
> 
Windows users have to use the --option-name="value" syntax instead of the --option-name value syntax.

In Linux, we must add the hyphen:
```
vlc --stop-time**[SIZE="4"]-[/SIZE]**N filename
```

---

### Post by glennric on 2012-07-17
> **hanzj said:**
> Glennric,
I think your command is correct for Windows 


I don't run windows.  Only Ubuntu Linux.  I tested the command exactly as I gave it and it works.  You can put an equality between the command line flag and its parameter and it will also work.  According to the website you linked I am correct.  On windows you have to put the equality between, but on linux it works both ways.
> Windows users have to use the --option-name="value" syntax instead of the --option-name value syntax.

By the way, putting a hyphen in does not work at all.

---

