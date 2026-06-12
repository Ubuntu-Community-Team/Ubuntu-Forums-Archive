---
title: "Title Bar (Missing)"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by D|F on 2008-05-21
Hello can anyone help me? actually i was installed Ubuntu 7.10 Gutsy Gibbon,
and i was installled KDE desktop. My question is when i open Firefox or others windows application i cannot see my title bar.
Thi thing heppen after i run compiz manager in Run Command.
please someone help me.


See the snapshot.

---

### Post by bumanie on 2008-05-21
What are your computer specs. including graphics card please. I know a possible fix if you are running an nvidia card and your computer is equipped to handle desktop effects.

---

### Post by shifty_powers on 2008-05-21
[http://ubuntuforums.org/showthread.php?t=799110](http://ubuntuforums.org/showthread.php?t=799110)

may help you

---

### Post by D|F on 2008-05-21
Im Using Desktop with 2.6Mhz INTEL Processor and Nvidia G-force FX5200.

---

### Post by bumanie on 2008-05-21
That's a fairly old gpu, may struggle with desktop effects if you have only 512mb ram - if you 1gig of ram it should be OK. Interminal type > sudo nvidia-xconfig --add-argb-glx-visuals -d 24  If your computer can handle desktop effects, that should fix the title bar issue.

---

### Post by D|F on 2008-05-21
Yes im using 1Gb of Ram...
when i put this

darknessfall@ubuntu:~$
 
Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

darknessfall@ubuntu:~$

The resault is like that, when i open any application, still without title bar. Do i have to restart my system? Or there's other way to fix this problem?
Please help me.
Thank for the information anyway.

---

### Post by D|F on 2008-05-21
darknessfall@ubuntu:~$ sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

darknessfall@ubuntu:~$

---

### Post by bumanie on 2008-05-21
When I used that 'fix' on a previous computer with an older nvidia card than you have, I think it worked straight away. No harm in doing a restart. The message you are getting is saying that the system has changed some settings and has backed up the original settings. Try a reboot/restart.

---

### Post by D|F on 2008-05-21
i already restart my system, but still the same problem i've got, after i login my screen monitor displayed the original screen monitor, but after 1/3 second my screen monitor turn dark and come back with the same problem that i cannot open my Title Bar...can i fix it?

---

### Post by sailor2001 on 2008-05-21
if  the trouble is when you have compiz enabled, go to compiz settings,effects,window decoration

---

### Post by D|F on 2008-05-21
Sorry i have to ask u where is the compiz settings,effects,window decoration?
i can't find it...

---

### Post by sailor2001 on 2008-05-21
system/preferences/advanced desktop settings.....this will be the entire setup for your compix. effects is an entire section in the menu

---

### Post by sailor2001 on 2008-05-21
you could also go to synaptics and /compiz/ and find the settings manager

---

### Post by D|F on 2008-05-21
i've found compizcomfig-setting-manager in synaptic.
But i don't know what i have to do next...
Please some explain to me ...

---

### Post by anarkae on 2008-05-29
try:
sudo apt-get install compiz-kde

---

