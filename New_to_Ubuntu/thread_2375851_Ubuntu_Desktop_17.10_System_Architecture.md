---
title: "Ubuntu Desktop 17.10 System Architecture"
date: 2017-10-28
forum: New to Ubuntu
---

### Post by kunalv-shah on 2017-10-28
Hello All,

I recently switched to Ubuntu and working my way to understand the various components like kernel, DE, Desktop Shell etc. Can anyone please point me to the graphical image or diagram that shows various software stack laying on top of each other so that I can understand the interaction? For example, GNOME shell on top of Wayland (or Xorg) which is on top of Linux kernel etc. But in more detail.

I try to check a few but they are very old (from 2011) and I am sure things have changed significantly since. 

Thanks
Kunal Shah

---

### Post by jpberes on 2017-10-29
Dear,
The things have NOT significantly changed, the architecture is still the same principle as from 2011 and even earlier ...
The changes occurring is the replacement of the old X11 system by some new onces, for instance Wayland and for the rest the updating of the Desktop Environments such as XFCE, Gnome3, KDE Plasma 5 etc.
For the Desktop Environments, running on top of the Windows MAnager (X11 or Wayland) a shift is being made from Gtk2 towards Gtk3 (for XFCE, Mate, ...) ... some others are using Qt (such as LxQT and KDE).
Gtk and Qt are the Development environments (with all the possible extras) to create the desired Desktop Environments.
I did try not to be too technical but simply 1st layer is KERNEL (with on one side on top the Shells (Bash, Dash, Csh, Zsh) on the other side on top of the Kernel the Windows Manager (currently mostly X11 - sometimes wrongly called Xorg OR Wayland OR previously also MIR) and on top of the Windows Manager the Desktop Environments.
Regards,
JP

---

### Post by kunalv-shah on 2017-10-30
so for example, when I use wayland - it is the so called x server implementation and GNOME as GUI Shell and when I use xorg at the login it uses xorg implementation of x server and GNOME as GUI shell. Is that right?

also Unity is replaced by GNOME.

Is this understanding correct?

---

### Post by mlan on 2017-10-31
[https://en.wikipedia.org/wiki/Wayland_(display_server_protocol)]("https://en.wikipedia.org/wiki/Wayland_(display_server_protocol)")

Yes, Unity has been replaced by Gnome.

---

### Post by jpberes on 2017-10-31
Hmmm not completely .. Wayland is a replacement of the X11 ... so it is not an x server implementation, it is Wayland (!) ... Xorg = X11 (simply the naming, had to do with some historical reasons),
And Unity is an extra implementation on top of Gnome3 (a shell on a shell), like also Cinnamon is build on top of Gnome3 ...
So the native shells on top of Wayland or X11 (Xorg) are Gnome2, Gnome3, KDE, XFCE, LXDE, LQte ...
Where as some are build with the Gtk (2 or 3) toolkit and some with the Qt toolkit ...
KDE, KDE Plasma, LQte are build with the Qt toolkit (so they say they are Qt environments) AND Gnome (2 & 3), XFCE, LXDE are build with the Gtk toolkit (Gtk2 or Gtk3) ;-)
More info can be found on -  [https://en.wikipedia.org/wiki/Desktop_environment](https://en.wikipedia.org/wiki/Desktop_environment)

---

### Post by kunalv-shah on 2017-10-31
thanks. that helps.

---

