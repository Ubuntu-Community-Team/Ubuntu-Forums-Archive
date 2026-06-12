---
title: "media player"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-02
OK. i havent found one so far, that can do the following:

-Run .ogg, .mp3, .wma, and .m4a files
-work with my logitech elite keyboard's media buttons (next/prev track, play/pause, and stop buttons)
-is organized

exaile, rythmbox, and helix (and others...) all only cannot plat m4as

flv player and audacity/audacious(forgot which it is) only play all the files

songbird cannot play wma and does not work with my buttons... otherwise it is perfect! well, close enough.

---

### Post by Tatty on 2008-05-02
VLC - simply the best media player around.  If you are using hardy you might have to change the output from pulseaudio to alsa due to some bugs with choppy sound, but aside from that it should do what you want out of the box

In terms of getting other players to work, Have you installed all of the codecs with this guide?: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sloggerkhan on 2008-05-02
might try: [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)
It's not a library style application, but personaly, I think as just a player it's beyond what VLC offers. So far I have not met a video format it does not play. Good GUI to lots of mplayer options, too.

---

### Post by ad_267 on 2008-05-02
This might help for .mp4 [https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)

---

### Post by Zopiac on 2008-05-02
> **Tatty said:**
> VLC - simply the best media player around.  If you are using hardy you might have to change the output from pulseaudio to alsa due to some bugs with choppy sound, but aside from that it should do what you want out of the box

In terms of getting other players to work, Have you installed all of the codecs with this guide?: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

vlc is what i meant instead of flv player. hate it :P

---

### Post by Zopiac on 2008-05-02
> **sloggerkhan said:**
> might try: [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)
It's not a library style application, but personaly, I think as just a player it's beyond what VLC offers. So far I have not met a video format it does not play. Good GUI to lots of mplayer options, too.

this program does not work with my buttons, has a horrible interface for music, is hard to get music from folders, and completely hogs my resources

---

### Post by sloggerkhan on 2008-05-03
*shrugs*
Obviously it has a horrible interface for music... it's MEDIA player not a MUSIC player. So far as buttons go, I can't speak to that, but I'd sorta expect that need to be configured. So far as hogging resources, on my computer it only uses like 10mb of memory, I guess if it's playing back something it will use more for buffers or whatnot. If you want a music library application, you aren't asking the same thing as a media player.

There's banshee, rhythmbox, amarok, exaile, and many others.

---

### Post by fenian on 2008-05-03
> exaile, rythmbox, and helix (and others...) all only cannot plat m4as

I can play m4as on both rhythmbox and exile.You probably need to install the correct codecs.
First add the medibuntu repos,open a terminal and enter...
> 
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then enter...
> 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

then enter...
> 
sudo apt-get install ubuntu-restricted-extras gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

You should then be able to play m4as in Rhythmbox and Exaile i've never used Helix so I don't know about that one.

---

### Post by Zopiac on 2008-05-03
> **fenian said:**
> I can play m4as on both rhythmbox and exile.You probably need to install the correct codecs.
First add the medibuntu repos,open a terminal and enter...


then enter...


then enter...


You should then be able to play m4as in Rhythmbox and Exaile i've never used Helix so I don't know about that one.

zopiac@zopiac:~$ sudo apt-get install ubuntu-restricted-extras gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll

---

### Post by Paqman on 2008-05-03
What about Miro? I uses VLC under the skin, so it should play anything. I found it a bit bloated, but if you want one ap that does *everything*, Miro is your baby. Heck, it'll even download torrents for you.

---

