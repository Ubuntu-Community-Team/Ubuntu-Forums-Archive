---
title: "switched to chromium for internet but I forgot how to install flash"
date: 2014-10-29
forum: New to Ubuntu
---

### Post by newblank25 on 2014-10-29
I switched to chromium for internet but I forgot how to install adobe flash player. Some sites require it. I'm using ubuntu 14.04. Is it in the software center? Or what commands are needed to install it from the terminal.
Can anyone help? thx

---

### Post by oldrocker99 on 2014-10-29
```
sudo apt-get install flashplugin-installer
```

That should fix you right up.

---

### Post by grahammechanical on 2014-10-29
Because of decisions taken by Google the Adobe Flash Plugin installer will not help Chromium. It needs something called pepper flash.

[http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04)

Pepperflash plugin-nonfree installer is in the software where centre but we still need to run a command to get it doing its stuff. Here are the commands that will do the same thing

```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```

Regards.

---

### Post by vasa1 on 2014-10-29
Keep in mind that the current version of Chromium "stable", v 37, lags Google Chrome 38 which was [released on October 7, 2014]("http://googlechromereleases.blogspot.com/2014/10/stable-channel-update.html") and included 159 "security fixes". Google Chrome 38 has since been updated twice.

If the Chromium version isn't kept updated, I wonder if there's a chance of the pepper flash pulled from a newer version of Google Chrome not playing nicely with the older Chromium.

---

### Post by craig10x on 2014-10-30
You might want to consider using Google Chrome instead...it has the pepperflash built in as well as a neat pdf reader too...and it puts a ppa file in your software sources so that you get the latest versions as soon as they are released (through your software updater)...Just download the deb file from their site and right click it and select "install with ubuntu software center"...
Once installed, just locate in your dash search and open chrome from there...then lock it to the unity launcher...

---

### Post by newblank25 on 2014-10-30
thx the pepper flash worked

---

### Post by Bucky Ball on 2014-10-30
Just for the record, pepperflash-installer is now in the repositories as of 14.04. You simply install that and that's it, for future travellers.

---

