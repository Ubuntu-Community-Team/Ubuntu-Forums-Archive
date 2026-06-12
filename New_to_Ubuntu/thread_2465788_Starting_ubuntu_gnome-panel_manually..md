---
title: "Starting ubuntu gnome-panel manually."
date: 2021-08-11
forum: New to Ubuntu
---

### Post by antonio-cpr on 2021-08-11
Hi! 

I'm using Ubuntu last version (minimal install) and I would like to know how do I start the panel of gnome manually because I want to use openbox as window manager. I tried gnome-panel but the output is "command not found". I installed gnome-panel but it is not the same as used by Ubuntu. I want this panel because I want to use system-monitor addon and the panel started with "gnome-panel" does not show the addon. The main thing is I want the system-monitor on my panel when I'm using openbox and gnome-panel started manually doesn't show it.

Thanks!

---

### Post by tea for one on 2021-08-11
When you arrive at the log-in screen, there is an icon in the lower right hand side.

Click on it and let us know the choices available.

---

### Post by antonio-cpr on 2021-08-11
> **tea for one said:**
> When you arrive at the log-in screen, there is an icon in the lower right hand side.

Click on it and let us know the choices available.

[LIST]
[*]Gnome Flashback (Metacity)
[*]Openbox
[*]Ubuntu
[*]Ubuntu On Wayland
[/LIST]

---

### Post by tea for one on 2021-08-12
I'm pretty sure that gnome-panel is heavily tied into gnome-shell, therefore it would be essential to start an Ubuntu session.

Doesn't Openbox include a native panel?

Can you not add a System Monitor launcher to the Openbox panel?

Finally, there is Conky system monitor - Huge thread here [https://ubuntuforums.org/showthread.php?t=1771033&highlight=conky](https://ubuntuforums.org/showthread.php?t=1771033&highlight=conky)

---

### Post by grahammechanical on 2021-08-12
> I would like to know how do I start the panel of gnome manually

You have Gnome Panel installed. At the login screen you select Gnome Flashback and the user interface will be Gnome Panel also known as Gnome 2 user interface. 

I do not think that you can have Open box and Gnome Panel running at the same time. Gnome Panel was the user interface for both the Gnome 1 and Gnome 2 desktop environments. When you installed Gnome Panel you installed a user interface. Try looking for the System Monitor utility in Openbox. Does Openbox have drop down menus? Does Openbox have a menu listing for applications or system utilities? If it does, you might find System Monitor there and it might load and run but do not expect System Monitor to look as if it is part of Openbox. 

Regards

P.S. Please read this

[https://wiki.debian.org/Openbox#System_monitors](https://wiki.debian.org/Openbox#System_monitors)

---

### Post by tea for one on 2021-08-12
I've misinterpreted the OP's original question.
I thought that the OP was referring to the Top Bar in gnome-shell rather than the [COLOR="#0000FF"]Traditional panel used in GNOME Flashback[/COLOR]

Apologies for my misguided intervention.

---

### Post by antonio-cpr on 2021-08-14
> **tea for one said:**
> I'm pretty sure that gnome-panel is heavily tied into gnome-shell, therefore it would be essential to start an Ubuntu session.

Doesn't Openbox include a native panel?

Can you not add a System Monitor launcher to the Openbox panel?

Finally, there is Conky system monitor - Huge thread here [https://ubuntuforums.org/showthread.php?t=1771033&highlight=conky](https://ubuntuforums.org/showthread.php?t=1771033&highlight=conky)
Ok. I didn't know that. No Openbox doesn't include that.

Well the thing is I thought Ubuntu last version would run very slow in my laptop but I was wrong, it running fine. That's why I was thinking about use Openbox. I could install xfce4-panel though. This is the panel I was using with Openbox when I had Arch Linux installed. I just want to use the panel offered by Gnome instead install another one. But for now I will stick with Ubuntu-Gnome.

Thanks for your answers by the way.

---

