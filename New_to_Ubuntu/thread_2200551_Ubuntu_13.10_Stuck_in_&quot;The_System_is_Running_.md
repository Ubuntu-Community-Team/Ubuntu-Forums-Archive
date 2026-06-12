---
title: "Ubuntu 13.10 Stuck in &quot;The System is Running in Low-graphics Mode&quot;."
date: 2014-01-20
forum: New to Ubuntu
---

### Post by arden2 on 2014-01-20
I have an Ubuntu 12.10 installed in my laptop. Because I can't install my wifi card in 12.10, I decided to install 13.10. The installation was successful but after rebooting after the installation, It is stuck in "The System is Running in Low-graphics Mode" screen. I already tried failsafex but i got an error. Can someone help me with my problem?

---

### Post by squakie on 2014-01-20
If you use the search in the forum, you will find many posts about this.  Whether any are specific to your laptop I don't know, but they may be specific to the graphics adapter the laptop is using.  The was such a thread that was just finished up in the last few days if you scan the forum.

One thing we would need to know is the chipset used for your graphics adapter, so please post back the output of the following command:

lspci | grep VGA

---

