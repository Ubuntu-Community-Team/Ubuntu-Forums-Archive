---
title: "[Python] How would one go about creating a GDE"
date: 2011-08-11
forum: Programming Talk
---

### Post by ki4jgt on 2011-08-11
How would one go about creating a Graphical Desktop Environment in Python?

---

### Post by papibe on 2011-08-11
Do you mean how to create a desktop (graphical) application? If so, take a look at these [screencasts]("http://www.omgubuntu.co.uk/2011/06/gnome-screencasts-taking-tutorials-to-the-next-level/"). 

Hope it helps,
Regards.

---

### Post by DangerOnTheRanger on 2011-08-11
Well, there's no straight-forward answer to your question. A desktop environment (DE) is nothing more than a collection of applications and applets, plus a window manager. For a more direct answer to your question:

[LIST]
[*]Find or create a window manager - look at the python-plwm package in the repos for a window manager library written in Python
[*]Create or reuse various applications that make the "actual" DE. This would be things like panels, configuration programs, a file manager, and other stuff.
[/LIST]
One really good resource for DEs is [http://freedesktop.org]("http://freedesktop.org/") - the organization that controls various standards for the Linux desktop (say, DBus).

---

### Post by ki4jgt on 2011-08-11
I actually read a page on it about a year ago. That's why I'm asking. None of the current systems will work for me though. I have a portable device. I'm getting tired of running the terminal from it (curses, but still the terminal) I'm wanting something a little more graphical. Something to the effect of Moblin (forgot what is't current name is)

---

### Post by papibe on 2011-08-11
Are you talking about Tiling Windows Managers?

Here's a few:
[LIST]
[*][xmonad]("http://xmonad.org/")
[*][awesome]("http://awesome.naquadah.org/")
[*][scrotwm]("https://opensource.conformal.com/wiki/scrotwm")
[*][dwm]("http://dwm.suckless.org/")
[/LIST]
Regards.

---

### Post by ki4jgt on 2011-08-11
> **papibe said:**
> Are you talking about Tiling Windows Managers?

Here's a few:
[LIST]
[*][xmonad]("http://xmonad.org/")
[*][awesome]("http://awesome.naquadah.org/")
[*][scrotwm]("https://opensource.conformal.com/wiki/scrotwm")
[*][dwm]("http://dwm.suckless.org/")
[/LIST]
Regards.

Talking about replacing Gnome, KDE, Unity and any others with my own.

---

### Post by papibe on 2011-08-11
> **ki4jgt said:**
> Talking about replacing Gnome, KDE, Unity and any others with my own.
I apologize for my confusion. Let's start again.
> **ki4jgt said:**
> How would one go about creating a Graphical Desktop Environment in Python?
I would start reviewing the code of the existing ones:
[LIST]
[*][Qtile]("http://qtile.org/")
[*][PyWM]("http://pywm.sourceforge.net/")
[*][samurai-x]("http://code.google.com/p/samurai-x/")
[/LIST]
Kind Regards.

---

### Post by cgroza on 2011-08-11
> **ki4jgt said:**
> Talking about replacing Gnome, KDE, Unity and any others with my own.
Than all you have to do is organize a collection of your python apps that will form your DE and then make a package that depends on them all. Ubuntu-desktop is a similar package.

You may have to write some parts that are not available in python if you insist on it being 100% python.

---

### Post by ki4jgt on 2011-08-12
> **cgroza said:**
> Than all you have to do is organize a collection of your python apps that will form your DE and then make a package that depends on them all. Ubuntu-desktop is a similar package.

You may have to write some parts that are not available in python if you insist on it being 100% python.

Well, wanted to hack the Zipit Z2. The only GUIs available are mainly based on curses or are deprecated. Any other DE would fizzle on such small screen. There was an Ubuntu release made for it, but as I said, it was deprecated :-( I'm just tired of terminal based access. I want something a little more modern. I mean, old time cellphones didn't even have terminal based OSs. Don't get me wrong, I love terminal, but more in a desktop setting. Unfortunately, all I know is Python. So, unless there is a language I can learn quite quickly, I'll have to go with it for the time being. The major problem I have with the current OS that most people use is it's terminal based of course. None of the applications work. The Applications aren't integrated into the desktop. I want to make an online app store for the device, like iOS. The device sells for $15, brand new online, so you can see where I'm going with this. Cheap tablets for everyone. It even has a built in headphone jack and doesn't play flash, just like iOS.

---

