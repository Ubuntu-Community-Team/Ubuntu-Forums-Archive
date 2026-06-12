---
title: "Ubuntu as a Testing Server"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by jamal2 on 2014-03-21
Hello! I am in the process of designing a website for a friend, however the developers of the CMS I am trying to utilize say that it only works on a Linux/Unix server with several modules (LAMEmp3, Libogg + Libvorbis, FFMpeg-PHP, among others). I am normally a Windoze user, but I have to complete this project. Any help on the BEST way to accomplish my goal would be quite helpful.
Thanks in advance
-J

---

### Post by SeijiSensei on 2014-03-22
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The libraries like libogg will probably be included as dependencies if you install ffmpeg or mplayer.

This is the first I've heard of an ffmpeg module for PHP; I don't know if it is in the repositories, but I found the home page for the project [here]("http://sourceforge.net/projects/ffmpeg-php/").  Be warned though that development ended on this project in 2008, so it's compatibility with modern releases of ffmpeg and PHP is not assured.

---

