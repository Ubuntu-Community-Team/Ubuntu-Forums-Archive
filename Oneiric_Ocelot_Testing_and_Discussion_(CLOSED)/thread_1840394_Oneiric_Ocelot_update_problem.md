---
title: "Oneiric Ocelot update problem"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rigobot on 2011-09-07
Hello everyone!

Today I upgraded my box and after a reboot all the configuration of gnome are returned to the default ones.
Few examples: the GTK theme is set to raleigh, the configuration of the keyboard is the one I found after the installation.
 The "metacity" theme is correct and I can change it through the gnome-tweak-tool, but everything else doesn't change as the configuration of the keyboard!
Even other settings of the main configuration tool don't work...it seems something that have to do with dbus...could it be?
is it worth to open a bug or someone can help me?

thank you,
rigobot

[edit]
After removing the folder .config in home and restoring various settings everything is back to normal.

---

### Post by kyleabaker on 2011-09-11
Sounds like your install was corrupted in some way. I've been running alpha builds of Ubuntu since Ubuntu 8.04 and have seen similar issues. Sorry I can't offer a quick fix, but what I've done in the past is just a fresh install of the latest build.

I know exactly what you are talking about (and actually live in Raleigh, NC where this theme originated [probably from Red Hat] and work right beside Red Hat), but I have no fix for you situation.

I've noticed that Unity crashes frequently and causes Nautilus to go into "Raleigh Mode", but after force killing Nautilus and restarting it its usually back to normal. Still a bug but not the say deal.

I suggest you force a crash log on Nautilus, Gnome or gconf, which ever is causing the problem and submit it to LaunchPad for further inspection.

kill -11 [pid]
(where pid is the process id and can be found in System Monitor)

Best of luck, I used to file a lot of bugs in LaunchPad, but now they are anal about the quality whether its auto generated (apport) or not, so be as descriptive as possible.

I think the admins are getting lazy and just marking invalid on bugs (important or not) that aren't clear cut (as a software developer myself I can tell you that is terrible practice for them, but be descriptive by all means). Best of luck.

---

### Post by rigobot on 2011-09-11
> **kyleabaker said:**
> Sounds like your install was corrupted in some way. I've been running alpha builds of Ubuntu since Ubuntu 8.04 and have seen similar issues. Sorry I can't offer a quick fix, but what I've done in the past is just a fresh install of the latest build.

I know exactly what you are talking about (and actually live in Raleigh, NC where this theme originated [probably from Red Hat] and work right beside Red Hat), but I have no fix for you situation.

I've noticed that Unity crashes frequently and causes Nautilus to go into "Raleigh Mode", but after force killing Nautilus and restarting it its usually back to normal. Still a bug but not the say deal.

I suggest you force a crash log on Nautilus, Gnome or gconf, which ever is causing the problem and submit it to LaunchPad for further inspection.

kill -11 [pid]
(where pid is the process id and can be found in System Monitor)

Best of luck, I used to file a lot of bugs in LaunchPad, but now they are anal about the quality whether its auto generated (apport) or not, so be as descriptive as possible.

I think the admins are getting lazy and just marking invalid on bugs (important or not) that aren't clear cut (as a software developer myself I can tell you that is terrible practice for them, but be descriptive by all means). Best of luck.

Thank you for your contribute...however, as I wrote, I solved the problem in a brute-force way,I hope that it will not appear again.
I think that this beta has some problem, above the others, with the X server + nvidia driver...sometimes compiz and X are eating the CPU and firefox is slow, sometimes everything (like now) is fine and smooth...


cheers,
rigobot

---

