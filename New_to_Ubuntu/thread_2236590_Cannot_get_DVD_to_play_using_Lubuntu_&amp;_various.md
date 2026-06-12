---
title: "Cannot get DVD to play using Lubuntu &amp; various players"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-07-27
[COLOR=#ff0000][/COLOR]I can't open and play a DVD with VLC media player. I get the messages:


[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/dvd".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.[/COLOR]

With Movieplayer I get:

An error occurred, the movie could not be read.

I can't get it to play with GNOME MPlayer either.

Anybody have any thoughts?

It is an HBO documentary DVD I got from the library. It is copyright protected. I am in the U.S.

Thanks,

R.

---

### Post by kira-yamato-2008 on 2014-07-27
I'm pretty sure that Open Source software such as Lubuntu and VLC come without means of decoding commercial DVDs.

---

### Post by Dennis N on 2014-07-27
You can get directions here on what can be done:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Even so, results can vary as to what features will work correctly.  For best results, use a regular stand alone DVD player if possible.

---

### Post by AbleTassie on 2014-07-27
I actually had similar problems with a library DVD several months ago. I think I was still using Ubuntu 12.04 LTS back then. I looked at the reviews on the repository and downloaded several video players. And eventually I found one that worked. But I can't remember the name of the one I used. I do not think the one that worked then is one I have now (VLC media player, GNOME MPlayer, or MoviePlayer).

QUESTION: Any suggestions? 

libdvdread4 was already installed in VLC and I tried disabling DVD menus and that did not work either. There may be a few other things I can try, like regionset and run these two terminal commands: (1) chmod 660 /dev/sr0  (2) chgrp cdrom /dev/sr0

Any suggestions?

Thanks,

R.

---

### Post by yancek on 2014-07-27
Do you have libdvdread4 installed as well as libdvdcss?

---

### Post by Vladlenin5000 on 2014-07-27
> **yancek said:**
> Do you have libdvdread4 installed as well as libdvdcss?

Good question indeed.

@[[COLOR=#000000][/COLOR][COLOR=#000000]RMcGinnis[/COLOR]]("http://ubuntuforums.org/member.php?u=1901514") 	 - Have you actually read the link in post #2? You reply kinda ignored it...

---

### Post by dave131 on 2014-07-27
Just to explain the above:  libdvdread4 is only a small piece of the puzzle.  libdvdcss actually handles the copy protection (decryption).  Just installing libdvdread4 does not install libdvdcss.  There is a script to install libdvdcss - /usr/share/doc/libdvdread4/install-css.sh.

All of this is in the link a previous poster pointed you to earlier.  If you haven't already, you should follow that link and be sure to read it and follow it.

---

### Post by AbleTassie on 2014-07-28
I did execute the terminal command 
sudo /usr/share/doc/libdvdread4/install-css.sh 

and then rebooted. I can now open the DVD in some ways: I can get VLC Media player to play the theme 
song of the documentary with a picture. But I cannot get VLC Media player to advance to play the chapters
in the documentary. It just keeps playing the first 1:30 minutes or so of theme song with a picture over & over. 
I actually watched the documentary over at the library. I was able to get the library's VLC media player
to do the same thing as the VLC mediaplayer I have at home. But I could not watch the documentary over at the
library either with VLC media player. SO I had to use a different library DVD software program to watch the
documentary.

The menu and advance & return controls on VLC media player don't seem to work to advance or return to the next 
chapter or let me use the menu to play the next chapter. They just cause the first 1:30 minutes of music with 
the picture to repeat.

Any thoughts?

Thanks,

R.

---

### Post by Rob Sayer on 2014-07-28
It's very difficult to find computer programs that support all DVD features like menus.  I only ever heard of one Windows program that had menu support.  I don't remember what it was because I rarely use windows anymore and the said program was terrible otherwise so I yanked it.

Otherwise, as mentioned, you probably just need to install the needed libraries.

---

### Post by dave131 on 2014-07-28
So, what's the different program you had to use at the library?  Perhaps we can better help you if we know what it is.

Anything?  I ask this for a very important reason:  the DVD may be in a different format specifically for some reader program, not for playing as a normal DVD.  VLC supports normal DVD menus and jumping to those entries just fine.  I suspect it's a format issue and a special reader application is needed.

> **Rob Sayer said:**
> It's very difficult to find computer programs that support all DVD features like menus.  I only ever heard of one Windoze program that had menu support.  I don't remember what it was because I rarely use windows anymore and the said program was terrible otherwise so I yanked it.

Otherwise, as mentioned, you probably just need to install the needed libraries.

Back when I used to run Windows, I had several DVD player programs that ran DVDs with menus fine.  If I can ever remember their names I'll post them back here for you

---

### Post by oldos2er on 2014-07-29
> **RMcGinnis said:**
> I can't open and play a DVD with VLC media player. I get the messages:


[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/dvd".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.[/COLOR]

With Movieplayer I get:

An error occurred, the movie could not be read.

I can't get it to play with GNOME MPlayer either.

In vlc I usually need to open /dev/sr0 to play a DVD.

---

### Post by dave131 on 2014-07-30
I never noticed that before!  Guess that's why I'm a newbie.

---

### Post by AbleTassie on 2014-08-01
Dennis, Vlad, yancek, Dave, Rob, Ann, and others,

The programs that worked are: Cyberlink Power DVD9 (Windows 7 or 8), and in Windows XP: Intervideo WinDVD (Toshiba), and Windows Media Player.

If I put the DVD into the DVD reader, and let the PC automatically open VLC player, then I can get VLC player to play the theme song with a menu screen. But until tonight, that was as far as I could get, I could not actually play the DVD. But now I have figured out how to actually watch the DVD using VLC media player in Lubuntu.

If I open VLC from the menu button in Lubuntu by going to Sound & Video, I must use the drop down menu in VLC to go to dev/sro as Ann said to get to the DVD title page to open. Then I can play the DVD.

Thanks everybody, I will mark this thread as solved.

R.

---

