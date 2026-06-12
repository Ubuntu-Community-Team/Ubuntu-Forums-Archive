---
title: "No icons after updates installed"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by chris_dummer on 2014-02-23
[COLOR=#000000]chris_dummer[/COLOR]
[COLOR=#000000][INDENT]**no icons after updates installed**
i have an old ibm thinhcentre (s50)drivers on [windows]("http://ubuntuforums.org/#") system i upgraded from ver13.4 to 13.10 as the grahics drivers for linux were no longer available for linux 13.4(ubuntu) it worked fine with my icons on the left ie home settings dash etc. i installed the latest updates this morning and all i get after restart is my wallpaper(no task bar on the left. i managed to lnstall chrome which i can load from the terminal (ctl+t then google-chrome-stable)in chrome on facebook my games now work fine so assume the graphics driver has made a difference.

q:how do i get the task bar back?
q:how do you pin apps to the desktop?

new to ubuntu please help.

regards ):P[/INDENT][/COLOR]

---

### Post by kostkon on 2014-02-23
You could try resetting compiz/unity.

Open the terminal to start chrome and load [this]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html") page (that shows you how to reset unity/compiz), then open a new tab in your terminal to be able to give all the commands needed to accomplish that.

Finally reboot, by giving
```
sudo reboot
```
and providing your password when asked.

---

### Post by chris_dummer on 2014-02-23
thanks for prompt reply will try and get back to you i will have to try and install chrome again as i reinstalled ubuntu again this morning and just get the mouse icon and default wallpaper.

---

### Post by bapoumba on 2014-02-23
Hello, I've changed the thread title from "no reply to thread after i week" to "No icons after updates installed", cheers :)

---

### Post by kostkon on 2014-02-23
> **chris_dummer said:**
> thanks for prompt reply will try and get back to you i will have to try and install chrome again as i reinstalled ubuntu again this morning and just get the mouse icon and default wallpaper.
If it's a fresh installation then more likely it's a graphics card/driver problem. What's your system specs?

---

### Post by fdrake on 2014-02-23
do not think is a video card issue:
try this
```
sudo apt-get -f install && sudo apt-get --reinstall install unity
unity --reset
unity --replace

```

---

### Post by chris_dummer on 2014-02-23
sorry guys i could not try your sugestions as i could not access any software:
so i installed ver 14 beta and now everything is working perfectly chrome(chromium),graphics desktop etc .
 I would normally have  persisted but have been battling for a week (even tried debain) i was once ok with unix(old sun sparc`s) but have forgoten the knowledge.
Although this old think centre has limited graphics its now being used to relearn linux insted of being scraped.

thanks for your efforts Best regards Chris(TOPPER).

---

### Post by fdrake on 2014-02-23
> **chris_dummer said:**
>  i installed ver 14 beta and now everything is working perfectly chrome(chromium),graphics desktop etc .
 

A beta! I would be very carefull installing a beta on my primary system . Anyway hope everything work for the best . Just remember it's still a beta release . so if this is your primary working/studying pc i would think again about it.

---

### Post by chris_dummer on 2014-02-23
no its an old machine destined for scrap just using to gen up on unix again. thnks anyway

---

