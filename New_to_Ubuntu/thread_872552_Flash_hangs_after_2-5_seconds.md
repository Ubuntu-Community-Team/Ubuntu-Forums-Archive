---
title: "Flash hangs after 2-5 seconds"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by kramer65 on 2008-07-28
Hello,


I've got ubuntu 8.04 installed recently and now have a problem with flash players. It loads and displays video (youtube etc.) for 2-5 seconds and then just stops like it is in pause. I can drag the "position-point" to another point in the video and then it plays again for a couple seconds after which it just hangs again.

All other media on my computer is working fine. Just the flash is making trouble, which is quite annoying.

Can anybody help with this?

---

### Post by northern lights on 2008-07-28
Do you have the package 'flashplugin-nonfree' installed?

If not, or unsure, run ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by kramer65 on 2008-07-28
Yes I got that installed. I ran the command again and it said that it was already installed.

Any more ideas?

To be honest, this is quite a dealbreaker for me. I really love ubuntu, but if flash doesn't work anymore, that would be quite a problem..

---

### Post by gjoellee on 2008-07-28
try use flash 10BETA, read more here: [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by silkstone on 2008-07-28
See this tutorial and scroll down to the section headed 'Troubleshooting - Adobe Flash Player'.

That tells you how to install the Flash 10 beta is such a way that it can be replaced by the one in the repositories very easily, if you ever want to do that. It works fine for me.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by LTFC2020 on 2008-07-28
try this it worked for me

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by kramer65 on 2008-07-28
Well well well, I tried various of the things in the post you gave me. I got errors all over the place... but... it works somehow again!!

I have no clue where something went right, but hey, it's ok again. How can I check which version is installed now?

---

### Post by boom2k1 on 2008-08-22
I also have this problem suddenly.. i tried reinstalling flash using the flash in the ubuntu repository, but it didn't work for me.

---

### Post by kramer65 on 2008-08-22
Well youtube works like a charm now for a couple days already. However, when I go to [a chart on bloomberg]("http://www.bloomberg.com/apps/cbuilder?ticker1=NDX1%3AGR"), it doesn't work and says I need a version of flash higher than 8..

Anybody a solution to this?

---

