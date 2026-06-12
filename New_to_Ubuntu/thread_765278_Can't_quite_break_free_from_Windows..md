---
title: "Can't quite break free from Windows."
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Durandall on 2008-04-24
Hello everyone.

It's an odd feeling, being a noob again.  I'm new to Linux.  I've been running Hardy Heron for a couple weeks now.

Problems I'm having:

~ when the screen saver activates... I usually have to restart.  I've worked around that, by disabling the screen saver and turning off the monitor when I'm done.  But surely there's a better fix.

~ Video games... when I run one... it runs fine... but!  it's like I'm not getting a good v-sync.  the screen constantly flickers.  I can't explain the way it looks, really.  in the case of tuxracer, I can set the resolution to 1680x1050 - then it seems better... but not all games have that option.  and some do have the option, but it doesn't fix anything.

my rig - i have an ATI Radeon X1950 XTX, with drivers and stuff installed via Envy.  My monitor is a 22" LCD, Widescreen 1680x1050.  I have no idea what the hz is set to.  As of this moment, it's still running the Heron Beta.  I'm downloading the official release now - but I wont know if that fixes everything until hours from now.

Another question... I realized recently... I don't know how to do basic stuff anymore.  Like... burn an ISO.  Is there a Nero, or Nero equivalent for Ubuntu?

---

### Post by pytheas22 on 2008-04-24
> Another question... I realized recently... I don't know how to do basic stuff anymore. Like... burn an ISO. Is there a Nero, or Nero equivalent for Ubuntu?

You should be able simply to right-click on the ISO file and there will be an option like "Open with CD/DVD Creator," which makes burning it really easy.  If you want a more extensive program for CD/DVD creation, install k3b, which is extremely powerful.

Unfortunately I don't have an ATI card so I don't have any suggestions there, beyond trying the open-source drivers.  I think they work well for some cards, and not so well for newer ones, but I'm not positive.  Hopefully someone else knows more about it than I do.

---

### Post by diablo75 on 2008-04-24
> **Durandall said:**
>  As of this moment, it's still running the Heron Beta.  I'm downloading the official release now - but I wont know if that fixes everything until hours from now.

Well you're probably one of the last few running Beta.  You should consider downloading the official LTS iso via a torrent file so you'll get it fast, then try to install that fresh (if you've got nothing to lose....otherwise, just backup your home folder).

---

### Post by Perfect Storm on 2008-04-24
> ~ Video games... when I run one... it runs fine... but! it's like I'm not getting a good v-sync. the screen constantly flickers. I can't explain the way it looks, really. in the case of tuxracer, I can set the resolution to 1680x1050 - then it seems better... but not all games have that option. and some do have the option, but it doesn't fix anything.

Some games allows you to set the resolution their config files which can be found in your home directory (hidden).
If 1680x1050 don't work with a specific game - try with another widescreen resolution.

Moreover find out what Hz your screen support.

---

### Post by anachreon_ on 2008-04-24
Hey there,

It sounds like most of your issues are just ATI-related.  I gather that they've definitely improved in recent months, but from what I hear ATI's linux drivers just aren't on par in terms of maturity, stability or performance, with nVidia's right now.  And for performance reasons I would not recommend using the open source drivers if you're playing games.  

Also, are you playing linux games, or playing windows games through wine?

---

### Post by kk0sse54 on 2008-04-24
if i am still running hardy beta but i have kept up with all my updates do i have still have to download the official release and do a fresh install?

---

### Post by heartburnkid on 2008-04-24
> **Durandall said:**
> Another question... I realized recently... I don't know how to do basic stuff anymore.  Like... burn an ISO.  Is there a Nero, or Nero equivalent for Ubuntu?

Ubuntu comes packed with a basic CD/DVD writer program, but, speaking as a former Nero user myself, I much prefer Brasero.  It has the same level of flexibility and power.

I had heard somewhere that Brasero was going to be the default CD burner in HH, but I'm not too sure if that is the case or not.  In any case, it should be available from Applications | Add/Remove.

---

### Post by Perfect Storm on 2008-04-24
> **C!oud said:**
> if i am still running hardy beta but i have kept up with all my updates do i have still have to download the official release and do a fresh install?

If you have kept updated since then you don't need to do anything - Congrats you're on Hardy ^_^

---

### Post by Durandall on 2008-04-24
> **anachreon_ said:**
> Hey there,

It sounds like most of your issues are just ATI-related.  I gather that they've definitely improved in recent months, but from what I hear ATI's linux drivers just aren't on par in terms of maturity, stability or performance, with nVidia's right now.  And for performance reasons I would not recommend using the open source drivers if you're playing games.  

Also, are you playing linux games, or playing windows games through wine?

I'm playing Open Source games.  Tux Racer, Super Tux... Linux games, natively in Ubuntu. All downloaded through Synaptic.

And... I thought i was using ATi's drivers?  Envy... didn't that install the official driver for my ATi card?  I even have the Catalyst Control Center going.

---

### Post by Durandall on 2008-04-24
> **diablo75 said:**
> Well you're probably one of the last few running Beta.  You should consider downloading the official LTS iso via a torrent file so you'll get it fast, then try to install that fresh (if you've got nothing to lose....otherwise, just backup your home folder).

Downloading via torrent now.  You've just saved my life!  My download from Ubuntu still had 4 hours to go, then it eventually died.  The connection timed out.  I requested a free CD from the site - and found a torrent online.  It'll be done downloading in a couple minutes!!

That being said... how do I verify that this is the official Ubuntu release, as in - hasn't been tampered with in any way?

---

### Post by Fire_Chief on 2008-04-24
> **heartburnkid said:**
> Ubuntu comes packed with a basic CD/DVD writer program, but, speaking as a former Nero user myself, I much prefer Brasero.  It has the same level of flexibility and power.

I had heard somewhere that Brasero was going to be the default CD burner in HH, but I'm not too sure if that is the case or not.  In any case, it should be available from Applications | Add/Remove.

Yes, Brasero is included by default on Ubuntu 8.04.

---

### Post by mister_pink on 2008-04-24
You can do an md5 sum to check that its the official release, this also checks there hasnt been any corruption it as well. Check here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Edit: Just noticed there's no hashes up for hardy yet, they're here though: [http://releases.ubuntu.com/8.04/MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS)

---

### Post by Durandall on 2008-04-24
> **mister_pink said:**
> You can do an md5 sum to check that its the official release, this also checks there hasnt been any corruption it as well. Check here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Edit: Just noticed there's no hashes up for hardy yet, they're here though: [http://releases.ubuntu.com/8.04/MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS)

Well... thanks very much!

I was able to verify it, and it is in fact a legit ISO.  You've been a lot of help.

---

### Post by Mazza558 on 2008-04-24
> **Durandall said:**
> I'm playing Open Source games.  Tux Racer, Super Tux... Linux games, natively in Ubuntu. All downloaded through Synaptic.

And... I thought i was using ATi's drivers?  Envy... didn't that install the official driver for my ATi card?  I even have the Catalyst Control Center going.

It might be to do with using Compiz at the same time. Are you?

---

### Post by Crash 0verride on 2008-04-24
Your screensaver problem is that you have powersave mode activated.

I have the same problem just turn it off and put on a screensaver

---

### Post by Person98 on 2008-04-24
I fixed the screensaver thing by using xscreensaver instead of gnome-screensaver (you can get it through synaptic)

---

### Post by Paqman on 2008-04-24
> **Fire_Chief said:**
> Yes, Brasero is included by default on Ubuntu 8.04.

And rocks, too. I've found it a lot more reliable than K3B.

---

