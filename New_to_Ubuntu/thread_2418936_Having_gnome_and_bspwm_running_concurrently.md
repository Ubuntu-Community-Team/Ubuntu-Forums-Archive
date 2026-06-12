---
title: "Having gnome and bspwm running concurrently"
date: 2019-05-14
forum: New to Ubuntu
---

### Post by djedefre on 2019-05-14
I just installed ubuntu 18.04 and wanted to try out bspwm window manager.
I followed [this]("https://github.com/windelicato/dotfiles/wiki/bspwm-for-dummies") tutorial doing the "with display manager" path.
At the end of this, it tells you to restart your current display manager. 
I executed "sudo service gdm restart" and then everything just starts flickering between the normal desktop and the "gnome text log". 
(I don't know how you properly call it. I mean the command line where most lines start with [OK])
Moreover, the OS doesn't react to any mouse/keyboard input.

After that, I restarted logged into my account on gnome switched to tty3 and tried to start bspwm through "startx". 
However here I just get a black window and nothing happens. It also doesn't react to the keybindings set in sxhkd (Though I know that sxhkd works as it reacts to the keybinds in gnome).

Lastly, I restarted once again and then on the login screen found the small cog where one can select between bspwm, Ubuntu, and Ubuntu with Wayland. 
I selected bspwm logged in and it worked.

Though now I was wondering if it is possible to have bspwm running on e.g. tty2 and gnome on tty3 at the same time?
Therefore I tried selecting bspwm on the login screen, logging in, switching to tty3 and executing "sudo service gdm restart" there. 
However, this resulted in the same flickering as described above though now between "Linux text console" and the "gnome text log" and turned bspwm into a black screen.

Can someone help and/or explain why and what the problems are?

---

### Post by dino99 on 2019-05-14
possible solution: [https://superuser.com/questions/1345392/bspwm-not-working-on-ubuntu](https://superuser.com/questions/1345392/bspwm-not-working-on-ubuntu)

---

### Post by djedefre on 2019-05-14
I've already applied these settings so that wasn't the problem I guess.

---

### Post by cruzer001 on 2019-05-15
So this is where your at?
> **Logging into your new bspwm session**
Now for the moment of truth. Type startx in your tty. If all went according to plan, you should be presented with a blank screen. That's good. Open up your preferred terminal using whatever key combination / terminal name you chose in your .config/sxhkdrc. If nothing happens, start trouble shooting.

Maybe better off using Ubuntu repositories.

[https://packages.ubuntu.com/eoan/bspwm](https://packages.ubuntu.com/eoan/bspwm)

You are running xorg or wayland xorg?

---

### Post by djedefre on 2019-05-17
If restarting the PC has the same effect as restarting gnome then yes that's where I'm at.

How would I setup bspwm if I use the repository and how is it going to work with sxhkd then?

"echo $XDG_SESSION_TYPE" returns x11 so I guess I'm running xorg.

---

### Post by djedefre on 2019-05-17
After removing all packages related to bspwm and all the config and installing it through the Ubuntu repository it finally worked properly, Thanks cruzer001!

---

### Post by cruzer001 on 2019-05-17
Excellent :)

On a side note..
I like to row my own too. I have found that doing a console only install then adding my starter packages makes a nice platform to build on.  For a gnome3 environment I usually use the gnome-core package, it works out of the box, has gdm3 installed and nicely featured for a core build.

[https://packages.ubuntu.com/eoan/gnome-core](https://packages.ubuntu.com/eoan/gnome-core)

):P

---

