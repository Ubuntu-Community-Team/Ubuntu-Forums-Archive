---
title: "No sound in Lubuntu 11.10"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by Shawn.E.Carr on 2012-01-17
I just installed Lubuntu on a PC and a Laptop.  The PC is fine.  The laptop is not.

I could only move the master volume button after installing pulseaudio.  Also, I am unable to move the master volume in the alsamixer from the terminal.  

I think I can barely hear sound coming from the speakers.  

I have a screen shot and a report from the alsa site.

report =     [http://www.alsa-project.org/db/?f=0431a4ce193c598bcaff83a04d1fca2e494bbcdd](http://www.alsa-project.org/db/?f=0431a4ce193c598bcaff83a04d1fca2e494bbcdd)

---

### Post by Rodney9 on 2012-01-17
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by amjjawad on 2012-01-17
> **Shawn.E.Carr said:**
> I just installed Lubuntu on a PC and a Laptop.  The PC is fine.  The laptop is not.

I could only move the master volume button after installing pulseaudio.  Also, I am unable to move the master volume in the alsamixer from the terminal.  

I think I can barely hear sound coming from the speakers.  

I have a screen shot and ahttp://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148 report from the alsa site.

report =     [http://www.alsa-project.org/db/?f=0431a4ce193c598bcaff83a04d1fca2e494bbcdd](http://www.alsa-project.org/db/?f=0431a4ce193c598bcaff83a04d1fca2e494bbcdd)

Hello and Welcome to Ubuntu Forum and thanks for choosing and using Lubuntu :)

From LXTerminal, please run:

```
sudo lshw -C multimedia

```

Post the output but please make sure to wrap up the text with CODE Tags or highlight it and click "#"

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by Shawn.E.Carr on 2012-01-18
Thank you for the help.  Sorry for the delay.  

> From LXTerminal, please run:

Code:
sudo lshw -C multimedia

```
  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:40 memory:c0000000-c0003fff
```

---

### Post by amjjawad on 2012-01-18
Hi and thanks for your reply :)

Have you checked the links on Rodney's post?

---

