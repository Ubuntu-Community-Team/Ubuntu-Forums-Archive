---
title: "youtube error"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by gpguillaume on 2008-08-11
I cant watch a youtube video.
I did install the latest flashplayer software.
Where the video is normally playing it's just white.
What to do?
I'm using ultimate version 1.8

---

### Post by ukripper on 2008-08-11
> **gpguillaume said:**
> I cant watch a youtube video.
I did install the latest flashplayer software.
Where the video is normally playing it's just white.
What to do?
I'm using ultimate version 1.8

Are you using Firefox or opera?

---

### Post by gpguillaume on 2008-08-11
firefox

---

### Post by lukjad on 2008-08-11
Do you have the NoScript addon installed? I do, and I need to temporarily allow youtube to view the clip.

---

### Post by Crafty Kisses on 2008-08-11
> **gpguillaume said:**
> I cant watch a youtube video.
I did install the latest flashplayer software.
Where the video is normally playing it's just white.
What to do?
I'm using ultimate version 1.8

You can technically uninstall Flash and reinstall it again, and if that doesn't work you can try Gnash.

---

### Post by iaskedalice09 on 2008-08-11
> **gpguillaume said:**
> I cant watch a youtube video.
I did install the latest flashplayer software.
Where the video is normally playing it's just white.
What to do?
I'm using ultimate version 1.8

Do you have Java JRE Installed? I actually forgot, and it seems like a no-brainer!

If you don't or don't know, in Terminal, type:

```

sudo apt-get install sun-java6-jre

```

---

### Post by rockerphil on 2008-08-11
just to be sure run this code:

sudo apt-get install flashplugin-nonfree

that's obviously the plugin for Flash, which is what plays YouTube videos. hope this helps,

Phil

---

### Post by iv2101 on 2008-08-11
I am having a similar issue on a RH-based distro with firefox 3 and the flash plugin. There are some things that it always plays (youtube works) and some things that is never plays and leaves a white space. 
@gpguillaume 
do you have a problem with _every_ flash page or only some pages?

---

### Post by gpguillaume on 2008-08-12
I have the same problem as you , only with some pages

---

### Post by gpguillaume on 2008-08-12
I've tried everything they said but without any result.
I have the same problem with seamonkey and qonkueror.
If the problem is Java,how can i turn it on or off
Thx for your help

---

### Post by lukjad on 2008-08-12
If you have JavaScript turned off through NoScript, you should see a blue 'S' with a red circle with a slash through it (Think of a no smoking or no parking sign). If you see it click on it and a menu will apear on top of it with something like "Allow youtube.com" and "Allow yming.com". Allowing those two will most likely allow you to view your youtube clips. 

If you (or someone else) have disabled JavaScript in Firefox globally, here is how to re-enable it. Open Firefox, got to Edit->Preferences->Content (it's visible at the top) and the look for the "Enable JavaScript". If there is a checkmark beside it, that is not the problem, simply hit the Close button at the bottom right hand corner since this is not your problem.

---

### Post by iv2101 on 2008-08-12
Now I noticed that I have the same problem on my ubuntu machine, in addition the issue with the RH machine.

---

### Post by teamcpc on 2011-03-12
If configure option is unavalaible [try this]("http://www.worldlingo.com/SYls3jUpdI3LCOCbu5k2HWSYriooRdnRFsZbrxpDzkcM-/translation?wl_url=http%3A%2F%2Fmalagaoriginal.blogspot.com%2F2011%2F03%2Fel-fallo-de-youtube-rosa-un-apano-y-la.html&wl_srclang=ES&wl_trglang=EN").

---

