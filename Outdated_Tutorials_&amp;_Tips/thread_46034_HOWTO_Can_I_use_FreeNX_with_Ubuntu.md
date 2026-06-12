---
title: "HOWTO: Can I use FreeNX with Ubuntu?"
date: 2005-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Ozitraveller on 2005-07-02
I thought someone might interested in this HOWTO!

I installed FreeNX and the windows NXClient quite easily. In fact I'm I'm logged on now, typing this! Nice and speedy too! Now I want to got the extra step and secure it all and add OpenVPN.

[http://www.ubuntuforums.org/showthread.php?t=1968&highlight=freenx](http://www.ubuntuforums.org/showthread.php?t=1968&highlight=freenx)

One thing that is a bit irrating is the default size and choice of fonts. And the desktop button and trash can icons are just red X place holders. And the launchers on the menubar are a little displaced, which is probably something to do with the fonts.

But otherwise excellent!!!

---

### Post by XDevHald on 2005-07-02
[QUOTE=Ozitraveller]I thought someone might interested in this HOWTO!

I installed FreeNX and the windows NXClient quite easily. In fact I'm I'm logged on now, typing this! Nice and speedy too! Now I want to got the extra step and secure it all and add OpenVPN.

[http://www.ubuntuforums.org/showthread.php?t=1968&highlight=freenx](http://www.ubuntuforums.org/showthread.php?t=1968&highlight=freenx)

One thing that is a bit irrating is the default size and choice of fonts. And the desktop button and trash can icons are just red X place holders. And the launchers on the menubar are a little displaced, which is probably something to do with the fonts.

But otherwise excellent!!![/QUOTE]
 Awesome! been looking for this :D

---

### Post by intangible on 2005-07-04
I've noticed if you already have a session logged in on the computer (like locally) and then you log on to the same user account with nx, you'll see the missing icons.  Log out the other session first, then try it.

---

### Post by Ozitraveller on 2005-07-04
[QUOTE=intangible]I've noticed if you already have a session logged in on the computer (like locally) and then you log on to the same user account with nx, you'll see the missing icons.  Log out the other session first, then try it.[/QUOTE]


Thanks intangible. It's very curious though, because all the other icons seem to be there? Maybe it doesn't pickup up the theme properly?

---

### Post by chaumurky on 2005-07-04
Is there any equivalent to x2vnc for freenx? At the moment using x2vnc causes my vnc server's cpu to go crazy.

---

### Post by chaumurky on 2005-07-05
:EDIT

---

### Post by intangible on 2005-07-05
vino-server is built in Ubuntu (System->Preferences->Remote Desktop), or x11vnc works real well for me.  I don't use it with freenx, but you should be able to.

Any specific reason why you want to use VNC instead of just X?

---

### Post by chaumurky on 2005-07-06
[QUOTE=intangible]vino-server is built in Ubuntu (System->Preferences->Remote Desktop), or x11vnc works real well for me.  I don't use it with freenx, but you should be able to.

Any specific reason why you want to use VNC instead of just X?[/QUOTE]
 My 2 PC's have their own monitor side by side but I'm sharing my mouse and keyboard between 2 PC's with x2vnc (befor I moved to Ubuntu I ised win2vnc on XP). It's the only reason I have desktop sharing turned on. The trouble is, even though x2vnc doesn't actually show the shared desktop, it appears to poll the whole desktop a like a vnc viewer - hence the high cpu. Anyway, I asked that question before realizing that freenx doesn't share the desktop so it's not really relevent now. I think x2x or synergy may be what I'm looking for if I can work out how to use it...

---

### Post by ubuntonista on 2005-09-12
The guide at the wiki has been updated recently to show how to change the sshd port, and also to cover installation of the client on Ubuntu systems:
[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

Thanks, everyone.

---

