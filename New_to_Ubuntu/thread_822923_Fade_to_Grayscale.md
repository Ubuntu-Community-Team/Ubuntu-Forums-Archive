---
title: "Fade to Grayscale?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by dalezjc on 2008-06-08
I don't know if this is a Firefox issue or a Linux thing, but whenever a site becomes unreachable using Firefox, my browser fades to grayscale and becomes totally unusable.  I have to kill the process and restart it.  Is there an option I can set to disable this?

Thanks
Dale

---

### Post by Kronie on 2008-06-08
i'd reccomend u to switch to FF3.0RC1.. because as far as my experience goes with b5-its totally unusable. it crashes, it frezes.. on RC1 i dont have any o fthose problems[so far?]...

---

### Post by crashsystems on 2008-06-08
If it fades to gray, this means that Compiz Fusion is running on your system. Once of the default effects is that when an application becomes unresponsive, then it fades to gray.

If you don't want compiz running on your system, then disable it via the "Desktop Effects" tab in Appearance.

If you want to keep compiz but remove the fade effect, then install the "Advanced Desktop Effects Settings" program, and find the appropriate setting in there.

---

### Post by skitching on 2010-09-08
Another way to disable the fading is to run "gconf-editor" from the commandline, and then go to:
  apps/compiz/plugins/fade/screen0/options
and untick the "dim_unresponsive" box.

Of course this doesn't make the problem program *actually* responsive, it just disables the graphical feedback that happens when the program doesn't respond to compiz messages.

---

