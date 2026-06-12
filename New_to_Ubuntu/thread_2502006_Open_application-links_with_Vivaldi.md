---
title: "Open application-links with Vivaldi"
date: 2024-10-29
forum: New to Ubuntu
---

### Post by jordan83 on 2024-10-29
Hello,

I recently came back to Ubuntu after many years.
My favorite browser is Vivaldi and I'm encountering an issue.

Sometimes a program needs to use the browser for logging in and then it should come back with the authentication completed. F.e. when logging in the "Online accounts" in Gnome.
Other times a link should open a specific application in Gnome, f.e. a Gnome extension from the extensions website or a magnet link to download a torrent.

In all these cases Vivaldi prompts me to open "xdg-open", however if I click it nothing happens.
If I do the same operations via Firefox, everything works.

How do I get Vivaldi to work like Firefox for these things?

Thank you!

---

### Post by grahammechanical on 2024-10-29
The X in xdg-open stands for X-server. X-Desktop-Group = xdg.

The X-Server was used on Linux systems as a display server. Ubuntu now uses something called Wayland. That is the reason that xdg-open does not work. Ubuntu is not running on the X-Server. We can switch to X.org and back to Wayland at the login screen.

But you might be successful if you research Vivaldi to see if it, like Firefox, can perform the same functions on Wayland. What do you see in the Vivaldi settings?

Oh, by the way, Wayland is here to stay. As they say: "It the future."

Regards

---

### Post by tea for one on 2024-10-29
Yes, indeed, Wayland is the future
However, even in a Wayland session, open a terminal and enter (ignore the permission denied message):-
```
xdg-open https://ubuntu.com
```
It works for me in a Wayland session, but should it?

---

### Post by grahammechanical on 2024-10-29
@jordan83

Is your install of Vivaldi a deb packaged version or a snap packaged version. I ask this because [@TheFu please look away now :)] I think that xdg-open is now a snap package on Ubuntu. Is Vivaldi set as the default browser in System Settings>Apps

[https://www.ubuntuupdates.org/package/core/noble/universe/updates/snapd-xdg-open](https://www.ubuntuupdates.org/package/core/noble/universe/updates/snapd-xdg-open)

@tea for one  does that command work with Vivaldi as the default browser?

---

### Post by tea for one on 2024-10-29
> **grahammechanical said:**
> @tea for one  does that command work with Vivaldi as the default browser?
I haven't installed Vivaldi because Firefox is more than adequate for my needs.
Therefore I cannot confirm one way or the other.
However, I reckon the command will defer to the user's default browser in the browser preferences.
Also, you are not limited to websites.
Files can be opened also - try it with a pdf located somewhere in your user directory.
```
xdg-open ~/Downloads/issue210_en.pdf # Full Circle Magazine edition 
```
> xdg-open - opens a file or URL in the user's preferred application
The command is not part of a snap package, more info here [https://manpages.ubuntu.com/manpages/noble/man1/xdg-open.1.html](https://manpages.ubuntu.com/manpages/noble/man1/xdg-open.1.html)

---

### Post by jordan83 on 2024-10-29
@grahammechanical it is installed as a snap app.
Vivaldi is set as default browser.

---

