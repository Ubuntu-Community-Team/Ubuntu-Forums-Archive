---
title: "how programatically to get wireless information"
date: 2010-04-01
forum: Programming Talk
---

### Post by mobio.dev on 2010-04-01
hi experts, 
i'm newbie for linux programming and using ubuntu 9.10, i just start learning from sample, i would like to know how programatically can get wireless information such as name and signal strength on ubuntu, by default ubuntu using network manager to display wired and wireless info, so i'm trying similar like this for ubuntu, how this can be done, can anyone give idea for this, do anyone have done this before, 
 
thanks in advance

---

### Post by the_unforgiven on 2010-04-02
You can use d-bus to talk to network manager:
[http://projects.gnome.org/NetworkManager/developers/spec-08.html](http://projects.gnome.org/NetworkManager/developers/spec-08.html)

Hope you know how to use [d-bus]("http://en.wikipedia.org/wiki/D-Bus") :)

---

