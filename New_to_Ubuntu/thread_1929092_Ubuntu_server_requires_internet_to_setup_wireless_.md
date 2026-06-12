---
title: "Ubuntu server requires internet to setup wireless card?"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by Steelmesh on 2012-02-21
On top of dealing with the console freezing, I still tried to push forward with this project.  I have no idea how to fix my PCI wireless card.  I purchased a specific model as recommended by ubuntu. Atheros chip in it and it recommends the madwifi driver. I deactivated my Mobo wireless adapter in bios, as it is not working.

In console, I think was doing iwconfig and it did indeed see the card.  However, I don't know how to get these drivers because some of these tutorials I find on the google give me code that tries to get the stuff off the internet, catch 22 there.

My steps maybe you can help me with:
1) I just did a clean install (and trying to reinstall, having freezing issues in console)
2) I think my next step is to get it connected to wifi so I can obtain other modules
3) Lots of stuff, but 1,2 more important

Building a home server for personal use (host websites, ftp, backup).

---

### Post by partloer on 2012-02-21
Hello Steelmesh,

I would have to recommend using a wired connection especially for the server uses that you have listed as it is much more stable.

If that is not an option it would be very helpful to initially connect to the internet through a wired connection to initially download and install the MadWifi project.

However if not then downloading on a thumb drive then copying the files will also work.  I don't know what you have done thus far but from their website [http://madwifi-project.org/]("http://madwifi-project.org/") they have a good first time user howto guide [http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo") I would recommend going through that and if you run into any problems post them.

---

