---
title: "How to change specific application port"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by kamrava on 2013-08-04
[COLOR=#333333][FONT=UbuntuRegular]I would like to install apache2 but does not allow me to install it.
As you know apache using port 80. But port 80 already opened(TeamViewer Apllication use port 80).
How to change TeamViewer port ?
Any ideas would be awesome.


[/FONT][/COLOR]

---

### Post by raja.genupula on 2013-08-04
Hi

you can do that but I will help you in the apache port changing. actually apache will listen to the specific port with listen directive. so if you mention to listen certain port then it will listen from that port only. so to change that open your terminal and type as 

> sudo nano /etc/apache2/ports.conf

then in the text file opened , write a line as 

> listen 8000

then , from now on wards it will listen port 8000 only. press CTRL+X+Y to save and quit. then give a enter . 

now restart your apache with 

> sudo /etc/init.d/apache2 restart


hope that helps and if its solved your issue , then mark your thread as solved from thread tools.

---

