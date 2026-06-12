---
title: "Systray balloon message?"
date: 2008-03-09
forum: Programming Talk
---

### Post by Cenoforums on 2008-03-09
hi,

I'm programming a modem dial-up application using php-gtk, and I want to do the following.
When an internet connection is established, a "balloon" pops up in the system tray (or notification area, whatever you wanna call it) saying just that. I saw ubuntu's update manager using  this, I'm sure you know what I'm talking about.

I have no idea how to implement this, is there a specific gtk class? or is it just an image?

any input would be appreciated, even if it's in C or python, doesn't have to be in php

thx in advance,
jorge azevedo

---

### Post by imdano on 2008-03-09
You probably want [libnotify](http://www.galago-project.org/news/index.php).  I know there are Python bindings for it (that's what the update manager uses), not sure of a way to use PHP.

---

### Post by Can+~ on 2008-03-09
pynotify

I found another post about that:
[http://ubuntuforums.org/showthread.php?t=447613](http://ubuntuforums.org/showthread.php?t=447613)

---

### Post by tgalati4 on 2008-03-09
Give zenity a spin:

[http://ubuntuforums.org/showthread.php?t=328766&highlight=zenity+uptime](http://ubuntuforums.org/showthread.php?t=328766&highlight=zenity+uptime)

---

### Post by Cenoforums on 2008-03-10
thx for the fast replys, the zenity thing doesn't seem to be what I'm looking for. I think it only does a tooltip, a message that appears when you leave the mouse over the icon? I read it in a hurry, maybe I got it wrong.

I'll check out the python stuff as soon as I get some time in my hands, got an exam in 4hoursO_O

---

### Post by _duncan_ on 2008-03-10
A fellow ubuntu user (gborzi) is already doing the same thing, but using python. Maybe the 2 of you can just collaborate on the project? Anyway, this link might interest you.

[http://ubuntuforums.org/showthread.php?t=534709]("http://ubuntuforums.org/showthread.php?t=534709")

---

### Post by Cenoforums on 2008-03-10
thx duncan, that was actually quite helpfull, I was doing some pretty **** programming, got me some insight on this whole pppd thing.

Well, after some research I confirmed that you need libnotify to do notifications to the systray. If you install it you can try it out by entering in the terminal "notify-send test".
Python has a binding, php-gtk does not. I talked to one of the dev's and that's what I implicitly understood.

Which sucks. At first I thought "no big deal" because my program is basically a GUI to run wvdial with a click and it has a "terminal" built into it.
But running notify-send raises some problems, and I'm guessing it's because of the mess of pipes envolved in the process. The code I have is messy all by itself, stderr does not appear to work, adding libnotify and Dbus signals was way too much.

*sigh* there goes absolute user friendly, I don't see how I can make this work .
I should've chosen python, damn.

Any more insight on this topic is appreciated, if any of you has any idea.

Oh, I forgot about something. Isn't it strange that the update manager was making notifications with me having to install libnotify? Or did I just updated it? can't quite remember...

---

### Post by mssever on 2008-03-10
Why can't you use exec() or one of its friends to call notify-send? Since there's a CLI interface, theoretically any language can use it, bindings or not.

---

### Post by Cenoforums on 2008-03-11
lol yeah, good idea. Should've thought about it myself, god I'm really new at this.

same thing, I get:

libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Any idea why this is happening?

---

### Post by mssever on 2008-03-12
> **Cenoforums said:**
> same thing, I get:

libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Any idea why this is happening?

Are you trying to run as root? It appears that if you're running as a different user, you'll have to figure out how to hook into the proper session (DBUS, maybe?). I don't know how to do that. It might be helpful to read the spec mentioned in the notify-send man page.

It might also be helpful to look at the source code of other programs that use libnotify and run as root to see how they handle things.

Of course, it doesn't help that you're using PHP. :)

---

