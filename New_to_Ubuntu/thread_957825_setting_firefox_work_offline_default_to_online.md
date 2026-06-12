---
title: "setting firefox work offline default to online"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by ranch hand on 2008-10-24
OK: I am using, right now to post this, a usr5610c internal modem.  It works great, thanks to the great help I had in these forums getting it configured.

Firefox always comes up set to work offline.  This really is getting on my nerves.

When I boot up the modem is dialing before the log on screen comes up and I have never been able to get into the Ubuntu working screen before I am connected.  This is a great hardware modem that really "fights" for the connection and keeps the speed as high as possible even when I have a fairly crappy connection.

I have gone through the Launchpad stuff on this bug.  None of this works because there is no  "/etc/network/interfaces" file at all.

If you cursor over the network applet it tells you there is "No network connection" but is you click on it it gives you the opptions of connecting or disconnecting from Dial Up Connections /ppp0 via modem.

What bugs me is that I used Netscape 7.1 for years and you can set the online/offline default in the preferences menu.

Does anyone have any ideas what I should try here?

I would prefer to load Netscape, frankly, but I don't think it is compatable with Hardy.

Thank you in advance.

---

### Post by pdwerryhouse on 2008-10-24
I don't know what has happened to the browser online/offline button (mine is missing too), but you can try setting this from the about:config menu. So, try this:

* In the url field, enter:    about:config
* Look for the preference name   "browser:offline"
* Make sure its value is set to "false" (double click on it, to change it)

That's all that it should need.

---

### Post by ranch hand on 2008-10-24
> **pdwerryhouse said:**
> I don't know what has happened to the browser online/offline button (mine is missing too), but you can try setting this from the about:config menu. So, try this:

* In the url field, enter:    about:config
* Look for the preference name   "browser:offline"
* Make sure its value is set to "false" (double click on it, to change it)

That's all that it should need.

I can set it every time in the menu for online but it bugs me and really bothers my wife.

Your suggestion is interesting, didn't see it on launchpad, but: I have 2 things that come up when I do this:
(1)browser.offline                 user set   boolean   false
(2)browser.offline-apts.notify     default    boolean   true

I have promised to be good and not break Ubuntu for the 5th time until I come up with a way to preserve files so I think I better ask if I should change #2 before I do it.  What do you think?
Thanks

---

### Post by pdwerryhouse on 2008-10-24
Only change the first one (browser.offline). I'm not sure what the second one does...

---

### Post by Boondock5 on 2010-11-19
> **pdwerryhouse said:**
> I don't know what has happened to the browser online/offline button (mine is missing too), but you can try setting this from the about:config menu. So, try this:

* In the url field, enter:    about:config
* Look for the preference name   "browser:offline"
* Make sure its value is set to "false" (double click on it, to change it)

That's all that it should need.

This just fixed my wife's computer, with the new AMD64 I5 processor, and Ubuntu 10.04LTS 64bit
It took a bit for me to decipher how to do  this as I'm so mouse impaired.

Also, I had to restart the computer to get it to take affect.

Thanks:D

---

