---
title: "Developer wanted for BitTorrent Firefox Plugin"
date: 2007-02-01
forum: Programming Talk
---

### Post by JoshHendo on 2007-02-01
Just to let everyone know, I am working on a new project, [BitFox]("http://code.google.com/p/bitfox"), that will (hopefully) be a BitTorrent client built into Firefox.

I am currently not sure if this will even work out (I think you can, but I am not sure, implement C++/Python code (either will be fine) into a Firefox plugin for example), and I am very new to Firefox extension writing.

I am looking for a developer who is experienced in Firefox extensions (I am experienced in programming in general, but not in Firefox extensions) and who is willing to work on this project (free of charge, as it is a open source, non-profit project, I don’t get money for it).

If you are interested, please email me, [email]josh@joshhendo.com[/email].

---

### Post by Note360 on 2007-02-01
Seems interesting though I dont know what to do.

---

### Post by Note360 on 2007-02-01
I was thinking. Maybe a plugin that interfaces with a home installed web app that downloads torrents, because I dont know how to integrate C++, Python into extensions. We may be able to call out or embed it into the JavaScript though. PHP may be a good Idea

---

### Post by lnostdal on 2007-02-01
what is wrong with associating (mime-thing .. whatever) with .torrent-files and having torrent-software start (or handle, if it's already running) "externally"?  it's a one-click operation

i believe this is the way ubuntu works by default .. but the client might suck a bit .. maybe just a change in default client is all that is required? .. i dunno

---

### Post by Note360 on 2007-02-01
Because thats not fun.

---

### Post by lnostdal on 2007-02-01
> **Note360 said:**
> Because thats not fun.

lol .. fair ennuf :)

---

### Post by JoshHendo on 2007-02-01
Well, I have been writing up some pages on how this could possibly be done. The main BitTorrent client is open source and written in Python, and there are some links on this page: [http://code.google.com/p/bitfox/wiki/RunPython](http://code.google.com/p/bitfox/wiki/RunPython) that show how you can link to Python in a Firefox extension.

Based on the fact that you can run Python in a FF extension, it should be possible. What I am going to be doing for the next few days is just attempting to run just some Python within a extension, and then work on changing it to the BitTorrent code.

Yea, and just opening the torrent file in a external client just takes all the fun out of it. What I was looking for was something that had been done in a client, but could be included in a Firefox extension.

Edit: Here are 2 senarios where this could work:

1. Ben wants to download Ubuntu, but doesn't know what BitTorrent is. He knows how to install extensions in Firefox, and installs this extension as he would with any other extension. A friend of his gives him link to a torrent, and he pastes it in Firefox, and it just appears to download the actual contents of the torrent within Firefox just as any other download.

2. Emily wants to download a large file/program. The website that offers this program as a free download offers a HTTP download, but prefers clients use BitTorrent. Emily does know what BitTorrent is, but isn't able to install or run a client (not a admin and doesn't have enough privileges to run a program from her home directory), but is able to install and run a Firefox extension. She then finds this Firefox extension and is able to download the file she wants.

Also, it is fun to make :)

---

### Post by JoshHendo on 2007-02-03
Well, I have done some more research, and I have found that I can't really use Python within Firefox extensions, but I can use C++ using XPCOM.

If there is anyone experienced with using XPCOM and/or with C++ Bittorrent, and is willing to help out, or at least guide me in the right direction, that would be great.

This extension will get somewhere without help, but it will take a lot longer as I will need to tech myself XPCOM ;)

- Josh

---

