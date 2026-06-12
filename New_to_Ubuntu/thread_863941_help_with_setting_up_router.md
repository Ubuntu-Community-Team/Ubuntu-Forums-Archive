---
title: "help with setting up router"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-07-19
alright well I just reinstalled ubuntu onto my computer. and I just installed  LAMP. I need to fix my router so that when you put in my ip address it will forward you to my page. How do I do it? I don't remember. I'm using a netgear router.

thanks you for reading! :)

---

### Post by pavel989 on 2008-07-19
go to 192.168.1.1 or w/e ur routers default IP is. (its typically what i said)

---

### Post by RadiationHazard on 2008-07-19
alright. now that I'm logged in how do I forward the port?

---

### Post by pavel989 on 2008-07-19
well, find wherever it says port forwarding.
if you gimme ur router model #, i can give u better directions

---

### Post by bab1 on 2008-07-19
See:[http://portforward.com/]("http://portforward.com/")

---

### Post by superprash2003 on 2008-07-19
its normally under virtual server

---

### Post by RadiationHazard on 2008-07-19
ok this is a screen shot of what my port forwarding section looks like. what do I do to get it to show my web page I'm making whenever my ip gets put in?

---

### Post by jerome1232 on 2008-07-19
That looks right as long as 192.168.1.4 is your server (btw I have that router)

One thing though alot of isp's block incoming connections on port 80 so if it doesn't work you may want to tell apache to listen to port 81 or 8080, and forward that port and retest

---

### Post by RadiationHazard on 2008-07-19
I can't get this thing to freaking work!!! :(
 
and I've had it several times before. that's what makes me the most mad.

---

### Post by pavel989 on 2008-07-20
whats ur isp?

---

### Post by RadiationHazard on 2008-07-20
roadrunner. and my ip is no where on there. where am I supposed to put that? ha.

---

### Post by pavel989 on 2008-07-20
no ur iSp, internet service provider. comcast, verizon....

---

### Post by jerome1232 on 2008-07-20
> **RadiationHazard said:**
> roadrunner. and my ip is no where on there. where am I supposed to put that? ha.

You can reach the web page in you home LAN so we know apache is set up correctly, from the screenshot you posted your router is set up right. Just make sure you are typing your public ip in when trying to reach the server outside of your lan. The public ip will show up if you goto the site I link lower down

If you just have regular internet through roadrunner (no static ips or a buisness version) they block port 80, one way to tell is goto [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and slap in port 80, it'll come back invisble if they filter the port.

edit: on that site it will just time out, some other port checkers say closed/invisble. This one doesn't specify.

---

### Post by RadiationHazard on 2008-07-20
it just timed out. I didn't do anything but go back to that page.

---

### Post by jerome1232 on 2008-07-20
That means your ISP blocks incoming connections on port 80 you will have to use another port, 81 and 8080 are common alternative ports.

There are services such as dynDNS and noIp that can help you with getting around that. With dynDNS you can create a domain name with a webhop, so someone types [http://my.web.site](http://my.web.site) and dynDNS will redirct traffic to [http://my.realweb.site:81](http://my.realweb.site:81)

It's very handy, it can even mask the address so they have no idea the redirect ever happened.

---

### Post by RadiationHazard on 2008-07-20
how do you set up apache to a different port? and do you really go site.com.site:81 as the WebHop?

I'm so confused right now! can you please go into full detail with screen shots if you don't mind?

---

### Post by jerome1232 on 2008-07-20
> **RadiationHazard said:**
> how do you set up apache to a different port? and do you really go site.com.site:81 as the WebHop?

I'm so confused right now! can you please go into full detail with screen shots if you don't mind?

first things first lets config apache.
I'll do this command line only it's easier to show.

to edit apache's configuration

```
sudo nano /etc/apache2/ports.conf
```
or if you are in a graphical enviroment you can do this
```
gksudo gedit /etc/apache2/ports.conf
```

either way you should now be in a text editor that has some text in it.

At the beginning you should see this:
```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```
change it to this (change Listen to 81)
```
Listen 81

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

save the file (if using nano hit ctrl+x, type y and hit enter)

now restart apache

```
sudo /etc/init.d/apache restart
```

now to test, open your browser (on same machine) and goto [http://localhost:81](http://localhost:81)  (the colon is how you specify a port)

it should work! post back with results, if something goes wrong please post the output of you terminal with what went wrong or with what you have a question on.

You will also have to set your router to forward to port 81 instead of 80. But that won't matter for right now. Based on earlier posts I assume you know how to do that now.

---

