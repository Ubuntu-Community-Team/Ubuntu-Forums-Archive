---
title: "Can`t see public_html (Joomla install page)"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-04
I have been following and doing steps from this blog: [http://www.parcival.org/2006/07/14/howto-install-joomla-on-your-very-own-ubuntu-server/](http://www.parcival.org/2006/07/14/howto-install-joomla-on-your-very-own-ubuntu-server/) , so now have a new directory in the root or home directory) called  public_html, into which I have unzipped the downloaded Joomla 1.5 installation package. Acccording to the blog, if I now enter:  [http://192.168.0.1/~user](http://192.168.0.1/~user) name (mine of course), and I have tried that ip, as well as my own router`s ip (192.168.1.1) I am supposed to see the installation page to install Joomla...but a page never loads when I do that, nothing happens.  I do have Apache installed and enabled (even have wedmin, so I can check). I am just a noob going step by step, and googling and following advice, so I know I`ve done something wrong lol.  The user name I put there was the user name I use at the command line (terminal) and I also log into the computer with it.  In my router also, I entered the Dyndns account info (user name, host name). If I just enter this: [http://192.168.1.100/](http://192.168.1.100/) I get this:  Apache/2.2.8 (Ubuntu) Server at 192.168.1.100 Port 80, (that`s not my router`s ip, but the ip I used in port forwarding for port 80 used for www). But if I tack the `username` at the end, as suggested, I get:  The requested URL /~bosslady was not found on this server. What on earth could I be doing wrong :confused: I really want to install Joomla!  I would love any advice, thanks.

---

### Post by dracayr on 2008-11-04
try to enter 127.0.0.1/~user

dracayr

---

### Post by Coreigh on 2008-11-04
You need to define public_html as a available site in your /etc/apache2/sites-available/default. Essentially you need to create a virtual host. I am sorry I do not have any links to offer. But there is some documentation on the Joomla website [http://docs.joomla.org/]("http://docs.joomla.org/") and at [Apache.org]("http://httpd.apache.org/docs/").

Also you could use the default html folder (/var/www ). Unless there is a specific reason that the tutorial suggests creating public_html.

---

### Post by Lakeside on 2008-11-04
Thanks for the suggestions. When I try 127...user (my username of course) I get: The requested URL /~b****y was not found on this server.
From a lot that I`ve read, most people are putting joomla in var www(forward key won`t work right now) So I`m wondering how exactly I do that.  Do I go to var www and mkdir Joomla, because it won`t let me do that.  Or do I create a folder called joomla, that all the rared files from the download get unzipped into, and then move that into var www.  I`m just not sure. thanks

---

### Post by Lakeside on 2008-11-04
thanks for the help and suggestions, I`m going to create a new thread though, as the issue has changed slightly. thanks

---

