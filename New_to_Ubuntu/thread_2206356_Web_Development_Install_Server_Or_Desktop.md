---
title: "Web Development: Install Server Or Desktop?"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by i-mail-l on 2014-02-18
Hi,

Using Win 8.1 for web design. I have a number of clients with LAMP web sites so I installed Ubuntu 12.04 in a VM on my desktop. I worked with Unix a -long- time ago, but forgotten a lot of it, so this has been a refresher. Works fine.

I now would like to install a complete dummy web server environment... PHP, MySQL, etc. Should I remove Ubuntu 12.04 Desktop and install the Server version instead, or can I set up a LAMP environment with the Desktop version?

If I go to the server version, do I lose the GUI desktop and those applications?

TIA,

---

### Post by Impavidus on 2014-02-18
In principle, you can install any software from the desktop version on the server version and vice versa. By default, the server version doesn't have a GUI.

---

### Post by SeijiSensei on 2014-02-19
Just follow the [instructions here]("https://help.ubuntu.com/community/ApacheMySQLPHP") to install the LAMP stack via tasksel.  The presence or absence of a GUI desktop environment is irrelevant.

---

### Post by i-mail-l on 2014-02-19
> **SeijiSensei said:**
> Just follow the [instructions here]("https://help.ubuntu.com/community/ApacheMySQLPHP") to install the LAMP stack via tasksel.  The presence or absence of a GUI desktop environment is irrelevant.

Thanks. I guess I'm a bit confused then as to what the difference is between Ubuntu 'Desktop' v. 'Server'. I don't want to over-simplify, but would it be fair to say that the core is the same but one has a GUI and the other comes with various server bits (Apache, etc.) pre-installed?

I'm pretty old and back in the day there wasn't a 'server' Unix vs. a 'desktop' Unix... there was just =Unix= and if you wanted a 'desktop' you installed some sort of X-Windows thing on top.

TIA,

---JC

---

### Post by Dave_L on 2014-02-19
> Thanks. I guess I'm a bit confused then as to what the difference is between Ubuntu 'Desktop' v. 'Server'. I don't want to over-simplify, but would it be fair to say that the core is the same but one has a GUI and the other comes with various server bits (Apache, etc.) pre-installed?

That sounds accurate: [https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)

---

### Post by i-mail-l on 2014-02-19
> **Dave_L said:**
> That sounds accurate: [https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)


Thanks. My bad for not searching first.

---

