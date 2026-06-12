---
title: "Linux, Apache, Tomcat, MySQL, PHPmyAdmin, Webmin"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-21
I want to install Linux, Apache, Tomcat, MySQL, PHPmyAdmin, Webmin on my Ubuntu 8.04LTS fully configured, such that all i have to do is to open localhost, localhost/phpmyadmin, localhost/webmin and etc an everything opens up....

---

### Post by Thirtysixway on 2008-05-21
[http://ubuntuguide.org](http://ubuntuguide.org)

This website has a very useful guide where you can simply click on what you need and it gives you the commands.  The Gutsy page works for Hardy so don't worry ;)

---

### Post by AndrewTheArt on 2008-05-21
If you are willing to wait a few days (probably until Saturday) I'm going to complete the revised version of my Ubuntu 8.04 LAMP Installation Guide, which goes through the process of setting up MySQL, PHP, Apache, Tomcat, and FTP step by step.

---

### Post by shoaibi on 2008-05-22
okay, i am waiting

---

### Post by AndrewTheArt on 2008-05-24
Might be late tonight when I release it, or Sunday even. Having some issues. I don't release crappy beta products, unlike other monopolistic companies we know :P

---

### Post by shoaibi on 2008-05-24
good :P...

---

### Post by PriceChild on 2008-05-24
Or.... you could use the official ubuntu documentation: [uwiki]Apache[/uwiki]

ie```
sudo tasksel install lamp-server
```Then
```
sudo apt-get install phpmyadmin
```

---

### Post by AndrewTheArt on 2008-05-25
Yea, go ahead and follow those instructions if you only want PHP+Apache. My guide will also cover Tomcat and some advanced configuration of it. 

(Also, the webmin package doesen't exist in any repository I have enabled. What's up with that?)

---

### Post by pearjam on 2008-05-25
I've always had good luck with Xampp. It's at:

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

It has all the things you want except for tomcat (but that can be installed as a module I think).

---

### Post by PriceChild on 2008-05-25
> **AndrewTheArt said:**
> (Also, the webmin package doesen't exist in any repository I have enabled. What's up with that?)See the bottom of [https://wiki.ubuntu.com/EboxSpec](https://wiki.ubuntu.com/EboxSpec)

---

### Post by AndrewTheArt on 2008-05-25
Finally think I'm done - 

PDF - 

[http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf](http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf)

HTML Version here - 

[http://andrewtheart.tripod.com/linux/Ubuntu804ServerGuide.html](http://andrewtheart.tripod.com/linux/Ubuntu804ServerGuide.html)

Obviously I need to move it off Tripod, but it's temporary. Check out

[http://www.andrewsteinhome.com/linux/server/](http://www.andrewsteinhome.com/linux/server/)

in the future. Eventually that will host the guide.

---

### Post by PriceChild on 2008-05-27
> **AndrewTheArt said:**
> Finally think I'm done - 

PDF - 

[http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf](http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf)

HTML Version here - 

[http://andrewtheart.tripod.com/linux/Ubuntu804ServerGuide.html](http://andrewtheart.tripod.com/linux/Ubuntu804ServerGuide.html)

Obviously I need to move it off Tripod, but it's temporary. Check out

[http://www.andrewsteinhome.com/linux/server/](http://www.andrewsteinhome.com/linux/server/)

in the future. Eventually that will host the guide.The last two links are broken.

The recommended way of installing LAMP (rather than installing individual packages) is documented on the wiki, and by me earlier in this thread... I wonder why you put the recommended way *after* the graphical way, despite naming it such. Wouldn't it also be better to point users to that, so that you don't have to maintain your own guide separately?

sudo -i is really not recommended, nor needed to pipe with su permissions. You also don't explain that you should *really* exit that shell asap!
[URL="http://psychocats.net/ubuntu/graphicalsudo"]
gksudo should be used with graphical applications.[/URL]

Changing the apache root for tomcat instead of the other way around seems odd and nasty and could break ubuntu packages further down the line... I'm not an expert though.

Why don't you put "how to install tomcat" onto the wiki? There it would be much easier for others to find, and would allow greater peer review to improve it.

---

### Post by shoaibi on 2008-05-27
@andrew:
i followed your guide using tasksel....
now i have reached to the step where you configure proftp, just before that when i try:
[http://localhost/](http://localhost/)

it shows me list of files, but thats okay coz there is no index.html, but should it pick index.jsp like it picked in 8180?

and then if i do:
localhost/index.jsp
i get:
```

Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
Apache/2.2.8 (Ubuntu) mod_jk/1.2.25 PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch Server at localhost Port 80

```



[EDIT]:
and when i do: 
localhost/admin 
i get:
```

Tomcat's administration web application is no longer installed by default. Download and install the "admin" package to use it.

```
Plus also tell me how can i change localhost to be local.myname

---

