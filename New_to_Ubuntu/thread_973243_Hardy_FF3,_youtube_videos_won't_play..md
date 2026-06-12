---
title: "Hardy FF3, youtube videos won't play."
date: 2008-11-06
forum: New to Ubuntu
---

### Post by {Nabla} on 2008-11-06
When I go to youtube, in place of the video I get:

> 
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player.]("http://www.adobe.com/go/getflashplayer/") 

I checked preferences in FF, and javascript was already on, so I clicked onto the adobe page and downloaded the "tar.gz for linux", to my desktop, then extracted. When I tried to run the executable text file (by double click or right click>run), I get that message, "Do you want to run this file or display it's contents?", and clicking run does nothing but close the message. 

I then tried the "run in terminal option and this is what I got:

```


Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 10 for Linux

Adobe Flash Player 10 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 10 will be installed in your home directory.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 10 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Mozilla installation directory  = /home/matt/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): 


```

I then went to matt/.mozilla, by showing hidden files, and searched for xpti.dat, selected it and hit delete, but the message still continues on youtube. What am I doing wrong?

---

### Post by phidia on 2008-11-06
What verion and architecture (32 or 64 bit) of ubuntu are you running?
You should install flash from the package manager. System > Admin > Synaptic.

---

### Post by nhasian on 2008-11-06
to install adobe flash 10 from the terminal type:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by {Nabla} on 2008-11-06
I'm on 32-bit 8.04.1, I'll try those things.

---

### Post by Thelasko on 2008-11-06
> **{Nabla} said:**
> downloaded the "tar.gz for linux", to my desktop, then extracted. When I tried to run the executable text file (by double click or right click>run), I get that message, "Do you want to run this file or display it's contents?", and clicking run does nothing but close the message.
It didn't work because you aren't supposed to install tar.gz files in Ubuntu.  Please [read this.]("http://www.psychocats.net/ubuntu/installingsoftware")
Instead, go to the terminal and enter:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by {Nabla} on 2008-11-06
Thanks, it worked.

---

