---
title: "Ubuntu Server 13.04 questions"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by AxelVK on 2013-06-16
First of all; as the header states - I am a total noob to anything Linux so please be patient. I have a HP Microserver with AMD 64 bit CPU and I have just installed Ubuntu Server 13.04. The intention is to run Plex to manage my movie collection. I have managed to install Plex and it is running but having issues. However, if I plug a screen and keyboard in and start the server, I get presented with a graphical login screen and I can log in but I end up with just a blank blue screen. The server itself is running as I can SSH in to it. I think I have installed Gnome which I thought was like a graphical desktop ala Windows. Can someone please give me some pointers what to look for? I am somewhat familiar with the basic commands and I am able to use NANO if any files need editing. Thanks in advance and apologies for the dumb questions.

---

### Post by 2Stoned on 2013-06-19
:confused:

Why don't you use the desktop version?

---

### Post by snowpine on 2013-06-19
If you're not sure what you installed, then probably you didn't install the right thing. ;) A basic command that will install the full Ubuntu desktop environment:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

It's very important to understand that Plex is third-party software that is not provided or supported by Ubuntu in any way. Was your Ubuntu system working properly before you installed Plex? Looking at the Plex site, I see that it is tested for Ubuntu 10.04, but you are using 13.04... that is a difference of three years and six releases, which may explain why it isn't working properly. :(

There are plenty of *supported* applications for managing your media collection (for example XBMC) available from the Ubuntu Software Center. I would recommend sticking to tested and trusted software for a stable and enjoyable Ubuntu experience. If you must use 3rd-party software then make sure it has been thoroughly tested with the 13.04 release you are using (not some other older release).

---

### Post by DogMatix on 2013-06-19
I have a Plex Server running on a Ubuntu 12.04 install. It serves a Sony TV, a Playstation, a Mac & a Windows Phone. However, there are issues mainly concerning Plex & its use of Silverlight. Plex certainly prefers a Windows or OSX host.

---

### Post by zrdc28 on 2013-06-20
plex for ubuntu server 

Google the above and it will give you plenty of info to do it!

---

