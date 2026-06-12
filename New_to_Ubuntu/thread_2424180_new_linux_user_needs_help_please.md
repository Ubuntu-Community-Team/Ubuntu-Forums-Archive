---
title: "new linux user needs help please"
date: 2019-08-05
forum: New to Ubuntu
---

### Post by MrRubik on 2019-08-05
I'm coming from Windows 10 and I'm a very new Linux user so please don't judge me too harshly. I'm an MIS major and an expert Windows user but this is all still very new to me. I need some help installing programs. One of the most important programs I use is a multi-messaging/multi-email program. On Windows, I was using Shift and I'm a paid user. I love the program and I want to use it on Linux. When I download the program, it comes in a zip file. I have no problem unzipping the file and running it. It runs fine from the unzipped folder. But how do I INSTALL it? It doesn't come with a configure file to install, nor any readme or documentation. Do I just copy the folder to my desktop and run it from there? Will it auto-update like on Windows if I do this? Maybe I'm just a Linux noob, but it doesn't seem right to me that a program doesn't install. Another software like Shift that I'm looking at is a free one called Station. It comes in an AppImage format. Again, I can't figure out how to install it. It just runs from that file. I really need to learn Linux as I'm an MIS major and it may come in handy in my career. So, can someone please help me and tell me what I do with these files/folders to INSTALL them? Or if they just plain won't install, where should I put the folders? I have included links below to the Shift and the Station programs. I would really appreciate some help here. Thanks.


PS - Are there any multi-messaging/multi-email programs for Linux that are better than these 2?

---

### Post by wildmanne39 on 2019-08-05
Hello and welcome to the forum, I removed the links as they are for downloading the files, please provide links so our volunteers can read about the apps instead of downloading them, as a general rule we do not like to download files we are not sure about.

Thanks

---

### Post by mastablasta on 2019-08-05
> **baileyhood said:**
> I have no problem unzipping the file and running it. It runs fine from the unzipped folder. But how do I INSTALL it? It doesn't come with a configure file to install, nor any readme or documentation. Do I just copy the folder to my desktop and run it from there? Will it auto-update like on Windows if I do this? Maybe I'm just a Linux noob, but it doesn't seem right to me that a program doesn't install. Another software like Shift that I'm looking at is a free one called Station. It comes in an AppImage format. Again, I can't figure out how to install it. It just runs from that file. ?

well good programs provide users documentation (on web or with the application).

obviously you haven't been around long (at least not in IT). in the old DOS days and first windows days it was nothing unusual to just unpack the program and run it. there were no installs needed. this is nowadays again possible with the so called portable app or portable version of the software. they do not write in registry and usually portable apps are contained within their folder (so they won't write all over my documents and other places). in short they do not mess with the system and do all in their folder. because they do not mess with system files, they do not need administration rights to install (there is no install actually, just unpacking).

back to linux - these are likely binaries. kind of like exe files. they can be updated form within the application if developers provided such method otherwise to update them is to overwrite them with newer version. i suggest you create a folder for such software in your /home and just add them there. 

**Appimage **is the portable format for linux.
from wikipedia:
> AppImage does not install the application in the traditional Linux sense. Instead of putting the application's various files in the distro's appropriate places in the file system, the AppImage file is just the application's compressed image. When it runs, the file is mounted with FUSE. This behavior is consistent with AppImage's predecessors, klik and PortableLinuxApps.


It uses one file per application. Each file is self-contained: it includes all libraries the application depends on that are not already part of the targeted base-system. An AppImage of version 1.0 is an ISO 9660 Rock Ridge file (which can be optionally zisofs compressed) containing a minimal AppDir and a tiny runtime.[4] (Version 2 may use other file system image formats like SquashFS[5][6]). An AppImage application can be added to a live CD by adding only one file to the live CD.


AppImage files are simpler than installing an application. No extraction tools are needed, nor is it necessary to modify the operating system or user environment. Regular users on the common Linux distributions can download it, make it executable, and run it.


Station seems most recommended as alternative on alternative-to website, while Rambox is also graded well. but there are a bunch of other applications out there. i am not using any of these, so hard to say what you need.

Rambox is used in Oracle, Cannonical...Station is used by Dropbox, Linkedin, Airbnd, Uber...

---

