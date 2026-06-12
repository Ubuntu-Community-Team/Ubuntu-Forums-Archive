---
title: "python wxWidgets application problem"
date: 2013-03-20
forum: Programming Talk
---

### Post by peredur on 2013-03-20
I'm trying to run the text editor example application from:

[http://wiki.wxpython.org/Getting%20Started]("http://wiki.wxpython.org/Getting%20Started")

(Specifically the first example with a menu attached)

Ubuntu 12.04, Python 2.7

Having pasted the code into IDLE, saved the file and then run the application from within IDLE, the frame appears, but the menu does not.  The application does not run at all outside of IDLE.

Any suggestions greatly appreciated.

Best regards


PAE

---

### Post by peredur on 2013-03-21
Well, I sorted two out of the three problems.  Both were the results of my own stupidity.

The  menu doesn't show because it's the Unity interface and so the menu doesn't appear in the application window but rather at the top of the desktop.  I really should have thought of that earlier but tiredness took its toll, I'm afraid.

The application didn't run from the command line because I'd omitted the shebang line.  Again, it must be tiredness that's to blame for that.

But I still have the problem of not being able to re-run the application in IDLE.  If anyone does know why that should be the case I'd be glad to hear it, but it sounds like an IDLE problem, so I'll look for an IDLE forum and post there.

Many thanks


PAE

---

### Post by peredur on 2013-03-21
Continuing this conversation I'm having with myself - for which I apologise...

The way the IDLE process is started is responsible for the fact that I can't run programs twice in the same shell in IDLE.  Apparently the launcher starts IDLE using the -n option which has this undesirable side effect.  Starting IDLE from the command line without the -n option fixes the problem, but is annoying.

Does anyone know how to make the Unity launcher start IDLE 'properly' (i.e. without the -n option)?

Cheers


PAE

---

### Post by r-senior on 2013-03-22
You could edit the .desktop file. The usual way is to copy it from /usr/share/applications to ~/.local/share/applications and edit your local copy which takes precedence over the global one. Look for the Exec line. I'm assuming it would be idle.desktop.

---

### Post by peredur on 2013-03-22
Many thanks.  Yep.  That did it.  Although, actually, I had achieved it in a roundabout way before getting your reply.

Having failed to find out how to change the command in Unity, I started an LXDE session and did it there - where all you have to do is right-clickk on the menu item.  Back in Unity, the change persisted, so  job done.  But your way would have been better, had I known about it.

Pretty much all the main Linux desktops that are GNOME or KDE-based seem to be moving in the direction of making trivial changes like these hard to do, it appears to me.  I think that's a mistake.

Thanks for your help.

---

### Post by r-senior on 2013-03-22
I agree that it's probably harder than it should be. For reference, here are the docs that describe the process using the editor method and alacarte (which is what I suspect your LXDE session did):

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by peredur on 2013-03-22
Thanks.  Much appreciated.

---

