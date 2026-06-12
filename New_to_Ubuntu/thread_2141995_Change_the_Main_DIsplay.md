---
title: "Change the Main DIsplay"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by UserJB on 2013-05-04
I have a laptop with a second external LCD display.  Right now, when I create new windows (gnome-terminals, firefox, etc), those windows are created on the second LCD display.  I would like to change that so new windows are created on the laptop display.   I tried using the Displays from the System Settings menu, but there was no option.  How can I do this?

---

### Post by galgalesh on 2013-05-04
Hi


> [COLOR=#333333][FONT=Ubuntu Beta]Until [/FONT][/COLOR][Ubuntu Brainstorm Idea #17526]("http://brainstorm.ubuntu.com/idea/17526/")[COLOR=#333333][FONT=Ubuntu Beta] becomes a reality, it seems there is no way for non-NVIDIA users to change the primary display (not just move the panels) without resorting to the command line.[/FONT][/COLOR]
You can always try upvoting it, so it becomes a reality.

If you have an Nvdia graphics card, and you have the nvidea drivers installed, you should be able to change it in the nvidea settings dialog.


I'm not sure where the Nvidea settings dialog is located (maybe system settings?). But I found that you should be able to start it with the following command:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo nvidia-settings[/FONT][/COLOR]
```

Let me know if this helps!

---

### Post by UserJB on 2013-05-04
I'm on a laptop and I don't have a separate graphics card, not is the graphics chip nvidia.  So it doesn't help.

---

### Post by galgalesh on 2013-05-04
You can always try:
[http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions](http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions)

---

### Post by UserJB on 2013-05-04
That didn't work.  It did move my panels to the other HDMI display, whic his even worse.

---

### Post by UserJB on 2013-05-04
Why doesn't GNOME work the same on all distros?

---

### Post by galgalesh on 2013-05-04
GNOME is a bundle of different pieces. Every distribution is free to add, remove, change different pieces.

Then you have the different versions of GNOME: GNOME 2, GNOME 3, GNOME fallback... Then you have entirely different desktop environments using some GNOME libraries...

But why that question? Do you know the solution for your problem on another distro?

---

### Post by JohnDillinger43 on 2013-05-04
I haven't had a lot of great experiences with external displays in Ubuntu.  From the little I know, it seems that the left-most window in Displays is the one treated as primary.  Is your laptop screen the left-most window?  If not, try clicking and dragging so that it is.

---

### Post by BluNova on 2013-05-04
I believe that ubuntu at least it did in 12.04 had a bug where apps would open on the larger of the screens and sometimes only maximize on that screen

---

