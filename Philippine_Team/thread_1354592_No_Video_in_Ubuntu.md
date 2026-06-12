---
title: "No Video in Ubuntu"
date: 2009-12-14
forum: Philippine Team
---

### Post by stormsurge on 2009-12-14
Hey guys! I'm a new Ubuntu 9.10 user and I have a video problem in Ubuntu. I just noticed that I can't play my videos with any media players.  I tried Totem, VLC and Kaffein... All of these can't play my videos.
 
Its just weird because for the last 2 weeks of my fresh installation, I did not have any problems with my video then suddenly I encountered this. 

To give you a brief background on what particularly is my problem, everytime I double-click (or open) a video file, my video player opens then it immediately closes. 

Thank you!

---

### Post by loell on 2009-12-14
what happens when you just click the video player? be it VLC or Totem?  does it also quit unexpectedly?

---

### Post by stormsurge on 2009-12-14
I do not encounter any problems when I just click the program (VLC, Totem). But when I open the video file itself, it quits unexpectedly. Thanks!

---

### Post by loell on 2009-12-14
I'm suspecting that this caused by an update on video driver, would you know what video card and driver you're using?

---

### Post by stormsurge on 2009-12-14
Hi Loell! I tried to open a .avi video from a CD. Here are the results:

1. Totem - Quits unexpectedly
2. VLC - Played audio only

I did not update my drivers at all. Anyway, I can't determine my video card and my driver. All I know is I'm using Intel Graphics accelerator. LOL. Do you know any command to use in Terminal so I could determine my drivers? Thanks!

---

### Post by Alex Libman on 2009-12-14
You might be missing some needed codecs [(see this thread)]("http://ubuntuforums.org/showthread.php?p=8421040").

---

### Post by stormsurge on 2009-12-14
Rhythmbox can play my video!!!!! Hahaha! That's weird.... What could be the problem?!

---

### Post by loell on 2009-12-14
can you play this video in totem?

[http://commons.wikimedia.org/wiki/File:Indy_500.ogv](http://commons.wikimedia.org/wiki/File:Indy_500.ogv)


maybe you just needed w32codecs since you can  play it in rhythmbox.

---

### Post by stormsurge on 2009-12-14
Hi Loell!

Just for the record, I opened the video with Mozilla first and it plays. Then I opened it with Totem through Open Location under Movie. Still, Totem quits unexpectedly. How can I install w32codecs? Thank you very much!

---

### Post by loell on 2009-12-14
ah i see, that's rather strange, could you launch the terminal,
then launch totem from their?  play the video ( still using "open location") and when it crashes, post the output here.

---

### Post by stormsurge on 2009-12-15
Hi Loelle! Sorry but I'm not that familiar with the code which I may use to open my Totem via Terminal. Any idea? Thanks!

---

### Post by loell on 2009-12-15
oh sorry, in the terminal just type **totem**. :)

---

### Post by badrra on 2009-12-15
How about uninstalling then reinstalling VLC. Just go to synaptics, search for VLC, uninstall. Then re-install.

---

### Post by badrra on 2009-12-15
And you know what, why dont you just install Elisa. Its a media center that lets you play videos, music, run internet radio and more. 

my 2 cent

---

### Post by stormsurge on 2009-12-15
> **loell said:**
> ah i see, that's rather strange, could you launch the terminal,
then launch totem from their?  play the video ( still using "open location") and when it crashes, post the output here.

Hi Loell! Please see the output from Totem:

(totem:2095): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkliststore.c:797: Invalid column number 6 added to iter (remember to end your list of columns with a -1)
Segmentation fault

---

### Post by stormsurge on 2009-12-15
> **badrra said:**
> And you know what, why dont you just install Elisa. Its a media center that lets you play videos, music, run internet radio and more. 

my 2 cent

I'll also try your options this weekend. I really hope that I could resolve my problem. Thanks!

---

### Post by stormsurge on 2009-12-15
Here is also Terminal's output for VLC.

At first, I opened an MP3 file. After that, I opened a video. Just like Totem, I encountered the same experience.... 

VLC media player 1.0.2 Goldeneye
[0x81441f0] main interface error: no interface module matched "globalhotkeys,none"
[0x81441f0] main interface error: no suitable interface module
[0x80aa140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x80aa140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Can't stat media
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x8390010] access_file access error: cannot open file media (No such file or directory)
[0xb7300a70] main input error: open of `media' failed: no suitable access module
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Can't stat player
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x8390000] access_file access error: cannot open file player (No such file or directory)
[0xb7300a70] main input error: open of `player' failed: no suitable access module
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
[0x8512428] pulse audio output: No. of Audio Channels: 2
[0x8512428] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102

---

### Post by loell on 2009-12-15
this is in 9.10 karmic koala, right?

it seems there is a problem with the recent update,
the second to the last post maybe useful for you,    [https://answers.launchpad.net/ubuntu/+question/91356](https://answers.launchpad.net/ubuntu/+question/91356)

if you have questions or clarification with the workaround just ask away.. :)

---

### Post by stormsurge on 2009-12-19
> **badrra said:**
> And you know what, why dont you just install Elisa. Its a media center that lets you play videos, music, run internet radio and more. 

my 2 cent

I just finished downloading this man. This player rocks! Now I could play my videos again. Thanks!

---

### Post by stormsurge on 2009-12-19
Thanks for the help Loell! I just installed Elisa and it can play my videos again.

---

### Post by elite_angel on 2009-12-21
Cool experience! Keep it up!

Better if you only have 2 movie players. VLC and Totem can play all video formats. Sometimes, player codecs are just in conflicts.

---

