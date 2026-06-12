---
title: "Where is vnc.so - what package has it?"
date: 2005-01-19
forum: Repositories &amp; Backports
---

### Post by chaumurky on 2005-01-19
Hello everyone. This is my first Ubuntu post! So, down to business...  :D I want to load the vnc.so module using the method described at [http://www.realvnc.com/v4/x0.html](http://www.realvnc.com/v4/x0.html). I have the 'tightvncserver' package installed along with 'vnc-common' and even 'libvncserver-dev' but I can't find vnc.so on my system. It worked very well for me in Mandrake and was nice and fast. Can someone tell me if there's a deb package that contains this file? Thank you.

---

### Post by mendicant on 2005-01-19
You can look into x11vnc.  It doesn't actually have vnc.so, though.  That's in vnc4server, which is only in hoary.

---

### Post by chaumurky on 2005-01-19
Is it faster than vino? Gnome Remote Desktop is so laggy I have to use -dotcursor so my mouse arm doesn't feel like it's moving through molasses... :lol:

---

### Post by mendicant on 2005-01-20
Having never used vino, I couldn't tell you.  I also usually don't export my current desktop over VNC.  If you really want vnc.so, you could just grab it from hoary.  The dependencies of vnc4server look pretty straightforward, so it doesn't look like you'd be pulling in anything terribly unstable, but use aptitude to make sure.

---

### Post by milli on 2005-10-25
vnc.so is in the vnc4server package as of this writing.

I can tell you that the new vnc 4.x X server extension is a LOT faster than Vino.  It also has the distinct advantage that it works even if X is sitting on a greeter screen (i.e., gdm).  I have several servers that I previously had to set a timed auto-login just so vino-server would start.  I don't have to do that now.

You do have to use xvnc4viewer though to take advantage.

For Breezy, I did this:

On both client and server side:
[LIST]
[*]Uncommented the 'universe' line in /etc/apt/sources.list
[*]Ran **apt-get update**
[/LIST]
On the server side:
[LIST]
[*]Ran **apt-get install vnc4-common vnc4server**
[*]cd /usr/X11R6/lib/modules/extensions
[*]mv vnc.so libvnc.a
[*]Modified /etc/X11/xorg.conf to have 'Load "vnc"' in the Module section and 'Option "SecurityTypes" "None"' in the Screen section
[*]Killed and restarted the X server (**/etc/init.d/gdm restart** from a console, for example, or just Ctrl-Alt-Backspace inside of X)
[*]Checked /var/log/Xorg.0.log to make sure the vnc extension loaded after X restarted
[/LIST]
On the client side:
[LIST]
[*]Ran **apt-get install vnc4-common xvnc4viewer**
[*]Ran **xvnc4viewer *hostname***  (replace *hostname* with your server's name, of course)
[/LIST]
You can also, optionally, run **vnc4config** on the server side to enable clipboard support... very handy!

---

### Post by chaumurky on 2005-10-25
Ha! You dredged up my first post! I never got to doing that after all as I settled with x11vnc loading with GDM. I'll have to try it again!

---

### Post by chaumurky on 2005-10-25
I added:
 
```
 
Option "rfbAuth" "/home/<username>/.vnc/passwd"

```
 
In the "screen" section. Works well. :KS

---

