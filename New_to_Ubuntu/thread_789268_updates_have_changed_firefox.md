---
title: "updates have changed firefox"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Screwtape on 2008-05-10
Hey-

So after the most recent updates, the firefox window now takes up the whole screen whenever it starts. It's not the "fullscreen" setting and it's not a maximized window; instead, it just pops up over the start bar at the top of the screen and the x box and resize buttons are offscreen somewhere. I have to pick "fullscreen" and then use the "maximize" button to return it to normal. It's not fatal, but it is annoying. Any fixes?

Using Hardy on a a Toshiba satellite with the hated Intel 965 graphics card and a Centrino processor.

Thanks.

---

### Post by penguinbreath on 2008-05-10
Maybe a re installation of Firefox through synaptic will help? What version of Firefox is this?
Also do you have compiz on? Maybe you could try turning it off.

---

### Post by Screwtape on 2008-05-11
> **penguinbreath said:**
> Maybe a re installation of Firefox through synaptic will help? What version of Firefox is this?
Also do you have compiz on? Maybe you could try turning it off.

Tried both to no avail; Firefox is 3.0b5.

---

### Post by penguinbreath on 2008-05-12
The last thing I can thing of for the Firefox problem is to try a "complete removal" of Firefox in Synaptic (which I believe will erase all of its configuration files), and then install it again. Though I am not sure if doing this will affect any other Gecko based browsers you have installed. 

You could also try seeing if Swiftweasel works, which is pretty much Firefox. Swiftweasel should also works with your Firefox extensions (Swiftweasel 2 worked with all my Firefox extensions). However I am not sure of how resent and stable the last build was for Swiftweasel 3.
[http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)

You could also try using Epiphany, which is a Gecko based browser like Firefox. I believe the command for getting it from the terminal would be :
```
sudo apt-get install epiphany-browser 
```

I really do not know much about Linux/Ubuntu. Hopefully someone with more experience can help you here.

---

### Post by lswest on 2008-05-12
i seem to remember having the same problem, but i don't remember how i fixed it, sorry.  Maybe an update took care of it?  Or you could try deleting your firefox profile somewhere under ~/.mozilla/firefox/profiles/ (or something along those lines, not 100% sure, and i can't check atm)

---

### Post by MarkX on 2008-05-12
Firefox3 wasted a day for me. Reinstall firefox 2 and dump the new one.

I don't understand why on earth they are trying to upgrade people to a BETA anything which is widely reported to be causing trouble.

---

### Post by barney385 on 2008-05-12
> **MarkX said:**
> Firefox3 wasted a day for me. Reinstall firefox 2 and dump the new one.
 
I don't understand why on earth they are trying to upgrade people to a BETA anything which is widely reported to be causing trouble.
 
I have to agree with you.
 
It's still having compatibility issues obviously.

---

### Post by jbor7755 on 2008-05-19
This is now happening to me too. The only solution I have is to hit F11 until you get the title bar and the gnome toolbar back again.  It's killing me and must be affecting some other people too.

---

### Post by meborc on 2008-05-19
> **MarkX said:**
> Firefox3 wasted a day for me. Reinstall firefox 2 and dump the new one.

I don't understand why on earth they are trying to upgrade people to a BETA anything which is widely reported to be causing trouble.

are you out of your mind? :) ff2 took twice as much memory on my machine then ff3b5 does... ff3b5 is also much more responsive and is in any way a great improvement... the memory leaks i had in ff2 are gone... everything is super... 

btw hardy is a LTS which means it is going to be supported for a long time... how do you think this will happen when mozilla is about to drop ff2 support after ff3 is launched in september?

decisions to include beta software in a release are always taken with full analysis and research... don't think this was done just to piss you off

btw, does this anomaly with full screen happen with or without compiz? i have all upgrades (from main servers) and i don't see anything like this

---

### Post by takuhii on 2008-05-19
I'm more than willing to put up worth some of the issues in Firefox 3B5 at the moment, the memory footprint is so much smaller!!

---

