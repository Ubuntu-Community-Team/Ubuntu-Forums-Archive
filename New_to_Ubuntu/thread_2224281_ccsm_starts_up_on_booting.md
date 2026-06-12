---
title: "ccsm starts up on booting"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by gerry-liebling on 2014-05-15
I upgraded to 14.04 and had a few problems, all of which are solved except for one.

On booting, the CompizConfig Settings Manager (ccsm) window comes up on a black screen.  Booting stops until I click on the Close button, after which booting continues normally.

It's not a show-stopper, but it is an annoyance.  Any suggestions?

Thank you.

---

### Post by cariboo on 2014-05-16
Make sure ccsm isn't in Startup Applications Preferences. TOpen the application using either Alt-F2 or a terminal and type the following command:

```
gnome-session-properties
```

Although I'm running Utopic, this is what mine looks like.

---

### Post by gerry-liebling on 2014-05-16
Thank you for the response.

I should have mentioned in my original post that I did check the Startup Applications Preferences and confirmed that ccsm is not on the list.  My startup list includes:
HP System Tray Service
Panel
Window Manager

---

### Post by monkeybrain20122 on 2014-05-16
> **gerry-liebling said:**
> Thank you for the response.

I should have mentioned in my original post that I did check the Startup Applications Preferences and confirmed that ccsm is not on the list.  My startup list includes:
HP System Tray Service
Panel
Window Manager

Not all start up applications show up on the list. In fact most of them are hidden, to display them in Startup Applications, open a terminal and type
```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
```

I have no idea why they hide important info by default.

---

### Post by gerry-liebling on 2014-05-16
OK - did that and got quite a list.  Screen shot of list attached.  A couple more did not fit on the screen - Window Manager and Zeitgeist Datahub - but no ccsm.  Did see several items that I don't use or need, so I unchecked them - like Desktop sharing and Personal File Sharing.

---

