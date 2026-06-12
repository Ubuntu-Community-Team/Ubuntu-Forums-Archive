---
title: "MPlayer vs VLC"
date: 2011-05-12
forum: Recurring Discussions
---

### Post by Oxwivi on 2011-05-12
**GUI aside** why would you prefer one over the other? Both of them are one-size-fits-all player.

I myself prefer MPlayer because I've experienced no tearing and lagging as opposed to VLC. And subtitle support sucks on VLC too.

This part is just biased opinion, but I see MPlayer as the lean, mean machine.

---

### Post by Lucradia on 2011-05-12
Neither. Totem / Parole is enough for me.

---

### Post by TeoBigusGeekus on 2011-05-12
You should try smplayer, which is a front end for mplayer with one awesome easter egg: resume video from the last time you stopped it.

---

### Post by el_koraco on 2011-05-12
Totem for life

---

### Post by Oxwivi on 2011-05-12
> **TeoBigusGeekus said:**
> You should try smplayer, which is a front end for mplayer with one awesome easter egg: resume video from the last time you stopped it.
**GUI aside** - I did not embolden it for no reason.

And yeah, Totem fails me in subtitles as well, otherwise I wouldn't have messed with MPlayer.

But please keep on topic, it's about **VLC** and **MPlayer**,

---

### Post by Fedz on 2011-05-12
MPlayer is ok but, it's a bit 'default'. VLC I only use for video media but, for audio I always use Exaile as this player totally surprised me how lean, quick & featured it was & is. I installed it by accident. Best thing I did (apart from installing Ubuntu) :)

---

### Post by Oxwivi on 2011-05-12
> **Fedz said:**
> MPlayer is ok but, it's a bit 'default'.
Default? Ever seen it's configuration files? You'd be blown away!

---

### Post by Fedz on 2011-05-12
> **Oxwivi said:**
> Default? Ever seen it's configuration files? You'd be blown away!
Maybe I need to look more closely! Last time I used MPlayer was about 2 versions ago & I wasn't taken by it personally but, sure I'll install it now & have a play :)

---

### Post by Lucradia on 2011-05-12
> **Oxwivi said:**
> And yeah, Totem fails me in subtitles as well, otherwise I wouldn't have messed with MPlayer.

if you just use stock codecs from Totem when it asks you to get codecs, then that's the reason. You need more stuff for subtitles to really work, and most of that is only provided by medibuntu: [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

Install libdvdcss2, non-free-codecs and the appropriate wXXcodecs, where XX is 64 or 32 (You can't download 32 on amd64 however, it'll spit an error.)

---

### Post by Oxwivi on 2011-05-12
> **Lucradia said:**
> if you just use stock codecs from Totem when it asks you to get codecs, then that's the reason. You need more stuff for subtitles to really work, and most of that is only provided by medibuntu: [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

Install libdvdcss2, non-free-codecs and the appropriate wXXcodecs, where XX is 64 or 32 (You can't download 32 on amd64 however, it'll spit an error.)
I installed all the codecs it asked for, and looking at the name of the package you're suggesting, it's to do with DVD subtitles. But the ones I'm having trouble with are ***/SSA.

---

### Post by Ric_NYC on 2011-05-12
Vlc .

---

### Post by Lucradia on 2011-05-12
> **Oxwivi said:**
> I installed all the codecs it asked for, and looking at the name of the package you're suggesting, it's to do with DVD subtitles. But the ones I'm having trouble with are ***/SSA.

Then you aren't watching a DVD? Shame on you.

---

### Post by Oxwivi on 2011-05-12
Yeah, I'm watching ***, LMAO!

---

### Post by nothingspecial on 2011-05-12
You can't watch youtube vids without X with vlc.

---

### Post by Lucradia on 2011-05-12
> **nothingspecial said:**
> You can't watch youtube vids without X with vlc.

Nope.avi: [http://www.clickonf5.org/linux/watch-youtube-videos-ubuntu-lucid-media-player/7557](http://www.clickonf5.org/linux/watch-youtube-videos-ubuntu-lucid-media-player/7557)

There was also a firefox addon called "System Player", which doesn't exist anymore, which would integrate with your media player, be it WMP, or Totem.

---

### Post by nothingspecial on 2011-05-12
I see plenty of X there.

---

### Post by philinux on 2011-05-12
Moved to Recurring Discussions.

---

### Post by Lucradia on 2011-05-12
> **nothingspecial said:**
> I see plenty of X there.

You said X with VLC, that's just X :V

---

### Post by nothingspecial on 2011-05-12
I said without X :P

---

### Post by nothingspecial on 2011-05-12
I take that all back -- you can with cvlc and it seems to fullscreen by default fr the vids I've tried so that's better than mplayer.

I change my vote.

---

### Post by nothingspecial on 2011-05-12
But I'll change my vote back to mplayer because cvlc in the console doesn't have any keybindings.

Which means I can't pause, rewind etc

---

### Post by jerenept on 2011-05-12
XBMC or Totem works fine for me.

---

### Post by andrew.46 on 2011-05-13
> **nothingspecial said:**
> But I'll change my vote back to mplayer because cvlc in the console doesn't have any keybindings.

Which means I can't pause, rewind etc

Perhaps you should have a look at the ncurses interface of vlc known as [nvlc]("http://wiki.videolan.org/Documentation:Modules/ncurses") which allows for the key commands that you mention. I am not sure if the Ubuntu repository version has built this, and I confess it can be a little twitchy, but I think there is a guide somewhere on these Forums which enables the ncurses interface while compiling vlc :).

---

### Post by SeijiSensei on 2011-05-13
> **Oxwivi said:**
> I installed all the codecs it asked for, and looking at the name of the package you're suggesting, it's to do with DVD subtitles. But the ones I'm having trouble with are ***/SSA.

Those subtitles require libass for correct rendering.  mplayer has a decent, but somewhat out-of-date version of libass.  However I recommend  the fork known as [mplayer2]("http://www.mplayer2.org/").  I built this from source recently and set it as my default mplayer version in smplayer.  There's no Ubuntu .deb available, but there is a Debian version [here](http://pkgs.org/debian-sid/multimedia-main-i386/mplayer2_2.0~git20110422-0.1_i386.deb.html).  Can't say if it works in Ubuntu, though.

mplayer2's multi-threading support helps quite a bit on multi-core machines.  If I watch an H.264-encoded video with the xv driver, I can see all the cores decoding the stream when I run "top" in a separate window.

---

### Post by Random_Dude on 2011-05-13
I use clementine for music, but VLC for video.

VLC just gets the job done: reads all the formats I need and supports multiple subtitle and audio tracks.

Cheers :cool:

---

### Post by Bandit on 2011-05-13
I have used both for years. But I find myself using VLC slightly more these days only because I like VLCs interface. But other then that, if MPlayer is /configured with as many options as possible; it can be very versatile.

---

### Post by nothingspecial on 2011-05-13
> **andrew.46 said:**
> Perhaps you should have a look at the ncurses interface of vlc known as [nvlc]("http://wiki.videolan.org/Documentation:Modules/ncurses") which allows for the key commands that you mention. I am not sure if the Ubuntu repository version has built this, and I confess it can be a little twitchy, but I think there is a guide somewhere on these Forums which enables the ncurses interface while compiling vlc :).

Thanks for your advice Andrew :)

Unfortunately, nvlc does not offer key bindings in the console as far as I can tell. By console I mean no Xserver running where as mplayer does.

Having had a little play, I also notice that the sound from {c,n}vlc is decidedly iffy. So I will stick with mplayer.

Do  you happen to know a method of getting mplayer to play fullscreen (properly) in the framebuffer without advanced mathematics.

A simple -fs will fill the screen but with the video in the centre, not necessarily fullscreen as we know it.

From what I have read, you have to figure out the exact aspect ratio of the movie and do some really complicated sum to tie that to the resolution of your framebuffer.

I would prefer to type mplayer -fs video.avi without the maths.

---

### Post by andrew.46 on 2011-05-14
> **nothingspecial said:**
> Unfortunately, nvlc does not offer key bindings in the console as far as I can tell. By console I mean no Xserver running where as mplayer does.

Oops, I see what you mean, nvlc crashes and burns on my system in a console :(.

> Do  you happen to know a method of getting mplayer to play fullscreen (properly) in the framebuffer without advanced mathematics.

A simple -fs will fill the screen but with the video in the centre, not necessarily fullscreen as we know it.

I wrestled and failed with this also I'm afraid......

---

### Post by nothingspecial on 2011-05-14
> **andrew.46 said:**
> Oops, I see what you mean, nvlc crashes and burns on my system in a console :(.



I wrestled and failed with this also I'm afraid......

Thanks for trying :D

---

### Post by andrew.46 on 2011-05-14
> **nothingspecial said:**
> Thanks for trying :D

But now I remember wrestling with this before, this thread deals with the same problem:

How to play FULLSCREEN videos in console?
[http://ubuntuforums.org/showthread.php?t=1647927](http://ubuntuforums.org/showthread.php?t=1647927)

I am getting old when I don't clearly remember this thread from only a few months ago :(. Looks like I managed full screen here by finding out how my framebuffer was set from Lilo and setting this in MPlayer. I shall log out and see if my old post can enlighten me!!

---

### Post by nothingspecial on 2011-05-14
That's cracked it, mines 1024

I haven't got many videos on this thing to test it with but, it works with the ones  I have.

Thank's again :popcorn:

---

### Post by andrew.46 on 2011-05-14
> **nothingspecial said:**
> That's cracked it, mines 1024

I haven't got many videos on this thing to test it with but, it works with the ones  I have.

Great news! Now if I had only remembered that thread and that investigation of fbdev before.......

---

### Post by Oxwivi on 2011-05-14
> **SeijiSensei said:**
> Those subtitles require libass for correct rendering.  mplayer has a decent, but somewhat out-of-date version of libass.  However I recommend  the fork known as [mplayer2]("http://www.mplayer2.org/").  I built this from source recently and set it as my default mplayer version in smplayer.  There's no Ubuntu .deb available, but there is a Debian version [here](http://pkgs.org/debian-sid/multimedia-main-i386/mplayer2_2.0~git20110422-0.1_i386.deb.html).  Can't say if it works in Ubuntu, though.

mplayer2's multi-threading support helps quite a bit on multi-core machines.  If I watch an H.264-encoded video with the xv driver, I can see all the cores decoding the stream when I run "top" in a separate window.
Will libass allow me to get the subtitles properly rendered in Totem/Media Player?

---

### Post by andrew.46 on 2011-05-14
> **nothingspecial said:**
> That's cracked it, mines 1024

I apologise if this is already old news to you but you can of course put all your framebuffer options into an 'extension related profile' in your $HOME/.mplayer/config in something like the following fashion:

```

[vo.fbdev2]
xy=1024
fs=yes
flip=yes

```

etc etc according to your needs (fbdev2 works better for me!), this will substantially ease the pain of remembering and typing all the options :).

---

### Post by Starks on 2011-05-16
mplayer2+umplayer

---

### Post by screaminj3sus on 2011-05-16
VLC. Seems to be under more active development and its easy to get vaapi working out of the box.

---

### Post by nothingspecial on 2011-05-16
> **andrew.46 said:**
> I apologise if this is already old news to you but you can of course put all your framebuffer options into an 'extension related profile' in your $HOME/.mplayer/config in something like the following fashion:

```

[vo.fbdev2]
xy=1024
fs=yes
flip=yes

```

etc etc according to your needs (fbdev2 works better for me!), this will substantially ease the pain of remembering and typing all the options :).

Thank you for that. :D

---

