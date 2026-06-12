---
title: "Firefox 3: 8.04 Quicktime Apple trailers"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by rxchaos on 2008-05-14
Hey all,

there are a ton of posts about this but they all seem to kind of go over my head involving things beyond terminal.  I dislike Totem with apple trailers and was trying to use mplayer.  I was wondering if I could use the mplayer plugin for mozilla for both embedded .mov files ([http://www.apple.com/trailers/miramax/reprise/trailer/](http://www.apple.com/trailers/miramax/reprise/trailer/)) and also non embedded .mov files ([http://www.apple.com/trailers/disney/thechroniclesofnarniaprincecaspian/hd/](http://www.apple.com/trailers/disney/thechroniclesofnarniaprincecaspian/hd/)).  

I've attached a screenshot of my firefox plugin manager.  I've removed the totem plugin and put in the wmplayer plugin.  But still to no avail mplayer plugin loads but there is no video.  It loads the entire video before playing a single clip, then all it plays is sound.  It took about 4-5minutes to load everything before playing, which is unusual (I am used to less than 45second load times with XP/MAC OS, not trying to put ubuntu down but trying to fix my problem ).  I've attached screen shots of what each looks like (embedded and non embedded).  Anyone have any experience to this problem?

Thanks

---

### Post by Xiong Chiamiov on 2008-05-15
Do you know that it is the mplayer plugin trying to play the videos?  Does mplayer (not the plugin, just separate) play quicktime files ok?

---

### Post by rxchaos on 2008-05-15
I just downloaded a .mov file to my desktop and it opened with totem and it played.  When I opened the file through mplayer I got this error. (attached)

---

### Post by tjwoosta on 2008-05-15
do this


```
gedit /etc/mplayer/mplayer.conf
```

then change this part (i dont remember what it originally said but put x11 like i did)
> 
# Specify default video driver (see -vo help for a list).
vo=x11


for a list of all availabe options go to a seperate terminal and type 
```
mplayer -vo help
```

---

### Post by rxchaos on 2008-05-15
I got an error: i cant save without permission

---

### Post by billgoldberg on 2008-05-15
> **rxchaos said:**
> I got an error: i cant save without permission

put "sudo" before the command (without the "")

---

### Post by rxchaos on 2008-05-15
the mplayer config change seemed to change something.  Now it looks like everything loads and on the non embedded one the external player loads and shows the first still of the video (green preview screen).  But, it still doesn't play.  I let it sit for a couple minutes and nothing.  I can fast forward and even click at different parts and it will show a still of the video at that part but will not play.

---

### Post by tjwoosta on 2008-05-15
try some of the other video output options

for a list of availible vo options type this in a new terminal
```

mplayer -vo help

```

just put one of those inplace of the x11 then save and retry mplayer

---

### Post by tarasin on 2008-07-24
:)> **rxchaos said:**
> Hey all,

there are a ton of posts about this but they all seem to kind of go over my head involving things beyond terminal.  I dislike Totem with apple trailers and was trying to use mplayer.  I was wondering if I could use the mplayer plugin for mozilla for both embedded .mov files ([http://www.apple.com/trailers/miramax/reprise/trailer/](http://www.apple.com/trailers/miramax/reprise/trailer/)) and also non embedded .mov files ([http://www.apple.com/trailers/disney/thechroniclesofnarniaprincecaspian/hd/](http://www.apple.com/trailers/disney/thechroniclesofnarniaprincecaspian/hd/)).  

I've attached a screenshot of my firefox plugin manager.  I've removed the totem plugin and put in the wmplayer plugin.  But still to no avail mplayer plugin loads but there is no video.  It loads the entire video before playing a single clip, then all it plays is sound.  It took about 4-5minutes to load everything before playing, which is unusual (I am used to less than 45second load times with XP/MAC OS, not trying to put ubuntu down but trying to fix my problem ).  I've attached screen shots of what each looks like (embedded and non embedded).  Anyone have any experience to this problem?

Thanks
I have managed to get the mplayer 'quicktime ' plugin to work perfectly. After much hunting around on the web I came across a Archlinux forum question which explained that sometimes the apple plugin wont work because it is not the latest plugin i.e. 'quicktime plugin 7' and the mplayer plugin says it is 'quicktime 6/7'. I believe this has more to do with the website not sending the content because it does not think your plugin is compatible.

To remedy this the webpage said to edit the pluginreg.dat file located in your /home/yourname/.mozzila/firefox/ folder.
make sure to backup the file before editing it.

Look for references to 
**:$ QuickTime Plug-in 6.0 / 7:$ 7 0:** 
and change it to **:$ QuickTime Plug-in 7:$ 7 0:**
note:**6.0 /** has been deleted
I found two references to this line in mine.
save it
restart Firefox and the pluginreg.data will regenerate itself and leave your alterations.
now go and watch some apple trailers.

---

### Post by philinux on 2008-07-24
VLC Totem and Mplayer can play these non-embedded files but.

VLC - video hangs 2/3rds through.
Mplayer crashes with errors.

Totem plays the whole thing fine.

Unfortunately all suffer from stutter.

---

### Post by ogromano on 2009-01-28
Hello...

I've recently started having a similar issue as the first poster. Up to a few automatic updates ago (not sure which) whenever I watched the trailers in the apple page the usual preview black frame of apple came out and the video started playing within a couple of seconds. Now, the mplayer plugin has taken over these filetypes and I have no idea how to put it back the way it was since it worked flawlessly. With this plugin, sometimes it works and sometimes it doesn't, and I always get double controls, (mplayer's and apple's). Sometimes I have to wait for the full video to be buffered before I can play it and sometimes even after that it doesn't want to play it. (see pic)

I've tried Tarasin's sugestion and it seems like it works a little better, but it still hangs up from time to time.

Something else I don't understand is why does Firefox need so many plugins for media playing (see pic)

Thanx,

 - OgRo -

---

