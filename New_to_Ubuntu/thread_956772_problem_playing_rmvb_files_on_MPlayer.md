---
title: "problem playing rmvb files on MPlayer"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by ahmed_mo2nis on 2008-10-23
Ok so I tried doing these steps

[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

[http://ubuntuforums.org/showthread.php?t=616353](http://ubuntuforums.org/showthread.php?t=616353)

and after I finished it I can play rm, ram & ra files (audio)

as for rmvb files when I try to play one it gives me sound only + this message

"cannot find codec matching selected -vo and video format 0X30345652"

can somebody please tell me what went wrong :confused:

---

### Post by ahmed_mo2nis on 2008-10-24
up

---

### Post by ahmed_mo2nis on 2008-10-24
up up

---

### Post by sacauntos on 2008-10-26
I had the same problem. I ended up downloading real player for linux just to watch rm files at the price of getting ads in my computer, it just sucked but it did the trick 'till I got bored. Look for helix player in the forums and maybe you'll succeed...

---

### Post by ahmed_mo2nis on 2008-10-26
the reason why I tried to play real files in MPlayer was that the real player had some problems while it played. But thanks any way I'll try to find that other player you have mentioned

---

### Post by inigmatus on 2008-11-02
"cannot find codec matching selected -vo and video format 0X30345652"

I was getting this error when loading a chabad.org movie. For some reason Mplayer would only play audio but no video for .rm movies, even thought I followed

Comprehensive Multimedia & Video Howto
[http://ubuntuforums.org/showthread.php?t=766683&highlight=mplayer+ram](http://ubuntuforums.org/showthread.php?t=766683&highlight=mplayer+ram)

I tried Gecko Media player but had the same problem. They played all other rm movies fine at other sites, but at this particular website (chabad.org) they weren't playing video at all, just sound. So I uninstalled Gecko and went back to Mplayer. Still no luck. I tried restarting, and finally gave up and installed Real Media Player. No luck - since in Firefox 3 my about:plugins page showed it was only set up for rpm and Mplayer was still setup for rm files, and chabad.org uses rm files. For some reason Mplayer was still the default player for rm files, which prevented Real Media Player from being the default.

So, I solved the problem real easy by simply removing Mplayer as a plugin for rm files:

sudo rm /usr/mozilla/plugins/mplayerplug-in-rm.so
sudo rm /usr/mozilla/plugins/mplayerplug-in-rm.xpt

I restarted my browser, checked about:plugins and didn't find "rm" anywhere, but went to chabad.org anyways, played the movie, and bam, the Real Player plugin loaded and the movie played! Problem solved.

---

