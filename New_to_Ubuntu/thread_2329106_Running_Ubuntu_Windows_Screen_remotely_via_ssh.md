---
title: "Running Ubuntu Windows Screen remotely via ssh"
date: 2016-06-28
forum: New to Ubuntu
---

### Post by adrian33 on 2016-06-28
[COLOR=#000000]I am able to ssh into my home computer remotely (A windows machine running cygwin X-Server). I am also able to run many GUIs (Spyder for Python, Nautilus, gedit, etc). What I am unable to figure out is how to create the Ubuntu desktop GUI so that I can load programs using icons instead of having to use the terminal. [/COLOR]

[COLOR=#000000]After reading through MANY threads, I still have not come across a solution that worked. I've ran updates, upgrades, and sudo apt-get ubuntu-desktop. According to many suggestions, I should be able to just type startx in my xterm and the desktop GUI should appear. It does not. Some say that I should switch to gdm and then type gnome-session. That did not work. (although gnome-panel did) Some said that it had to do with my Nvidia card, so I purged that and am now using a generic driver. It still does not work. I tried using lightdm without success.[/COLOR]

[COLOR=#000000]What am I missing? I'm using version 14.04[/COLOR]

[COLOR=#000000]Thanks,[/COLOR]
[COLOR=#000000]Adrian[/COLOR]

---

### Post by adrian33 on 2016-06-28
Here is a reply I received from another source:

If you would like to maintain your desktop environment, then I think the best thing to do would be VNC:

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04)



VNC is like X11 forwarding, only the *entire* desktop environment is displayed on your screen.

It looks like I will also need to use a client that supports VNC connections over SSH tunnels such as:  TightVNC, RealVNC, or UltraVNC.

I will try this later this evening and report my findings.


UPDATE:  I read up on VNC and I don't think that is what I'm looking for. For one, I would like to avoid loading another program on my Windows machine if I do not need to. Two, it has a "show my desktop" feel.  My thinking is that there is a way to run the desktop environment via X-windows just like any other GUI.  Is this possible? If not, that information is useful as well because I'll stop wasting time trying..

---

### Post by HermanAB on 2016-06-28
You can script a ssh session like this:
ssh -C -c blowish-cbc -X user@server "programname"

Then "programname" will run on the remote system and pop up on the local system.

---

### Post by adrian33 on 2016-06-28
Herman,

what "programname" should I use?  

I ran your code (using blowfish instead of blowish) and received the following error message:

Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Error: Can't open display:

Note: I do not have trouble with X windows forwarding. 

I use ssh -XY user@host

My problem is determining the correct "programname" that will give me the burnt orange Ubuntu desktop. All GUI's work (xlogo,gedit,spyder,gnome-calculator,Nautilus,etc)

Thank you.

---

### Post by HermanAB on 2016-06-28
Oh, OK, you want to run the unity desktop - I haven't actually tried that in years.  I use kubuntu/xubuntu which have different desktops.  A DE is actually a combination of two programs, a file browser that provides the full screen active area and the launcher or panel, that provides the side bar icons and menu.  The file browser part is not particularly useful, but you can run nautilus or other browser over SSH and try to get it into that full screen, borderless mode - apart from making your computer slow due to the large graphic, it won't really do anything though and your local machine already has a working desktop, so why overwrite it...

All that you actually need, is the taskbar, which is called "gnome-panel".  From a panel, you can launch things with the mouse and you can configure the panel any which way you want.
[https://wiki.gnome.org/Projects/GnomePanel](https://wiki.gnome.org/Projects/GnomePanel)

So try this:
ssh -XY user@host "gnome-panel"

You may find that the xfce panel works better though.

---

### Post by adrian33 on 2016-06-28
Hello Herman,

Thank you for the explanation. I am able to run gnome-panel as well as [COLOR=#000000]xfce-panel. I think I like xfce-panel better as it has the Mac-like icon bar at the bottom

[/COLOR]This will be my final solution.  

From what I now understand, trying to run the entire DE is very slow over ssh/X-server. This must be why it was so difficult to find someone that did it.

---

