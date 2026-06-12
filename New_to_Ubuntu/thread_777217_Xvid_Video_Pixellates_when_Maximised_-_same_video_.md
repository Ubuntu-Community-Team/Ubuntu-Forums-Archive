---
title: "Xvid Video Pixellates when Maximised - same video displays OK in Windows"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by johnnyking on 2008-05-01
Hi,

Had a bit of trouble installing Ubuntu - now it's working I'm having a lot of fun trying things out.

One thing I'm having trouble with is watching Xvid tv episodes. I installed the plugin for movie player to play Xvid stuff. I also installed VLC player.

- The same thing is happening with both. The video looks slightly choppy and very blocky when I maximise the video to watch it fullscreen.

I've got the ATI graphics drivers installed that Ubuntu recommended to me.

How can I fix this? It isn't just one video - it's all of them. The video's look fine in Windows when i play them.

---

### Post by johnnyking on 2008-05-01
Bumpp

---

### Post by SOULRiDER on 2008-05-01
I used to have this problem in my Debian install. I had to reinstall Codecs, mind you, its Debian and not Ubuntu. Look for seveas packages for hardy.


PS: Do not bump topics, its highly annoying, it will make them not show up as unanswered and will piss people off in general resulting in you getting no help.

---

### Post by peakshysteria on 2008-05-01
ATI is hellish to solve. Haven't made it myself yet with my ATI X700 EXCALIBUR PRO on Hardy 64 bit. But i recommend to uninstall the ATI driver you currently are using and installing [ENVY]("http://www.albertomilone.com/nvidia_scripts1.html"). You can also find it via Synaptic. That might solve things for you. I myself have given up for the time being. But I'm not giving up for good :) There a lot of guides around.

It would also be wise to post your specs, OS, card type etc....that way people might better understand and help you with your problem...

---

### Post by SunnyRabbiera on 2008-05-01
It might be best to just forget about using effects with a ATI card, you may just want to roll back your system a bit and forget about desktop effects.

---

### Post by peakshysteria on 2008-05-01
I had a perfectly nice and smooth working compiz after a clean install last week (without the proprietary ATI drivers). I was tempted once again to get my video playback upgraded and went for the proposed ATI drivers in the drivers manager. Messed it all up. Had to uninstall the driver. And when i went beck to the same setup as before no I can't enable Compiz at all since the screen and windows goes all choppy and freezy. Not sure why. The original out of the box setup was really sweet. Love Compiz and I must say it's hard to go on without it :) But I'll find it out before the end.....
 
But johnnyking if your just going for better videoplayback you should go for ENVY or some of the other howtos in the forums.

---

### Post by johnnyking on 2008-05-02
> **peakshysteria said:**
> 
But johnnyking if your just going for better videoplayback you should go for ENVY or some of the other howtos in the forums.

Thanks. Will do.

It's an ATI X1850XT.

Bought it when I used to play games. I don't anymore... so I'm actually going to buy a cheap graphics card that's passively cooled (so my systems quieter)

Would it be better to get an Nvidia chipset when I buy one?

---

### Post by johnnyking on 2008-05-02
Just installed EnvyNG. Uninstalled my old ATI drivers - installed the new ones using the automatic setting. Still no luck with video playback.

I'm using the GStreamer ffmpeg video codec. Can't find another one to use - but it seems like most people use that one - so that shouldn't be causing the problem?

This is so frustrating. I really like all I've seen in Ubuntu and it's fun to use a new operating system. Not being able to watch video's is somewhat frustrating.

---

### Post by peakshysteria on 2008-05-06
Are the driver enabled and OK? Is it only your playback which is the problem now??

If so, install Mplayer and/or VLC from:

System --> Administration --> Synaptic.

They'll play just about anything you try :)

---

### Post by johnnyking on 2008-05-10
I got the problem sorted - but not in an ideal way. Bought a v cheap Nvidia 6200 graphics card, and swapped out my ATI card.

Now video playback works a treat!

---

