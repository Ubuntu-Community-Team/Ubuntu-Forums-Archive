---
title: "can't see certain images in Firefox"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by TurquoiseWinds on 2012-08-24
hi i just installed Ubuntu and i am completely new to Linux, i need help.

i got online and i went to a site called "why Linux is better" on one of the links there all the pictures are gray and says i need a plug in. well i clicked the bar at the top that says "install missing plugins" and installed the two that showed up. i think they were Adobe Flash...something, im not sure about the rest, the other was Gnash SWF viewer i think. anyways the download took forever but when they finally downloaded i still couldn't see the images only now they were all black. also i updated everything using Ubuntu's update manager, that took about an hour or so which was a really long time. after installing all the updates i went and checked the page again and the pictures are still black. i can see all of the other pictures on the site though. i haven't really done any surfing yet so i don't know if the problem is with just that website or if its a problem with the plugins or Ubuntu i really dont know. please any ideas on how to fix this?

here is the page i was talking about:

[http://www.whylinuxisbetter.net/items/spatial_desktop/index.php?lang=](http://www.whylinuxisbetter.net/items/spatial_desktop/index.php?lang=)

---

### Post by jerome1232 on 2012-08-24
In your address bar type in "about:plugins" without the quotes, make sure there is something listed in there for flash.

If not try quiting and reopening firefox and try again.

If your using gnash to play flash that may be the problem (gnash is an opensoure implementation of adobe flash) try removing gnash and installing adobe's flash plugin.

```
sudo apt-get --yes purge browser-plugin-lightspark gnash-common lightspark-common browser-plugin-gnash 
``````
sudo apt-get install flashplugin-installer
```restart firefox and try again.

---

### Post by TurquoiseWinds on 2012-08-24
oh thank you that worked. i went and downloaded the Adobe Flash Plugin and now it works. i thought they were images but they were actually videos.

i kept Gnash though, i don't know how to uninstall it and it must be useful for something anyways right? or is it just the same as Adobe Flash so isn't needed?

---

