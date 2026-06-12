---
title: "mpd + ncmpc or a simple music app"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Inxsible on 2008-07-11
I was trying to weigh the advantages of using mpd + a client (ncmpc) as against cplay

I use the mpd + ncmpc on my Arch partition but cplay on my debian + fluxbox partition.

What would be the advantages of using mpd? I do plan to connect to this machine (connected to my music system) using another machine, but I can also do that via ssh and controlling cplay which i always start with screen.

What I am trying to get at is...what does mpd give me additionally?

---

### Post by spupy on 2008-07-11
MPD can stream music over the network.
EDIT: Wikipedia says that MPD does not stream audio, although I remember a tutorial on how to set this up. (Even as an internet radio)

---

### Post by Inxsible on 2008-07-11
But given that the machine is connected to my music system and my external hard drive where all my music is...I don't see how streaming helps me.

and I can control the music simply by ssh'ing into this machine from my personal laptop.

---

### Post by atomkarinca on 2008-07-11
If I remember correctly streaming is done via a Shoutcast or Icecast server.

If you are comparing mpd and cplay, the major difference is that mpd is just a daemon. You select the UI. Other than that with mpd you just define your music directory and it can update its database, but -to my little experience- with cplay you should define the playlist every time.

---

### Post by Inxsible on 2008-07-11
> **atomkarinca said:**
> If I remember correctly streaming is done via a Shoutcast or Icecast server.

If you are comparing mpd and cplay, the major difference is that mpd is just a daemon. You select the UI. Other than that with mpd you just define your music directory and it can update its database, but -to my little experience- with cplay you should define the playlist every time.But we have to create playlists in both.

In fact I was surprised that the playlists created by mpd - or rather ncmpc - did not play in other players even though they were standard m3u files.

One thing about mpd is that once you define your music databse....ncmpc always starts in that folder...whereas in cplay - I had to use the -cd option for urxvt to start in my music directory..not a great deal though.

---

### Post by atomkarinca on 2008-07-11
> **Inxsible said:**
> One thing about mpd is that once you define your music databse....ncmpc always starts in that folder...whereas in cplay - I had to use the -cd option for urxvt to start in my music directory..not a great deal though.

That's what I was trying to get to :) The thing I like about mpd is you can set up your playlist, start playing and then close the UI. Sometimes I do that while shutting down and I get music on the next startup. Cool, eh?

---

### Post by Inxsible on 2008-07-11
> **atomkarinca said:**
> That's what I was trying to get to :) The thing I like about mpd is you can set up your playlist, start playing and then close the UI. Sometimes I do that while shutting down and I get music on the next startup. Cool, eh?Yes but I get the exact same effect if I use screen to start up my cplay.

I use this command as my shortcut to start cplay```
urxvt -T "cplay" -cd /media/WD500/Music -e screen -S cplay cplay
```

Gets me directly to my music directory and then I can add to the playlist and start playing.

Not trying to bash one or the other...just wondering if its worth it to have the mpd daemon running in the background all the time as opposed to starting cplay when I want.

---

### Post by atomkarinca on 2008-07-11
I just checked the ps_mem.py and mpd daemon uses 1 MiB ram. I guess it boils down to personal preference. To me mpd feels more intuitive.

---

### Post by Inxsible on 2008-07-11
> **atomkarinca said:**
> I just checked the ps_mem.py and mpd daemon uses 1 MiB ram. I guess it boils down to personal preference. To me mpd feels more intuitive.
Its funny you mention that...I just listed my ps_mem.py on the arch forums..

Check it out here

[http://bbs.archlinux.org/viewtopic.php?id=51592](http://bbs.archlinux.org/viewtopic.php?id=51592)

mpd takes up more memory than cplay + mpg123

---

### Post by atomkarinca on 2008-07-12
Wow, I guess I checked its ram usage while not playing. ~10 MiB is a lot of resources for a music player. I'm using Consonance now and it uses only 4 MiB, but it's a graphical player.

---

