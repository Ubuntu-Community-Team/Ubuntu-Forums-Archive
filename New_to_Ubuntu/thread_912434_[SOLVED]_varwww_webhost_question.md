---
title: "[SOLVED] var/www/ webhost question"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by zuber786 on 2008-09-06
Hi
I think this is the right place to this this question

I am hosting website on ubuntu
this is my setup on router
I have DELL XP Ethernet Connected
Laptop Wireless
another desktop UBUNTU ONLY (hosting website)

on UBUNTU for website 
I have installed
Apache2
mysql
php5
phpmyadmin

now I want to install like FTP USER, meaning I can connect on my site throught ftp to upload and deleted files from my site. 
so it would be easy for me
please help me
thank you

 =D> 
[Special Thanx to **lazyart** you rock:guitar:
& Xiong Chiamiov for helping

---

### Post by tamoneya on 2008-09-06
I use vsftp on my server.  It was really easy:
[http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml](http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml)

---

### Post by zuber786 on 2008-09-06
I don't know 
I tired it but it doesn't seems to work
it doesn't work when I type in 
[ftp://mysiteaddress.com](ftp://mysiteaddress.com)
and this vsftpd didn't even have any option to create user name and password or anything
plz help
ty

**edited 
by the way the vsftp file is in etc/ 
not in /var/www/

---

### Post by zuber786 on 2008-09-06
can some one please help me

---

### Post by lazyart on 2008-09-06
If you're trying to ftp to your site from within your home network (the web server in at home with you), use the lan address instead of the site name... likely 192.168.x.x.

---

### Post by firefly2442 on 2008-09-07
Here's how I got vsftpd installed and working:

```
sudo apt-get install vsftpd
```

Edit /etc/vsftpd.conf

This will allow you to login as your username
```
local_enable=YES
```

This will allow you to write to your directory.
```
write_enable=YES
```

There's a pretty good/simple tutorial here:

[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)

Good luck. :)

---

### Post by zuber786 on 2008-09-07
I tired it but it doesn't work 
I removed # from front of all of the commands
when I go to ftp.mysite.com it doesn't work

---

### Post by lazyart on 2008-09-07
What is the IP address of your web server?  Did you try to FTP to that instead of mysite.com?

---

### Post by zuber786 on 2008-09-07
nope I just tired the ip address even with port 80, it is through router
&
even [ftp://192.168.x.x](ftp://192.168.x.x) doesn't work

---

### Post by lazyart on 2008-09-07
From the web server, type```
telnet localhost 21
```It should give you some info about your machine and the FTP application you're running.  That will tell us if the server is even listening (type exit to get out of telnet).
If it is listening, type```
ifconfig eth0
```and find your server's ip address next to "inet addr:"
Now, go to another machine and type```
telnet #.#.#.# 21
```substituting the ip address of the sever for #.#.#.#
You should get the same response from that command as you did when you ran it on the server itself.  Post output when you reply.

---

### Post by zuber786 on 2008-09-07
I typed 

> telnet localhost 21

it gave me this error

> telnet: Unable to connect to remote host: Connection refused


I tired on my other XP LAPTOP also
gave me this error
> Connecting To localhost...Could not open connection to the host, on port 21: Con
nect failed


---

### Post by lazyart on 2008-09-07
sounds like ftp isn't running on the server.  On the server, try```
ps -A | grep ftp
```That will tell you what processes are running on the server with 'ftp' in their name.

---

### Post by zuber786 on 2008-09-07
I tired it but it doesn't show anything

---

### Post by Xiong Chiamiov on 2008-09-07
> **zuber786 said:**
> I tired it but it doesn't show anything
That means no processes are running with 'ftp' in the name.

I believe [this]("http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html") is the guide I used setting up ftp on my server.

---

### Post by zuber786 on 2008-09-08
I have question,
I made dumb mistake
I just realise about my port 21 not been open it was set by me in my router. 
I added FTP OPTION and opened port 21 in the Virtual Servers in my router.

now it is letting me login as ftp, but only through my ip address, but it doesn't allow me to use ftp on my domain name. is there a way I can do that?

---

### Post by lazyart on 2008-09-08
It doesn't matter if the port is open on the router because you are accessing it INSIDE the network.  And since you are INSIDE the network you have to address the server by ip address.

To access it by domain name you have to be outside your network.  Go to a friend's house and try to log in by domain name.

---

### Post by zuber786 on 2008-09-08
kool thank you for all your help 
my problem is solved, 
another question is when I login to my ftp server, it does the my whole pc dir intead

---

