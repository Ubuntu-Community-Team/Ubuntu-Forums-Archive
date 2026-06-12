---
title: "How to deal with line-in on Audacity"
date: 2011-03-12
forum: Outdated Tutorials &amp; Tips
---

### Post by shantiq on 2011-03-12
**Now using Line-in with Audacity** can be tricky at times
so here is a quick little how-to which will hopefully help the perplexed








**[SIZE="2"]1. [/SIZE]**  The **line-in** is mute by default which is baffling but that is the way it is


i am doing this with **alsa** here which works fine too but i am sure pulse will work too  (use pavucontrol if you want to stay with pulse instead of alsa-mixer but i suggest try with alsa first)



so first thing is to enable the **line-in**




to install open terminal   ```
sudo apt-get gnome-alsamixer
```   or install it through synaptic or ubuntu software centre



then find it under    applications/sound and video


[B][SIZE="2"]
2.[/SIZE][/B] unclick the relevant ones for you  depending on your setup


=================================================


**[SIZE="2"]3.[/SIZE]**then go to audacity


and click on view/toolbars/devices


click on devices then pick your device you want as a line-in



=================================================

**or** you can go to edit/ preferences/devices as another route


=================================================
**[SIZE="2"]4.[/SIZE]**
**you will then see** a drop-down box on your audacity see attached picture   **Then pick **
   **mix0**


=================================================

**[SIZE="2"]5.[/SIZE] Also** make sure your input/output devices under preferences/sound are correct before you start; that they point to the correct input you wish to use as a line-in



**Hope this is of use to many of you...**

---

