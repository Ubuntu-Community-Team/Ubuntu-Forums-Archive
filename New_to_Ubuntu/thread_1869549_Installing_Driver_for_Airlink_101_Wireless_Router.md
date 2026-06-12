---
title: "Installing Driver for Airlink 101 Wireless Router"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by thuja.plicata on 2011-10-25
I have just downloaded the driver for my new Airlink 101 Wireless N 150 Router. I have no idea how to install it from the downloaded zip file. Please assist if you can!:confused: Thanks!

---

### Post by cariboo on 2011-10-26
You don't need a driver for a router, you should be able to access the management functions via http/https eg:

```
http://<router_ip_address>
```

Checking Airlink documentation the default ip address is:

> 192.168.1.1

so to access the router management interface the command would be:

```
http://192.168.1.1
```

The default password and user name is **admin**

See the documentation here:

[http://www.airlink101.com/support/index.php?cmd=knowledgebase&_a=viewarticle&id=43](http://www.airlink101.com/support/index.php?cmd=knowledgebase&_a=viewarticle&id=43)

---

### Post by thuja.plicata on 2011-10-26
When I enter that address, I get a "problem loading page" message. The router came with an installation CD which I can't use because I have an Acer netbook. So I was trying to figure out if I could install it via the internet. I have looked at the Airlink site, and for my router model (AR570W) the IP address is similar, 192.168.2.1, but it doesn't work either. What am I  missing?

Thanks for your help.

---

### Post by plucky on 2011-10-26
> **thuja.plicata said:**
> When I enter that address, I get a "problem loading page" message. The router came with an installation CD which I can't use because I have an Acer netbook. So I was trying to figure out if I could install it via the internet. I have looked at the Airlink site, and for my router model (AR570W) the IP address is similar, 192.168.2.1, but it doesn't work either. What am I  missing?

Thanks for your help.

Connect the wired port with a cable and try again.It is likely the wireless portion of the router is turned off,is the reason you are getting the "problem loading page" message.

Once you have logged into the router,you can set up the internet connection and turn on the wireless with password protection.

Good Luck

---

### Post by thuja.plicata on 2011-10-26
Thanks! This morning the IP address worked. Now I just have to see if I can set it up properly. Appreciate the help and hope I don't have to write about this particular issue again ^_^

---

