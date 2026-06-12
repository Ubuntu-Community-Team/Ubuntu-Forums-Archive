---
title: "Can´t save index.html file"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by MikeAmin on 2008-11-24
Hi, I´ve installed Ubuntu Server edition with GUI on my old laptop, and I´m playing around with it.

I found the var/www folder where the index.html is. I opened the index.html and edited the text to ¨my web site¨, but when I go to close and save it, I get the following message:

> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

How do I give myself permission to edit this file?

Also, a few more questions:

what webpage editor would you recommend I use with Ubuntu?

how do I check if my webpage can be seen on the internet? How do I find the IP address where the webpage would be located at?

Your help would be greatly appreciated

---

### Post by porchrat on 2008-11-24
> **MikeAmin said:**
> Hi, I´ve installed Ubuntu Server edition with GUI on my old laptop, and I´m playing around with it.

I found the var/www folder where the index.html is. I opened the index.html and edited the text to ¨my web site¨, but when I go to close and save it, I get the following message:



How do I give myself permission to edit this file?

When you edit it use this command instead to give yourself the needed permissions:

```
gksudo gedit index.html
```

> how do I check if my webpage can be seen on the internet? How do I find the IP address where the webpage would be located at?

That all depends on how your webpage is hosted.  Do you host it on your own machine or does your ISP host it for you?

---

### Post by MikeAmin on 2008-11-24
> When you edit it use this command instead to give yourself the needed permissions:

Thank you. It works, and I was able to edit it, 

*Edit, This command opened the .html file in /home/ubuntu  I was able to open the .html file in /var/www with gksudo gedit /var/www/index.html

> 
That all depends on how your webpage is hosted. Do you host it on your own machine or does your ISP host it for you? 

I just recently installed the ubuntu OS, so nothing has been setup. I just want to check if the html page can be seen on the internet. I´m wondering what IP address someone else would have to enter to get to it. Í´d like to eventually host a small website myself.

---

### Post by Thirtysixway on 2008-11-24
You can change the owner of the folder/files

sudo chown -R username:group /var/www

That way you don't need to use sudo everytime you want to edit a file.

---

### Post by MikeAmin on 2008-11-24
What username should I change it to? I tried to change it to ´group´ but I got the following:

chown: invalid user: `username:group'

---

### Post by jrib on 2008-11-24
> **MikeAmin said:**
> What username should I change it to? I tried to change it to ´group´ but I got the following:

chown: invalid user: `username:group'

you should create a new group like www-editors for example
```
sudo addgroup www-editors
```

---

### Post by MikeAmin on 2008-11-24
ok, I added a new group www-editor, but when I tried to change the owner of the folder I got this:

ubuntu@ubuntu:~$ sudo chown -R username:www-editor /var/www
chown: invalid user: `username:www-editor'

---

### Post by jrib on 2008-11-24
you need to pick a user to own the files and put it in place of "username"

---

### Post by DGortze380 on 2008-11-24
On a default install, if you're site is pointed to by a static address and DNS, you can access it via loopback 127.0.0.1

---

### Post by halitech on 2008-11-24
the others are handling the permissions issue for you so I'll stay out of that :)

as far as your IP address, are you on dialup or highspeed, do you have a router or no? if you have a router, go to [http://ipchicken.com](http://ipchicken.com) , [http://whatismyip.com](http://whatismyip.com) or log into the router and check there.

---

### Post by bodhi.zazen on 2008-11-24
Permissions are important on Ubuntu / Linux.

[uhelp]community/FilePermissions[/uhelp]

apache runs as www-data, so add your user to the www-data:

sudo usermod -G www-data <user>

where user = you log in name.

If needed, chown the file to root.www-data

sudo chown root.www-data /var/www/index.html

---

### Post by DGortze380 on 2008-11-24
> **halitech said:**
> the others are handling the permissions issue for you so I'll stay out of that :)

as far as your IP address, are you on dialup or highspeed, do you have a router or no? if you have a router, go to [http://ipchicken.com](http://ipchicken.com) , [http://whatismyip.com](http://whatismyip.com) or log into the router and check there.

That will only work if you sent port forwarding on the router. Loopback is easier and more secure for practicing/testing.



To do it the other way. Find your EXTERNAL IP at [www.whatsmyip.com](www.whatsmyip.com). log in to your router via the routers INTERNAL IP. Set port forwarding for http on port 80 to your servers INTERNAL IP.

This is rather dangerous and makes you decently vulnerable to attacks.

---

### Post by halitech on 2008-11-24
> **DGortze380 said:**
> That will only work if you sent port forwarding on the router. Loopback is easier and more secure for practicing/testing.


the OP was asking how to find his IP address, thats all I was addressing as they asked this question:
> I´m wondering what IP address someone else would have to enter to get to it. 
but without knowing if they have a router or any other details about their connection, I asked another question to get an answer and then gave some general info.

---

### Post by jrib on 2008-11-24
> **bodhi.zazen said:**
> 
apache runs as www-data, so add your user to the www-data:

sudo usermod -G www-data <user>

where user = you log in name.

If needed, chown the file to root.www-data

sudo chown root.www-data /var/www/index.html

www-data should not own files that apache does not need to write to.  It is better practice to create a new group.

---

### Post by MikeAmin on 2008-11-25
Thanks for the feedback.I was able to give permission to my root user to access the index.html file.

Also, I successfully accessed my site via 127.0.0.1 and I was able to find my external IP at [http://whatismyip.com/](http://whatismyip.com/). I tried accessing my site via my external IP, but it doesn´t access it. I´m assuming it´s because I´m using a router and I need to forward  port 80 to my server&#347; internal IP.

DGortze380,

> Find your EXTERNAL IP at [www.whatsmyip.com](www.whatsmyip.com). log in to your router via the routers INTERNAL IP. Set port forwarding for http on port 80 to your servers INTERNAL IP.

This is rather dangerous and makes you decently vulnerable to attacks. 

Thanks. Is there any way to do it that&#347; secure or is that unavoidable if I want my site accessible from the web?

---

### Post by halitech on 2008-11-25
opening just port 80 (as long as your ISP doesn't block incoming traffic on it) won't be that much of a problem for you. I would advise against putting your system in the DMZ though as that opens everything up. If you want to allow traffic from outside your lan then you will have to open the port.

---

### Post by DGortze380 on 2008-11-25
> **MikeAmin said:**
> Thanks for the feedback.I was able to give permission to my root user to access the index.html file.

Also, I successfully accessed my site via 127.0.0.1 and I was able to find my external IP at [http://whatismyip.com/](http://whatismyip.com/). I tried accessing my site via my external IP, but it doesn´t access it. I´m assuming it´s because I´m using a router and I need to forward  port 80 to my server&#347; internal IP.

DGortze380,



Thanks. Is there any way to do it that&#347; secure or is that unavoidable if I want my site accessible from the web?

Running a server accessible via the web is inherently insecure. It's not particular to any OS, or person, or application... if you can access it legitimately from the internet, people can hack it. Whether or not they ever will, can't say... that's the risk you take.

Monitor your logs. Keep as LITTLE personal information on the machine as possible. 

I would definitely advise forwarding http traffic on port 80, over placing the whole machine in a dmz. 

Unless of course there is no personal information on the server, and there is personal information on the other machines on the network. Then a DMZ is a good idea.

---

