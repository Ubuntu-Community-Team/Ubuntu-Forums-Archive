---
title: "Gnome 3 Shell on Alpha 3"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jeykon on 2011-08-05
Is their any way to get gnome 3 Shell running on alpha 3?

Formerly i've upgraded from 11.04 to 11.10 alpha 2. Then i've installed gnome 3 shell via package.
Both, unity and gnome 3 did their work.

After i've upgraded to alpha3 yesterday both environments were damaged. Their have been only the Nautilus panel and the desktop icons, but nothing more.

So i tried to remove gnome3 shell and reinstalled unity. No result.

Now i have installed a fresh downloaded 11.10 iso. I don't want to destroy my system again. 

So my question. Is their any way to geht both, unity and gnome3 shell running?


PS: Why no gnome3 shell in ubuntu? Unity still looks like a netbook environment. I don't like the look and feel of it. For me its ugly. I want to use it without shortcuts. Since years gnome is a part of my favourite system. Please simply integrate it. It Couldn't be so difficult. Let the user make his own choice.

Sorry for my english :D

---

### Post by Harry33 on 2011-08-05
> **jeykon said:**
> Is their any way to get gnome 3 Shell running on alpha 3?

Formerly i've upgraded from 11.04 to 11.10 alpha 2. Then i've installed gnome 3 shell via package.
Both, unity and gnome 3 did their work.

After i've upgraded to alpha3 yesterday both environments were damaged. Their have been only the Nautilus panel and the desktop icons, but nothing more.

So i tried to remove gnome3 shell and reinstalled unity. No result.

Now i have installed a fresh downloaded 11.10 iso. I don't want to destroy my system again. 

So my question. Is their any way to geht both, unity and gnome3 shell running?


PS: Why no gnome3 shell in ubuntu? Unity still looks like a netbook environment. I don't like the look and feel of it. For me its ugly. I want to use it without shortcuts. Since years gnome is a part of my favourite system. Please simply integrate it. It Couldn't be so difficult. Let the user make his own choice.

Sorry for my english :D

I have completely uninstalled Unity and installed gnome-shell.
It works very well and i do have fully updated setup.

---

### Post by jeykon on 2011-08-05
I Tried the bug workaround and downgraded to gnome session from ending 7 to 6.
The shell is working now, but im afraid of testing unity again. Please tell me that everythings gonna be ok :)

---

### Post by cariboo on 2011-08-05
Everything isn't going to be OK :) this is still alpha software, and breakage could happen at any time. Hopefully you still have a stable version installed, in case breakage makes your system unusable.

---

### Post by jerrylamos on 2011-08-05
> **cariboo907 said:**
> Everything isn't going to be OK :) this is still alpha software, and breakage could happen at any time. Hopefully you still have a stable version installed, in case breakage makes your system unusable.
Yes, I've got Ocelot Alpha 2, Narwhal, Meerkat, Lynx, and for that matter Tiny Core all running fine.

Alpha 3 no desktop.  lightdm says it's running but must be on some virtual invisible console.

If I do a startx, gdm does start up with a window that says gnome not found, only option is Logout which works.  This proves X will work but not lightdm.  Back to the command line.

I've tried sudo apt-get install openbox and lxde but apt-get can't find either one even though they are listed in Synaptic on Narwhal.

Jerry

---

### Post by jerrylamos on 2011-08-05
Booted again, no desktop as usual for Alpha 3.

Alpha 3 Live sources.list only about 4 lines long.  Copied in sources.list from Alpha 2, did apt-get update, apt-get install lightdm.

It ran!  Desktop, launch bar, everything except:

Mouse didn't move.  

Let me look at the forum for mouse problems...

Jerry

---

### Post by jerrylamos on 2011-08-05
> **jerrylamos said:**
> Booted again, no desktop as usual for Alpha 3.

Alpha 3 Live sources.list only about 4 lines long.  Copied in sources.list from Alpha 2, did apt-get update, apt-get install lightdm.

It ran!  Desktop, launch bar, everything except:

Mouse didn't move.  

Let me look at the forum for mouse problems...

Jerry

Switched from PS2 mouse to USB mouse, now works.  Now how to do an ubuntu-bug with crippled Alpha 3.

Jerry

---

### Post by cariboo on 2011-08-05
> **jerrylamos said:**
> Switched from PS2 mouse to USB mouse, now works.  Now how to do an ubuntu-bug with crippled Alpha 3.

Jerry

You use elinks like ranch hand suggested in the other thread.

---

### Post by Harry33 on 2011-08-06
> **jeykon said:**
> I Tried the bug workaround and downgraded to gnome session from ending 7 to 6.
The shell is working now, but im afraid of testing unity again. Please tell me that everythings gonna be ok :)

The gnome-session bug (#821477) has been fixed by the newest update of
gnome-session (3.1.3-0ubuntu8 )

---

