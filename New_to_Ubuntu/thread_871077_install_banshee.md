---
title: "install banshee"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-26
I can't figure out how to install banshee.  I downloaded the tar ball and unpacked it but that is as far as I have gotten.

Any suggestions?

---

### Post by appi2012 on 2008-07-26
type this in terminal:
```
sudo apt-get install banshee
```

Installing software in linux is different than installing software in windows. Instead of download a hopefully legitimate exe, in ubuntu, you go to applications -> Add/Remove. That contains a list of software that ubuntu supports and software that the community supports. Another advantage is that this way allows one applications (update manager) to install updates for all the applications that you have installed

---

### Post by SunnyRabbiera on 2008-07-26
right, installing applications in ubuntu is not like in windows where you download stuff from site a, b or c.
If you are unsure about installing stuff use this guide:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

And also keep in mind that latest doesnt always mean greatest.

---

### Post by BGFG on 2008-07-26
I've also seen it in Applications>>add-remove...

---

### Post by gjoellee on 2008-07-26
the easiest way to install additional software is by downloading Ultamatix from this link: [http://linux.softpedia.com/progDownload/Ultamatix-Download-39892.html](http://linux.softpedia.com/progDownload/Ultamatix-Download-39892.html) (now i would recommand to get Ultamatix anyway!)

Using synaptec or Add/Remove programs (Show: All available applications)
you will be able to find Banshee, all those ways as well as very much other software for Ubuntu

---

### Post by SunnyRabbiera on 2008-07-26
there is also get deb too.

---

### Post by wu-stix on 2008-07-29
I don't think any of the repliers understand the question buddy is asking.  The version of banshee available on the add/remove listing is version 0.13.2.  From the website they have a new version 1.0.  I have downloaded the new version and followed the install files but after you do the ./configure it says error; c compiler can't create executables.  When you try to do the next step make it says no target specified and no make file found.

---

### Post by b0b138 on 2008-07-29
Add ```
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
``` to sources.list 

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

:)

---

### Post by Vadi on 2008-07-31
Banshee instructions for Ubuntu are available from their website: [http://banshee-project.org/download/#ubuntu](http://banshee-project.org/download/#ubuntu)

Just a note - do not use ultamatix.

Because a) it's nothing special. All games are available from applications - add/remove, or getdeb.net, and b) it can break your computer, badly ([link]("http://www.geekosophical.net/?p=186")).

What the application claims to do is nothing special since all that done is already, and it is very, very sloppily coded.

---

