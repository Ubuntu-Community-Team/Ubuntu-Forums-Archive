---
title: "Website Content in Terminal???"
date: 2018-08-12
forum: New to Ubuntu
---

### Post by mborl on 2018-08-12
Something interesting has occurred. I was playing in the terminal (as Linux users are wont to do) when the output of some of my commands started displaying some of the text from the webpage that was open in a window of Google Chrome. I think I was using ```
apt show [PACKAGE]
``` when this occurred. Yes, the output of apt show, displayed what you would expect, _plus _some text from the webpage open on Google Chrome. 

I checked my clipboard, and the content was not the same as the text that magically appeared in my terminal. 

This has occurred twice. I have used clamscan to check my device for infections, but it turns up negative. The "sketchy-est" things that I have downloaded are just gnome-tweaks (which everybody downloads), the gnome-shell-extensions package, and a couple gnome and icon themes (all of which from the Universe repo). Thoughts? 

P.S. I post this because security is really important to me.

---

### Post by TheFu on 2018-08-13
If a terminal gets marked as the _system console_, then all  stdout and stderr from running programs will show up there.  You can also see this by starting GUI applications from a terminal. It is a common troubleshooting technique.

If you'd like to use a text-only web browser, there is **lynx**.  It is fast, because it completely ignores images and media parts of websites. It also ignores javascript, which can really slow down websites.  If you want to save web pages locally, you can use **curl**. Sometimes it is handy to run a webpage through a few filters to get readable text or pdf versions of websites.

If you use pre-configured repositories from Canonical and stay patches, the risks of any virus or malware is pretty low. If you are paranoid,like me, you can take extra steps to prevent nasty things from the web.

---

### Post by Impavidus on 2018-08-13
You checked the clipboard, but do you realise there are two clipboards in Linux? The other works by select, then past with the middle mouse button. So if by accident you clicked the middle mouse button, the last selected text would get pasted in the terminal or wherever the mouse was.

---

### Post by TheFu on 2018-08-13
> **Impavidus said:**
> You checked the clipboard, but do you realise there are two clipboards in Linux? The other works by select, then past with the middle mouse button. So if by accident you clicked the middle mouse button, the last selected text would get pasted in the terminal or wherever the mouse was.

Excellent point!  The X-buffer gets loaded by selecting alone.  This is built-into X/Windows.  I use the x-buffer for select-paste things as part of my normal workflow. Much faster than other methods, provided you know about it.

---

### Post by mborl on 2018-08-17
Great stuff! Always learning

---

