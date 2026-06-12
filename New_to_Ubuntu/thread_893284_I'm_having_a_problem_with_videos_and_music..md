---
title: "I'm having a problem with videos and music."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by LeetSpeak on 2008-08-18
Ok, this never happened on Vista, but it started happening when I switched to Linux. I have no idea why it happens but everytime I go to youtube, and try to watch a video, the video will work for about 10 seconds, then it just stops and a white box just appears. Same with myspace, when I'm trying to listen to music, it either works for a couple of seconds or it doesn't even load the song. Can someone tell me what the problem is and how I can fix it?

Thanks in advance! :)

---

### Post by rockerphil on 2008-08-18
ok, i'm guessing you're trying to run all of this through Flash (i know that's what YouTube runs on) so open up a terminal and run this

sudo apt-get install flashplugin-nonfree

and that should do the trick, hope it helps,

Phil

---

### Post by LeetSpeak on 2008-08-18
It says "flashplugin-nonfree is already the newest version." And yea I remember downloading it the first day I got Linux. Any other ideas of what it can be?

---

### Post by rockerphil on 2008-08-18
my next attempt would be to run this

sudo apt-get update

and 

sudo apt-get dist-upgrade

that should update your system, i'd also check to see what version of Flash you're running, because the latest Beta release still has some bugs in it.

Phil

edit: also, be sure the plugin is enabled

---

### Post by nicedude on 2008-08-18
there is a flash addon for firefox that you can use I believe. Open firefox and under tools click addons -> then get addons -> now search mozilla addons for flash and see what is available.

---

### Post by LeetSpeak on 2008-08-18
Yup, that did it, installed a plug-in that works really good. But, now I have a different problem, I don't know why but whenever I used to go on my myspace with vista on Internet Explorer ( newest version ) My fonts would be normal looking, now with Firefox, its all small and in cursive. Anyone know how I can change that? Thanks btw for the flash help! :)

---

