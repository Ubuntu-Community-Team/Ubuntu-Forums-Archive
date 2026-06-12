---
title: "[SOLVED] Sound events"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by bob brazie on 2008-11-20
8.10

I am having trouble getting the sounds to work in the sound preferences. The only sound that plays at the event time is the log-on sound at start-up.

The sounds play when I click on the test button.

In the help files It says: "you must select enable sound server startup option, and the sounds for events option before you can access the sounds events tabbed section"

I can't find where to enable this sound server startup option. I only have two tabs in the system/preference/sounds box. Devices and Sounds.

Thanks in advance. Bob.

---

### Post by beno1990 on 2008-11-20
Try this:

From a terminal open

```
sudo gedit /etc/apt/sources.list
```

Then add the following line to the bottom

```
deb http://ppa.launchpad.net/gkulyk/ubuntu intrepid main
```

Then open synaptic, reload, and mark all upgrades for installation.

---

