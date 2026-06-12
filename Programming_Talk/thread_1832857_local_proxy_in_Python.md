---
title: "local proxy in Python"
date: 2011-08-25
forum: Programming Talk
---

### Post by newelfik on 2011-08-25
Hello every one, 

In order to get back screensaver status information of each user on a local system and send them to a specific application. I will use dbus python API on org.gnome.screensaver

The problem is that dbus doesn't run inter session. So a little proxy has to be done and launch at session start for each user logged.

And when proxy get a signal from screensaver, it will inform the application. 

I wonder of the protocol to use between proxy and application.

There will not internet communication, or LAN communication. Only inter process and inter user, in local.

For most coherence, the proxy must to be in Python language.

Which protocol could be the best in my case ?

---

