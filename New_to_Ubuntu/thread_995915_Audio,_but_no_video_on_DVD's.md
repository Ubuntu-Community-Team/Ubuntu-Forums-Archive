---
title: "Audio, but no video on DVD's"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by cisner on 2008-11-28
I just got Ubuntu loaded this week and one thing I am having trouble with is that DVD's only play audio and no video at all.  I downloaded and hopefully installed the codecs, but still no luck.

Any hints?

---

### Post by taurus on 2008-11-28
Which media player have you tried?  Try vlc if you haven't done so.

```
sudo apt-get update
sudo apt-get install vlc
```
It's in Applications -> Sound & Video now.

---

### Post by cisner on 2008-11-28
I did install vlc and still no luck.

---

### Post by taurus on 2008-11-28
Do you happen to have compiz running?

---

### Post by cisner on 2008-11-28
I have no idea what compiz is or even if I have it, and if I did where to find it.

---

### Post by cisner on 2008-11-28
Okay, I Googled it and don't have that one installed.  BTW, regular video like U-tube etc plays just fine, so I'm assuming it's a codec issue still?

---

### Post by taurus on 2008-11-28
Perhaps you need libdvdcss2.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by cisner on 2008-11-28
let me see if I can figure out how to do that...

---

### Post by cisner on 2008-11-28
I'm pretty new at this so I may need some step by step instructions for a complete newb.

---

### Post by stoogiebuncho on 2008-11-28
Which version of Ubuntu do you have?

---

### Post by cisner on 2008-11-28
8.1

---

### Post by taurus on 2008-11-28
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by cisner on 2008-11-28
So do I just type that into console?  Told you I was new...

---

### Post by thadacto on 2008-11-28
I, too am having problems getting videos to run. 
The only one that seems to work for me is KMPlayer.
Totem, which I think seems to be part of the Ubuntu package won't play AVI nor mpg files. KMPlayer does, so for me, its not a problem of Codex but a problem of confiuguartion of the Totem program.

---

### Post by taurus on 2008-11-28
Why type?  Open a terminal and do the cut 'n paste.

Highlight the first line with the left button of your mouse and paste it to the terminal with the middle scroll track.  Then, hit return.  Now, do the same with the second line and then the third.

---

### Post by theozzlives on 2008-11-28
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

```
/usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by stoogiebuncho on 2008-11-28
Yeah, when people post code like that, it means you are supposed to enter it into the terminal.  I believe you can find the terminal under Applications > Accessories > Terminal, but I'm running Xubuntu right now, so I can't check for sure.

There are ways to do these thing through the graphic user interface as well, but generally on these forums it's easier to tell someone how to do it with a line of code than to write a long description telling them where to go and what to click.

As was said before, you can copy a line of code, open a terminal, right-click and choose "Paste" to save yourself some typing.

---

### Post by cisner on 2008-11-28
Okay I did those commands in terminal and no change in vlc.  Do I need to do a restart or some such thing like in windoze?   Do I need to enable the codecs in the program itself now?

---

### Post by cisner on 2008-11-28
I see that the control C and P don't work in this environment.

---

### Post by cisner on 2008-11-28
I got video playback!  I changed the vlc video output to open gl and it is now working! Audio and video.  Now how do I make it the default player and should I dump the other one?

---

