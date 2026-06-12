---
title: "Visual Effects Problem"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by Wharve on 2011-10-20
Ok, so I'm using Ubuntu 10.04 LTS and all of a sudden my screen flickers and my visual effects completely turn off. I've been using the Compiz Cube thingy for a while and it's been working perfectly.

I go to the menu to change my visual effects from "none" to "normal" and it tells me that "Desktop Effects cannot be enabled". 

I have no idea what is causing this problem but I know that my computer is capable of using normal effects since I've been using them from the start. 

Also, I should note that this is a ThinkPad SL410.

---

### Post by ArgusVision on 2011-10-20
Could be a recent update. Especially one to the video driver.

---

### Post by bryncoles on 2011-10-20
Hi Wharve.  

That happened to me this morning -- I'm also using Ubuntu 10.4.  Been compizing just fine.  I boot up this morning, and no compiz.  I resolved this issue by right-clicking the desktop, selecting change desktop back ground, visual effects and selecting 'custom' form the list.  It then restarted whatever graphics driver it had decided not to use.  Interestingly, selecting 'normal' or 'extra' effects didn't work, as it just decided I didn't have the right driver.  I had to choose 'custom'.  

Now, I think you only have the option for 'custom' settings if you have Simple Compizconfig settings manager (simple-ccsm) installed.  

Try that, if it doesn't help, I'm out of ideas!

---

### Post by pme 72 on 2011-10-21
There was a security update to xserver on 10/19 that caused GL to break in Lucid Lynx 10.04. Have you installed any updates recently?

---

