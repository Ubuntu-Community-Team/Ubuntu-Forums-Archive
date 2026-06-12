---
title: "Ubuntu 11.10 Server"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by Esmore on 2012-01-26
Hello I have installed Ubuntu Server from an ISO cd and when i go to restart my pc it takes me to a terminal screen i can log in to my account and do some comands but im trying to get to the log in screen to the desktop not into terminal type thing any ideas what I did wrong or miss?

---

### Post by mikewhatever on 2012-01-26
The server addition doesn't have a GUI, the terminal screen is all there is. If you want/need GUI/Desktop, install it.

---

### Post by Esmore on 2012-01-26
Thank you for let me know there is there anyway you can tell me how to do that?
Thank you again

---

### Post by cariboo on 2012-01-27
THe Ubuntu server is designed to run headless (no keyboard and monitor) so if you are coming from Windows, it can be a bit daunting. There are no GUI applications to manage the server, so your best bet would be to install a desktop until you can familiar with managing the server from the command line. I suggest you install a simple desktop version that looks kind of familiar. Once you've logged on to the server enter the following command to install the Lubuntu desktop:

```
sudo apt-get install lubuntu-desktop
```

The above command will install a familiar looking desktop that doesn't use a lot of resources. Once you have the desktop installed, you can install the services you need eg:

[LIST]
[*]apache2 -- web server
[*]samba -- file sharing
[*]mysql -- database
[*]openssh-server -- remote access server
[/LIST]

and more

---

### Post by critin on 2012-01-27
> **Esmore said:**
> Thank you for let me know there is there anyway you can tell me how to do that?
Thank you again

Download and install the **Desktop version** from the ubuntu site.   You can install the desktop from Synaptic package manager, but I don't know the terminal so can't tell you how to do that.  Having a live cd on hand is handy for later, so I'd go ahead and download it anyway.

---

### Post by 3rdalbum on 2012-01-27
> **critin said:**
> Download and install the **Desktop version** from the ubuntu site.   You can install the desktop from Synaptic package manager, but I don't know the terminal so can't tell you how to do that.  Having a live cd on hand is handy for later, so I'd go ahead and download it anyway.

I'd actually agree with this - you might as well have a full live desktop CD so others can install Ubuntu, or you can recover files on someone else's computer, or anything else that a live CD is useful for.

So, it's up to you: Download the "desktop CD" and install it over your existing Ubuntu Server. Or download the desktop CD and download+install just a desktop environment to go with your Ubuntu Server.

Plug in an Ethernet cable to get an internet connection, then type:

```
sudo dhclient3
sudo apt-get update
sudo apt-get ubuntu-desktop
```

The last line could be 'sudo apt-get install lubuntu-desktop' if you want a faster but less full-featured desktop.

It's probably more efficient for you to just download the desktop CD and reinstall Ubuntu using that, it saves downloading the same thing twice.

---

