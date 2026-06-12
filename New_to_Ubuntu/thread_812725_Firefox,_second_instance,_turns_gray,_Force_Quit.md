---
title: "Firefox, second instance, turns gray, Force Quit"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cwmoser on 2008-05-30
I am running Gutsy Ubuntu, Firefox 2.

When I open a second browser window, Firefox turns gray in color.
When I click on the "X" to kill the window, I get a Force Quit message.

Why is Firefox crashing?

Thanks

Carl

---

### Post by muteXe on 2008-05-30
This happens to me as well.  I'm running Hardy.

---

### Post by enoughsaid05 on 2008-05-30
Probably due to flash or something? If it is flash then open up the terminal and type in

killall npviewer.bin

might save you the trouble of having to restart firefox.

Or probably due to some graphics? Probably you might have compiz turned on. My laptop spec is not good enough for compiz and it keeps crashing the system, so I turned compiz off and everything turns fine.

---

### Post by muteXe on 2008-05-30
Cheers.  For me it is probably flash yeah. is this a known bug then in FF then?
mute

---

### Post by skymera on 2008-05-30
Do you mean when you view Flash it freezes?

Here's a nice tasty solution:
[http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)

I'm using swfdec rather than Adobe Flash aswell, i haven't froze on any Flash sites.

---

