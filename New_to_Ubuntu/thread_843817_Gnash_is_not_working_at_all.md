---
title: "Gnash is not working at all"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by OpposingForce on 2008-06-28
Hi, I installed gnash because adobe's flash version for linux is really bad and crashes nonstop.  However gnash isn't even working.  On youtube it just shows a white screen, and no video.  If I set it to start as paused in preferences it just shows a black box, then when I click play in the menu, it goes white again.  Flash doesn't seem to work on pretty much any page.  I tried going into preferences and changing the player version, but it didn't work and now I can't change it back because I don't remember what it was set to by default and there's no "reset to default" button in the gnash menu.  I even tried going into synaptic and doing "complete removal" and then reinstalling, but upon reinstall all of the old preferences before I removed it are back, which is something I totally do not understand (I thought complete removals got rid of everything: including configuration files as well).  If anyone can help me get gnash working that would be great, I'd hate to have to go back to using adobe's proprietary piece of crap that crashes the browser constantly.

I'm using ubuntu 8.04 and firefox 3.0, gnash is at latest version.  Just tried creating symbolic links to the plugins folder for firefox to libgnashplugin.so but it did nothing

---

### Post by chrisod on 2008-06-28
I can't help with Gnash but have you tried the Adobe Flash 10 beta? Installing that solved my Firefox 3 / Flash issues.

---

### Post by OpposingForce on 2008-06-28
I tried it but I'm still getting crashes.  I guess I'll have to go back to flash 10 if no one can help.

---

### Post by madjr on 2008-06-28
gnash needs codecs, else it will show a white screen.

install the codecs (flv i think), search for them in ADD/Remove

---

### Post by dbsoundman on 2008-06-30
I'm actually having the same problems. I'm having strange issues with both versions of Adobe Flash (9 and 10) so I decided to try Gnash, and I get the white screen. I have gstreamer-ffmpeg already installed, which is the specified codecs necessary, and everything seems to be in order. I even tried purging all the other flash bits from my mozilla setup (nswrapper etc.). I did try the other open source flash player, I forget what it's called. It worked, but I was hoping gnash would work since it supports the actual youtube controls like full screen, etc...

-Dan

---

