---
title: "Home web server, am I missing something?"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2012-04-15
So I have installed Cherokee, PHP, MySQL, PHPMYADMIN and a heap of other stuff I need all on my 12.04 beta 2 x64 box.

The webserver is on internal ip 192.168.1.2 I also have the public static ip of xx.xx.xx.xx

Now when I go to the public IP in my browser I am asked for my routers user name and password and am not presented with my website? instead all I get is the routers panel.

Any ideas?

---

### Post by roccity1 on 2012-04-15
What do you get when you type [http://serveripaddress/info.php](http://serveripaddress/info.php) (where serveripaddress is your own server ip address) in a browser

*side note*

Do you have the port for your server open? like port 80.

Have found some *Wizards* that will help to setup some basic functions of your server like Wordpress and PhP

---

### Post by lisati on 2012-04-15
Have you configured port forwarding on your router to redirect port 80 to your server?

---

### Post by terrykiwi83 on 2012-04-15
thanks for the reply, when I go to my ip and that file I get file not found. 

And yep I have port 80 open, Cherokee is listening on it. And the Linux firewall isn't opening. I have also set it as open on the router. Also I have set the webserver as the DMZ host

Any more suggestions

---

### Post by terrykiwi83 on 2012-04-15
Some images of settings I have changed.

---

