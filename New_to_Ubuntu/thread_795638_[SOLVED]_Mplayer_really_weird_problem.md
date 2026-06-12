---
title: "[SOLVED] Mplayer really weird problem"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Ryuki_NdranC on 2008-05-15
Ok, i have installed from the repos, smplayer, vlc, xine and mplayer and all of them seems to work just "fine" (with some minor issues). I installed manDVD, DeVeDe and ripDVD and all of them work with mplayer.

My problem is when i try to load a preview of a video, the DVD programs call mplayer but even though i can hear the audio of my video and mplayer appears in "top", there is no windows or anything similar to a video windows anywhere. Eventually i have to killall mplayer so i can move on with my life.

I have properlly installed fglrx (ati x200m) and i have compiz-git (don't know if that have to do anything with my problem). Any of you guys has an opinion of what may be going on?

Im new to linux so any opinion will be appreciated.

Thanks in advance

P.S: mplayer uses x11 video driver. don't know why but some1 in the forums told me to put that on (is the onlyone that works i think)

---

### Post by tjwoosta on 2008-05-15
i have heard of someone else hear on the forums about a month ago with this same problem

this is what he had to do to fix it

first open up mplayer.conf like this
```

sudo gedit /etc/mplayer/mplayer.conf

```

near the top of the page you will se a part that  looks like this
> 
##################
# video settings #
##################

# Specify default video driver (see -vo help for a list).
vo=x11


yours will say vo=somethingelse,  just change it to say vo=x11

if this doesnt solve the problem you can try other vo options

for a list of other vo options open a new terminal and type this
```

mplayer -vo help

```

---

### Post by Ryuki_NdranC on 2008-05-15
I love you :)

It worked perfectly, it was in vo=vx.

so far i can guess that for some reason when i installed mplayer under hardy heron (didn't happened on gutsy) the default driver was setup in vx and even i did change (GUI interface :s) the default driver to x11 it didn't change in the really default command line mplayer.

I got that right? I swicth to linux because i love computation and got tired of windows keeping me from knowing how does a real smart OS works.

So any extra explanation you or other may add it will be greatly appreciated because for some reason i didn't find someone with a problem related to mine. Maybe i didn't use the correct search keywords.

Once again thanks and for now SOLVED :)

---

### Post by tjwoosta on 2008-05-15
glad to help out


here is the link to the thread i was talking about where i got the info

[http://ubuntuforums.org/showthread.php?t=784829]("http://ubuntuforums.org/showthread.php?t=784829")

---

