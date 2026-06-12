---
title: "Rythmbox doesn't play and VLC has a weird echo"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by cheddarva on 2011-10-01
Hi, sorry, I have no idea what the heck just happened... My rythmbox  that was seemingly fine last night now refuses to play an mp3. Meanwhile  VLC is playing videos with this weird echo filter added to it, and it's  not for the same video.

What's weird is that Movie Player (the one that comes with ubuntu) is  still able to play things... but apparently none of my other players  can....

I just torrented a movie, and watched it for the first time... could it be some sort of ubuntu virus?... 

sounds kinda far fetched but I can't think of what else it could be...

Maybe plugins?...

Help?

---

### Post by cheddarva on 2011-10-01
I actually found out what was wrong, it has something to do with my pulse audio... not sure what that's about... 

I found what to do here
<http://ubuntuforums.org/showthread.php?t=1230561>

What I did was the following:

sudo killall pulseaudio

sudo apt-get purge pulseaudio

Honestly I don't know what I did... all I know is now VLC has no echo and rythmbox doesn't have an echo...

Be nice people, I'm a noob, I'm monkey see monkey do =D>

Question... do I have to do anything else or can I just leave things like this?...

---

### Post by cheddarva on 2011-10-02
oh..... my volume controller is gone... hmm... maybe that's what pulse audio is...

---

### Post by cheddarva on 2011-10-02
Lol... ok, so here's what I did... I tried

sudo apt-get install pulseaudio... but when I did that my sound messed up again...

So I uninstalled it again, and now it's working fine.... except without volume control...

Any alternatives?...

I have volume + and - keys on my keyboard that I like to use, but doesn't have to...

Now I'm using one called ALSA, but it has no taskbar icon... kinda annoying...

---

### Post by qkall on 2011-10-06
try 

alsamixer

---

