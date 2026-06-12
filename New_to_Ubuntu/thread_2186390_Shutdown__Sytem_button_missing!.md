---
title: "Shutdown / Sytem button missing!"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by neil5 on 2013-11-07
I've been tinkering with Ubuntu 13.10 and after installing the Skype Wrapper noticed that the icon at the top right of the screen (the gear icon) was missing. I'm very new to Linux so I'm not sure why this would be, but have read that this is a common 'bug' in ubuntu after upgrading, but this was a completely fresh install on and empty hard drive on my laptop.

Not sure of the relevance of this info, but i struggle to even find skype in Software Centre and Synaptic Package Manager. I ended up installing it via the terminal - likewise for the wrapper.

Anyone know how to get the icon back? 

Thanks.

---

### Post by 0N3 on 2013-11-07
It's some bug unfortunately there is a minor work around 

```
[FONT=Ubuntu Mono]killall unity-panel-service[/FONT]
```

---

### Post by neil5 on 2013-11-07
Thanks 0N3

---

### Post by hufemj on 2013-11-10
I have the same problem. That is, no gear icon in the status bar. In fact the status bar is completely blank except for the network manager and Dropbox icons. But when I try 'killall unity-panel-service' I get 'no process found'.

This happened after upgrading from 13.04 to 13.10.

---

### Post by neil5 on 2013-11-11
I had Dropbox syncing away as well. Not sure this has anything to do with it, but all info helps I guess! Does anyone know what actually courses this, or is it one of those mystery bugs that needs hunting down?

---

### Post by philinux on 2013-11-11
Try resetting unity to it's default state. Any customisations like launcher icon size can easily be restored afterwards.

[http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)

---

### Post by hufemj on 2013-11-12
> **philinux said:**
> Try resetting unity to it's default state. Any customisations like launcher icon size can easily be restored afterwards.

[http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)

I tried that. The icons in the side task bar changed to the defaults, but the top status bar did not.

If I leave my session idle long enough so that the screen saver kicks in, the login screen will show the normal status bar with the shutdown (gear) button and the button works. I created a new user, but the status bar is completely blank for the new user as well.

---

