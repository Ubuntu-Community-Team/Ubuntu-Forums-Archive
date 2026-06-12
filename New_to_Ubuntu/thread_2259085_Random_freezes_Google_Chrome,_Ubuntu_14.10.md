---
title: "Random freezes Google Chrome, Ubuntu 14.10"
date: 2015-01-01
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2015-01-01
Hello Ubuntu Forums community!

Google Chrome seems to be crashing on me unexpectedly, generally while I'm opening or watching a video in YouTube

Sometimes it's just Chrome, and I can FC it, but sometimes it's the whole session. In that case switching to a tty, and then switching back to virtual console 7 just makes the cursor appear on top of the tty login.

In that tty, running [FONT=Courier New]ps ax | grep chrome[/FONT] outputs something similar to:
```
4202 pts/3    S+     0:00 grep --color=auto chrome
```

The only way to make the system usable again is killing gnome-session or restarting the display manager via [FONT=Courier New]sudo -i restart gdm[/FONT].

This machine has Ubuntu GNOME 14.10 (dual-boot w/ windows 8), no updates done, no GNOME 3 PPAs added. This is the PC I use for maximum stability, and find this quite annoying, and going against the purpose I didn't preform updates or add GNOME 3 PPAs in the first place.

Help?

P.S. I would've stayed with Ubuntu 14.04 LTS in the first place, if it didn't break and cause me to upgrade.

---

### Post by vasa1 on 2015-01-01
Do you have hardware acceleration set to "on" in Chrome's settings? Try turning it off.

---

### Post by Jonathan Precise on 2015-01-03
Hello vasa1. Thanks for the reply.
I just saw your reply, sorry for the late response.

Thanks for the tip, just changed the setting, will see the results, probably by the end of this day.

-Jonathan

---

### Post by Jonathan Precise on 2015-01-03
Update: Chrome is still crashing on me :(

Hardware acceleration seems not to be the issue here.

---

### Post by Jonathan Precise on 2015-01-24
Update: Just ran a Chrome update. No session-freezing for now, but Chrome still freezes, hitting the X button numerous times to bring up the "Force Quit" to exit Chrome, then reopening and hitting "Restore".

---

### Post by monkeybrain20122 on 2015-01-24
I have the same issue with Firefox on 14.10. Same version works with no issue on 14.04. Meanwhile Chrome has another problem [http://ubuntuforums.org/showthread.php?t=2251728](http://ubuntuforums.org/showthread.php?t=2251728)

I will pass 14.10.

---

### Post by Jonathan Precise on 2015-01-24
> **monkeybrain20122 said:**
> I have the same issue with Firefox on 14.10. Same version works with no issue on 14.04. Meanwhile Chrome has another problem [http://ubuntuforums.org/showthread.php?t=2251728](http://ubuntuforums.org/showthread.php?t=2251728)

I will pass 14.10.

Hey monkeybrain20122, thanks for the reply.

I actually would have stayed with 14.04, but an update broke internet, hardware acceleration for Unity, everything was so...      slow...

Update to 14.10 fixed everything, but brought this up...

I'm at lost now. Any other ideas?

---

### Post by Jonathan Precise on 2015-01-28
Update: Chrome 40.something now freezes more constantly. :(

---

### Post by JeQhdMD on 2015-01-28
Have you noticed any improvement on Youtube in past 24 hours re default for video is now html5 vs flash.   You could also disable flash (or uninstall it) to test further if problem connected to flash.

---

### Post by Jonathan Precise on 2015-01-30
Hello JeQhdMD.

I have HTML5 enabled on YouTube, I think I didn't even install flash on it... but not sure of that. Actually, I've seen that normally the freeze occurs in YouTube. Maybe that's causing problems?

I shall disable HTML5 playing in Chrome and post back the results.

---

### Post by JeQhdMD on 2015-01-30
Often, flash can cause all kinds of stability issues depending on other settings in the browser.    The latest Firefox (v35) will also now utilize html5 . . . and they've improved sync.   Might be worth a look at if nothing but for better security.

---

### Post by carman594 on 2015-02-01
> **JeQhdMD said:**
> Often, flash can cause all kinds of stability issues depending on other settings in the browser.    The latest Firefox (v35) will also now utilize html5 . . . and they've improved sync.   Might be worth a look at if nothing but for better security.

I too am having this problem. This just started for me a couple days ago, never any issues before that. I'm guessing it's related to a recent update... hopefully it will be fixed soon. Firefox doesn't have this issue. I wouldn't mind using Firefox, however, I rely on a few different Chrome extensions that aren't available for Firefox.


Very frustrating!!

---

### Post by JeQhdMD on 2015-02-01
Yeah Carman, I understand as Chrome is awesome but it's also more than a browser . . . it's a mini-OS but Linux users will need to be mindful that a "Google Only" universe is not much different than Microsoft hegemony (Google's just a lot more innovative and better managed company).   I use  Firefox as well as Chromium/Chrome to hopefully maintain real competition and avoid lock-in.

---

### Post by monkeybrain20122 on 2015-02-01
> **Jonathan Precise said:**
> Hello JeQhdMD.

I have HTML5 enabled on YouTube, I think I didn't even install flash on it... but not sure of that. Actually, I've seen that normally the freeze occurs in YouTube. Maybe that's causing problems?

I shall disable HTML5 playing in Chrome and post back the results.

Chrome uses html5 by default on Youtube. Firefox would use Flash if it is installed and it would use html5 if you disable flash. It has been like that for a few years, you no longer have to opt in to html5 like long time ago.

---

