---
title: "X2go Client from Mac to Ubuntu 18.04 Desktop"
date: 2019-05-13
forum: New to Ubuntu
---

### Post by littleno255 on 2019-05-13
I wanted to remote control the Ubuntu 18.04 Desktop from my Mac and found this thread recommending X2go over SSH for this purpose: [https://ubuntuforums.org/showthread.php?t=2388248](https://ubuntuforums.org/showthread.php?t=2388248)

I successfully installed the X2go client on my mac, setup the server side on the ubuntu machine, created ssh-keys on the mac and successfully can control the Ubuntu desktop (using the existing Desktop setting in X2go client). However, that only works when a user is already logged in. In case no user had been logged in locally on the Ubuntu-machine the X2go client says "no remote desktop found". Since this is the normal case this doesn't help me.

So is there a way to get the remote session running even when no user is logged in locally on the Ubuntu machine?

---

### Post by TheFu on 2019-05-13
I don't use a Mac, but I use x2go, daily, constantly, on systems that are remote without **any** userids logged in. I don't have 18.04. We are on 16.04 here.

A few questions.

Does ssh work from the Mac to the Linux system?

Which DE are you using?  It is best NOT to use Gnome3. Stick with Mate, LXDE or XFCE.

Is there any encryption involved in the Linux system?

Does the Mac version require downloading a font package?  I know Windows does, but Ubuntu-to-Ubuntu clients do not.

What do the log files show on the Ubuntu machine?  Post only the relevant parts, with code tags, please.

---

### Post by littleno255 on 2019-05-13
> [COLOR=#000000]Does ssh work from the Mac to the Linux system?[/COLOR]
yes

> [COLOR=#000000]Which DE are you using? It is best NOT to use Gnome3. Stick with Mate, LXDE or XFCE.[/COLOR]
the Ubuntu (I think thats Gnome?) Desktop. But thats what I want, I need the same look and feel on the remote session as on the physical machine. And except for my login-issue it's working really nice thru X2go.

> [COLOR=#000000]Is there any encryption involved in the Linux system?[/COLOR]
you mean file system encryption? no

> [COLOR=#000000]Does the Mac version require downloading a font package? I know Windows does, but Ubuntu-to-Ubuntu clients do not.[/COLOR]
how do I find out?

> [COLOR=#000000]What do the log files show on the Ubuntu machine? Post only the relevant parts, with code tags, please.[/COLOR]
what logfiles to check?

---

### Post by TheFu on 2019-05-14
> Newer versions of the GNOME 3 and UNITY desktop environments have compatibility issues with X2Go. See the page Desktop Environment Compatibility for more details. 
[https://wiki.x2go.org/doku.php/doc:usage:x2goclient](https://wiki.x2go.org/doku.php/doc:usage:x2goclient)

[https://wiki.x2go.org/doku.php/doc:de-compat](https://wiki.x2go.org/doku.php/doc:de-compat) says:
> We might be able to support Gnome 3.14, especially for RHEL7/EPEL7, given enough $$$ and round tuits ([https://en.wiktionary.org/wiki/round_tuit](https://en.wiktionary.org/wiki/round_tuit)), but support for newer versions seems doubtful, due to certain design decisions made by the Gnome developers. 

Best not to ignore these warnings.

Mac specific information would be on the x2go site.

Check all the log files.  Use egrep.

---

