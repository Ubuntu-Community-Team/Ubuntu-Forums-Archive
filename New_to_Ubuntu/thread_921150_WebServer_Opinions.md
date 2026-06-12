---
title: "WebServer Opinions"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by jbrevik on 2008-09-15
I was thinking of building a web server for development/personal use and I wanted to know the opinion of some who have installed and configured a web server for personal use.

I've seen posts on creating LAMP, XAMMP, nginx webservers but unsure of which ones to install and which offer more config management tools. I also would like to know a good CMS to use with my newly built web server.

Any Ideas.....:confused:

---

### Post by sipickles on 2008-10-10
I've just built two web servers.

One is just a HTTP server, using Ubuntu Intrepid Server Beta. I installed LAMP and OpenSSH from the Server setup GUI.

The other is a development machine. I installed Ubuntu Hardy Server LTS then added gnome-core to get a desktop without all the games and office apps.

Both are headless (no keyboard or monitor). The HTTP server is controlled via the command line using SSH, and the Dev server is controlled through the awesome Nomachine NX remote desktop solution (goodbye VNC).

Both installations were very smooth on the whole. Be sure to assign static IP addresses to the server(s).

hth

Si

---

### Post by jbrevik on 2008-10-17
Since I only have one machine to work with, I went ahead and installed xampp. I mainly use it for torrentflux. The installation was smooth!!

---

