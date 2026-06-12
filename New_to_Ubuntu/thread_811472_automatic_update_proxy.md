---
title: "automatic update proxy"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by abraxas334 on 2008-05-29
I have the following problem:
I am running gutsy and connect to internet via a proxy. I would like my computer to install all available updates automatically but it does not seem to find them, unless i run the update manager manually and tell it to update. What settings do i have to change to make this possible?
Thanks

---

### Post by forestpixie on 2008-05-29
You can set up proxies in synaptic in settings>preferences>network

Perhaps that will help, but I'm not completely sure.

---

### Post by abraxas334 on 2008-05-29
yeah i set it up in synaptic, as all updates and stuff work fine it just doesn't seem to be able to find updates when i set it to automatically update system.

---

### Post by kpkeerthi on 2008-05-29
> **abraxas334 said:**
> I have the following problem:
I am running gutsy and connect to internet via a proxy. I would like my computer to install all available updates automatically but it does not seem to find them, unless i run the update manager manually and tell it to update. What settings do i have to change to make this possible?
Thanks

Do you have **update-notifier** in System -> Preferences -> Session -> Startup Programs ?

If not, add it to the list of startup programs.

---

### Post by kpkeerthi on 2008-05-29
Just realized that you may also need to change the update intervals for automatic updates under System -> Administration -> Software Sources

---

### Post by abraxas334 on 2008-05-29
All the above had the correct settings, so i don't understand, why it wouldn't work.

---

