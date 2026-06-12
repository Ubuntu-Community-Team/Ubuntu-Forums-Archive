---
title: "i'm in need of a linux server distro"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by rhariharan.cbe on 2011-09-20
hi eveyone.. i'm an engineering student.. i am about to do my project about developing a site.. i like linux so i need a linux server distro which does support for most of the softwares like DB2 J2EE ROSE WEBSPHERE MODELER ECLIPSE LOTUS FORMS DESIGNER PORTLET FACTORY WEBSPHERE PORTAL AND TIVOLI DIRECTORY SERVER... i can write programs and i am new to web deveopment and stuff like that...so plz help me out by telling which linux sever  distro has support for softwares and which would be easy to use to host my project from my pc..i dont know much of these things so please go ease with me if i'm wrong in anything .. :)

---

### Post by CharlesA on 2011-09-20
Just run any desktop linux disto and install the services you need. Not sure if any of those programs even run on Linux.

---

### Post by haqking on 2011-09-20
Not sure about the rest but im pretty sure Tivoli DS needs Suse or Redhat.

---

### Post by Volens on 2011-09-20
I'm no expert at web dev stuff, but if you are starting out, a basic LAMP stack with Ubuntu Server Edition will suit most needs afaik.

It uses apache2 to serve HTML, PHP for server-side scripting, and gives you a database via mySQL. Most other things, jQuesry, javascript, css, are handled on the client side.

I like it because installation is fairly easy. You pretty much pop the CD in pick LAMP stack and fill in some basic info like the hostname. I have a box at home running it that I run a wordpress site off of and that I use whenever I want to work on building stuff from scratch when I'm bored.

But then again, I'm not exactly sure what you're trying to support/do. If you're referring to "eclipse" the IDE, the server doesn't necessarily support that, the files are just uploaded to the folder that apache2 is serving to users.

---

### Post by Dangertux on 2011-09-20
Honestly with that list of software I would say redhat or centOS.

---

