---
title: "Question about creating a Linux distribution"
date: 2013-11-05
forum: Programming Talk
---

### Post by limestorm on 2013-11-05
Hello,
I am creating a distribution based on Ubuntu. I have removed all Ubuntu trademarks and branded the OS with my logos, but I have one problem. When I create the appearance of it in one account, it is fine, but when I log in as a guest, nothing shows up but the desktop icons. How do I make my changes to the desktop environment universal?

---

### Post by nvteighen on 2013-11-05
Is this using GSettings/DConf? If so, take a look [here]("https://wiki.gnome.org/dconf/SystemAdministrators"). All you need to create is "vendor patches" in the correct place so you can set the values you want.

---

