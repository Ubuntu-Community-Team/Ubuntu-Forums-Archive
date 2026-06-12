---
title: "New to *nix, setting up small server, slowly depressing..."
date: 2008-10-09
forum: New to Ubuntu
---

### Post by technosinner on 2008-10-09
Hello world!

This is my first post and I won't hold back!  I'm a total noob to Linux and obviously Ubuntu as well.  I did a lot of fiddling around with kubuntu (which I didn't like) and Mint (which I like better) but the whole point of me using Linux is to set up a file server that will double as a test server for web.

At first I tried ubuntu server but command line was a little ambitious... so I have Ubuntu desktop (AMD64) and it's working very well.  I got the user part down pat I think, but I get really confused with Apache.

I tried looking for help in the docs and here but it's a little daunting.  So my question is: is there an EASY tut where I can get help getting the basics of apache?  I use apache servers with my web provider but since it's already all set up when I get there I don't know how to get it going.

For one, I have a hard time finding all the files and which folders do what - found some conf files int /etc/... but I thought apache was loading from /usr/... Also it seems I have to log into root to change files in /var/www/... that's a big no-no unless I missed a class or something...? Anywhoo you can see I have a lot to learn!

Anyway, any help would be really appreciated. Thanks!

ts

---

### Post by LowSky on 2008-10-09
Well just so you know you Ubuntu server can have a GUI, all you need to to is install it and its easy
here is the command
```
sudo apt-get intall ubuntu-desktop-
```

this page might help with apache
[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

---

### Post by jerome1232 on 2008-10-09
[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

here's a little guide to move the defualt directory to something in your /home, you don't need to be loggin in as root to edit html pages ;)

---

### Post by hyper_ch on 2008-10-09
[http://www.howtoforge.com](http://www.howtoforge.com) --> search for the perfect server howtos there.

---

### Post by bodhi.zazen on 2008-10-09
There are a number of resources available.

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

Basically , for the most part you will be editing text files. I suggest you start with nano (as a text editor).

I am not really sure how installing "ubuntu-desktop" helps much as you will not use the vast majority of applications that are installed and in the end you are still editing text files.

I think more useful skills are :

1. Learning to remote admin over ssh :

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

2. Learn to user screen.

3. If you want a gui tool, take a look at something like webmin.

---

### Post by technosinner on 2008-10-09
Wow... I don't know how to thank you guys!  I never had such quick replies in any support forums before! This place rocks!!!

As for desktop vs. server, like I said it's because I didn't know there could be a graphical interface for it (thanks LowSky!).  However now I'm all set up and going.  Would there really be any clear cut advantage to switch to server?  

We're talking file server for 2-3 workstations, a web server that will probably not see the outside of my LAN and maybe, if I feel comfortable a VPN with OpenVPN.

Thank you again
ts

---

