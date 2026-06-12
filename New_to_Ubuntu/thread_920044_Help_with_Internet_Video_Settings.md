---
title: "Help with Internet Video Settings"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-14
Hello, I am having problems viewing full-screen youtube videos.  For some reason, whenever I maximize a youtube video to full screen, I see flashes of the desktop showing up periodically every 2-3 seconds.  I don't know why that keeps happening.

Here are my computer specs:
Q6600 Quad-Core Processor
3GB RAM (Not even being used past 15%)
ATI 128MB HD 2400 Video Card

I am not running a lot of programs, so my computer is definitely powerful enough to run full screen.

I don't have this problem with videos on VLC player or really anything else.  Can someone help?  I have Java installed, and I believe Flash.  Hmm...

---

### Post by lisati on 2008-09-14
I'm not sure of the answer, but sometimes I get a similar effect with MS-Windows when there are other processes (e.g. Skype) which pop up a window when something happens where it *might* want to alert you to something (e.g. another Skype user logging on or off)

---

### Post by RussW210 on 2008-09-14
I don't think that has anything to do with it.  I just started up my computer (nothing else running), turned on firefox and went to youtube and get it when the full-screen comes on... just flashes of the desktop background.  I am wondering if there is a setting in Compiz-Fusion that I have to change?

---

### Post by RussW210 on 2008-09-14
It seems I have solved the problem...

I went to the Advanced Desktop Effect Settings for Compiz Fusion.  Someone in a post about a year ago suggested:

"If not present install "Advanced Desktop Effect settings" , then uncheck "Unredirect fullscreen windows" in "General Options" and "Support legacy fullscreen" in the plugin "Workaround"."

That didn't work.  However, I did notice under the Utility: Workarounds, a box was unchecked called: "Fix screen updates in XGL with fglrx."

Bada bing, no more choppyness!

---

### Post by RussW210 on 2008-09-14
Nevermind, it is still happening after I restarted my computer... that is odd.  I checked and all the settings are the same on the Advanced Desktop Settings Manager but it is still flashing! =(

Anybody have an idea?

---

### Post by RussW210 on 2008-09-14
There is something screwy going on here... I unchecked "application switcher" (because for some reason when looking at the open applications they all came up as a blank white screen) and it stops glitching again on full screen.  But if I restart it will happen again.  Anybody?

---

### Post by RussW210 on 2008-09-14
Yep, still happening.  Is anybody out there?

---

### Post by RussW210 on 2008-09-14
Bump

---

