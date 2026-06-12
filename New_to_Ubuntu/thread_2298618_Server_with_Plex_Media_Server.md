---
title: "Server with Plex Media Server"
date: 2015-10-12
forum: New to Ubuntu
---

### Post by Benoit_Tremblay on 2015-10-12
Hi,

I currently have a Nas4Free server and would like to upgrade to a Ubuntu server. However, I'm a bit confused and need some help with my research.

I plan on sharing files with Windows and Mac on my network (mainly Windows however) and I want a media server as well. I'm used to plex which wokrs fine, but it's hard to update on Nas4Free.

When I search Google, I see tutorials with command line, but I thought that Ubuntu had a GUI.

Can I do everything with the GUI or will I have to do most things in command line? I can follow a command line tutorial, but since I'm no expert, I don't really understand what I do. So, when it is not working as explained on the tutorial I'm stuck! Futermore, when something is bugging a few month after I install everything, I don't remember what I have done in command line and it is a mess to repair something.

I saw tutorials with command line to install plex media server, but plex media server is available for download on plex web site. Can I install Plex in the GUI as I would in Windows?

Thanks for your kind help!

Benoit

---

### Post by tristan16 on 2015-10-12
Well, since you already know how to use Plex, that makes this super easy.

First, go to [https://plex.tv/downloads](https://plex.tv/downloads) and download the correct version. Once that's done, just double-click the downloaded file, and it will open in the Ubuntu Software Center. From here, you can install it like any other Ubuntu software. Just click install, enter your password when asked, and you're done!

Once it's installed, Plex Media Server is up and running. Open a web browser, and go to localhost:32400/web to set up your media server. If you prefer, you can search for "Plex Media Manager" in the Ubuntu dash, but it basically opens the same webpage in your default web browser.

Sign your server into Plex, forward any needed ports, connect it to Plex.tv, and you're all set!

---

