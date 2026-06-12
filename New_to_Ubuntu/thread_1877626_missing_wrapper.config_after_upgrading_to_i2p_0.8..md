---
title: "missing wrapper.config after upgrading to i2p 0.8.11"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by smokystone on 2011-11-08
Hi all, as the title, the wrapper.config is missing when I got i2p upgrading to 0.8.11, and i2p looked like to be stuck at starting stage.

error message was like this:


grep: /usr/share/i2p/wrapper.config: No such file or directory
Starting I2P Service...
Waiting for I2P Service....................^C

Anyone knows how to fix it or what's wrong with i2p? 

Thanks a lot. :(:(:(

---

### Post by kytv on 2011-11-09
Hi, I'm the one that creates the I2P packages. With changes (that I made) to the upstream packaging to solve a problem on Gentoo, that bug slipped in. :(

 Last night I uploaded a fixed package to the PPA. 

I apologize for the trouble that you experienced.

---

### Post by smokystone on 2011-11-10
> **kytv said:**
> Hi, I'm the one that creates the I2P packages. With changes (that I made) to the upstream packaging to solve a problem on Gentoo, that bug slipped in. :(

 Last night I uploaded a fixed package to the PPA. 

I apologize for the trouble that you experienced.

Nope. I2P is a great idea, please keep improving it to be close to perfect. 

and thanks for replying.

---

