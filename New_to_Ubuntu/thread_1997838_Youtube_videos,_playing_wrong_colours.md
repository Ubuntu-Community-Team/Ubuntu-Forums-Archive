---
title: "Youtube videos, playing wrong colours?"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by rubberduck1968 on 2012-06-05
Hi all, 

I'm suck here and need some help with this problem of Youtube playing wrong colours on its videos. Reds are blue, yellows are green and so on. It's only YouTube's web site that seems to have this problem for me, any other site, like BBC iPlayer doesn't have a issue with the video playback. Even videos from my camera are fine aswell as DVD's.
At first I thought it was FireFox or maybe Flashplayer add-on's but cannot find anything on forums or Google. Ive tried uninstalling, then reinstalling FireFox and Adobe Flash but to no avail.
If I download a YouTube video to my desktop it works fine, colours are all correct, any else had this problem?

P.S. I'm running Nutty 11.10

Cheers, Martin.

---

### Post by haqking on 2012-06-05
> **rubberduck1968 said:**
> Hi all, 

I'm suck here and need some help with this problem of Youtube playing wrong colours on its videos. Reds are blue, yellows are green and so on. It's only YouTube's web site that seems to have this problem for me, any other site, like BBC iPlayer doesn't have a issue with the video playback. Even videos from my camera are fine aswell as DVD's.
At first I thought it was FireFox or maybe Flashplayer add-on's but cannot find anything on forums or Google. Ive tried uninstalling, then reinstalling FireFox and Adobe Flash but to no avail.
If I download a YouTube video to my desktop it works fine, colours are all correct, any else had this problem?

P.S. I'm running Nutty 11.04

Cheers, Martin.

Probably Nvidia related.

Right click on the video and disable hardware acceleration then reload the video.

Peace

---

### Post by rubberduck1968 on 2012-06-05
> **haqking said:**
> Probably Nvidia related.

Right click on the video and disable hardware acceleration then reload the video.



Thank you for your reply, just tried it, can't untick the box and then it crashes. 

Martin.

---

### Post by rubberduck1968 on 2012-06-05
Its got to something to do with Adobe Flash player, only I can't work out why it's not working right. There just seems no way to cure this problem. Seems if I roll back the the Flash update version some videos play normally others cannot play without the update. Any video set up to play the new YouTube HTML5 player work ok.
I've tried updating everything, uninstalling, changing add-ons and even reinstalled FireFox, nothing will let me use the Flash player settings and disable hardware acceleration . Perhaps its a 'Nvidia' thing after all or maybe new update from Adobe would help, either that or I'll try using Google Chrome and see if that works.

Anyone comes up with a fix or ideas, I'm all ears!

Martin.
[B]
[/B]

---

### Post by GoodPanos on 2012-06-07
It's like watching the Blue Man Show :lolflag:

Anyways, I end up having to remove Adobe Flash Plugin.  It worked fine then both with Chrome and Firefox.

Some specs in case it helps:
[LIST]
[*]Using Lubunut 12.04
[/LIST]
[LIST]
[*]nVidia Graphics Card
[/LIST]

---

### Post by rez182 on 2012-06-08
I have the same problem. All flash videos have blue colour...

---

### Post by rubberduck1968 on 2012-06-09
Nice to I'm not the only view the YouTube world in 'Avatar' mode.

As for removing Adobe Flash Plugins, I find I can't watch anything, not even the news channels. So how do you get around this without Adobe GoodPanos?

Martin.

---

### Post by devanson on 2012-06-16
> **rubberduck1968 said:**
> Nice to I'm not the only view the YouTube world in 'Avatar' mode.

As for removing Adobe Flash Plugins, I find I can't watch anything, not even the news channels. So how do you get around this without Adobe GoodPanos?

Martin.

IS there any updates on this issue?

---

### Post by Curtis6767 on 2012-06-16
> **devanson said:**
> IS there any updates on this issue?

If you're using the latest version of Firefox, 13/14, then go to Firefox plugins and download Flash-Aid.

Flash support is built into Chrome, so if you're using Chrome and getting this error then it's something else. 

darkod also has some tips in the linked thread. Scroll to post #3.

[http://ubuntuforums.org/showthread.php?t=1983218](http://ubuntuforums.org/showthread.php?t=1983218)

---

### Post by dodo3773 on 2012-06-16
This problem is related to a conflict in flash and the nvidia vdpau library. You need to either patch vdpau to get it to work correctly or downgrade flash to an older version.

---

### Post by rubberduck1968 on 2012-06-16
> **Curtis6767 said:**
> If you're using the latest version of Firefox, 13/14, then go to Firefox plugins and download Flash-Aid.

Flash support is built into Chrome, so if you're using Chrome and getting this error then it's something else. 

darkod also has some tips in the linked thread. Scroll to post #3.

[http://ubuntuforums.org/showthread.php?t=1983218](http://ubuntuforums.org/showthread.php?t=1983218)

Thanks for that, think that's my next port of call having read that thread. If that doesn't work I'll try *dodo3773* idea.

Martin.

---

### Post by Autodave on 2012-06-16
> **rubberduck1968 said:**
> Thank you for your reply, just tried it, can't untick the box and then it crashes. 

Martin.


First of all, try maximizing the video to full screen and then try clicking to disable hardware acceleration: that usually works.

If that does not work, try the Flask Aid plug in. 

Lastly, if all else fails, install GNASH from the repositories.

No matter what you do, exit Firefox and then go back in to see if it worked.

---

### Post by anewguy on 2012-06-16
Take a look at [this]("http://askubuntu.com/questions/117127/flash-video-appears-blue") thread.

Dave ;)

---

### Post by rubberduck1968 on 2012-06-16
Yay! it's sorted, I downloaded 'Flash-Aid' and it's cured the problem. Don't know if will work with every PC but it worked here. 

Thanks to everyone for there help and advise. 

Martin.

---

