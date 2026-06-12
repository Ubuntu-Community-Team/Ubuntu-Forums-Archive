---
title: "function keys not working"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by aneez004 on 2013-04-08
[FONT=Verdana][COLOR=#dfe9f1]
[/COLOR][/FONT]Hi,

I installed Ubuntu 12.10 in my Toshiba  Satellite L755 laptop (6 GB RAM, 2.3 GHz, core i5, nvidia graphics card). 

No function keys are working. So I can't do things like reducing display brightness and other functions which I could do in windows7. I tried to reduce display brightness from system settings, but met with no success.

I also tried Zorin 6.2 in live mode but got the same result. Please suggest solutions to activate function keys or alternatively other ways to perform the required functions like reducing display brightness.

Regards,
Anees

---

### Post by BrunoLotse on 2013-04-08
On my Sony Vaio gnome-shell I am using this brightness control
[https://extensions.gnome.org/extension/231/brightness-control/](https://extensions.gnome.org/extension/231/brightness-control/)
Worsk lika a charm.
Cheers,
Bruno

---

### Post by aneez004 on 2013-04-08
> **BrunoLotse said:**
> On my Sony Vaio gnome-shell I am using this brightness control
[https://extensions.gnome.org/extension/231/brightness-control/](https://extensions.gnome.org/extension/231/brightness-control/)
Worsk lika a charm.
Cheers,
Bruno

Thanks for the response. Let me try that..

But Ubuntu 12.10 use Unity, not gnome3 right? So will it work?

Regards,
Anees

---

### Post by BrunoLotse on 2013-04-08
I am using gnome-shell. If it's not working on Unitiy just remove it.
No harm done. Just try it.
Cheers,
Bruno

---

### Post by aneez004 on 2013-04-09
Let me try

---

### Post by aneez004 on 2013-04-16
Hi, 

The brightness issue is solved. Adding some contents to /etc/X11/xorg.conf solved the issue. 
Got it from here: [http://askubuntu.com/questions/154948/unable-to-change-brightness-on-a-toshiba-l750](http://askubuntu.com/questions/154948/unable-to-change-brightness-on-a-toshiba-l750)

Need to find a way to integrate brightness control and other functions to function keys.

Thanks, Anees

---

