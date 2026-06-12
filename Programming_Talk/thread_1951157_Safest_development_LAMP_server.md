---
title: "Safest development LAMP server?"
date: 2012-04-02
forum: Programming Talk
---

### Post by underkz on 2012-04-02
Hi guys!

I'm wondering what can I do for having a development LAMP server without explosing me to any security problems.

So I install the LAMP stuff with this command:
```
sudo apt-get install lamp-server^
```

And after I edit /etc/apache2/ports.conf and I change
```
Listen 80
```
To
```
Listen 127.0.01:80
```
to make any other computers outside my network incapable of querying my server.

Is that enough or I can be exposed to some security flaws? Do you know some other things I can do?

Thank's for your time! ):P

---

### Post by CynicRus on 2012-04-02
Mm...for configure apache2 for local development, you need editing apache2.conf, /etc/apache2/sites-available/default, including needed modules with a2enmod. Of course if you do not plan to develop a project. Otherwise - By default, Apache is configured to localhost during the installation, configuration, and no longer requires. In addition to connecting the modules php, etc...

---

### Post by r-senior on 2012-04-02
How are you connecting your network to the Internet? Something like a broadband router?

If so, have you looked at the configuration of the firewall and how address translation works from the outside to your network?

There are port scanner websites that you can use to check which ports are open on your public IP address - things like ShieldsUP.

It's probably also worth having a look in the Security forum, starting with:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by dharmavir on 2012-04-02
r-senior, more important is how do you connect your development machine to the public internet?

Also you may want to give try to bitnami-lampstack. But if you're going to use ubuntu-server on production server it is always good to go with:
```
sudo tasksel install lamp-server
```
Same as what you did.

---

### Post by SeijiSensei on 2012-04-02
> **underkz said:**
> ```
Listen 127.0.0.1:80
```
Is that enough?

Yes.  If you want to be sure, try connecting with telnet to the server's public network interface like this:

```
telnet ip.of.your.server 80
```

You should get a "connection refused".  If you replace ip.of.your.server with 127.0.0.1, you should be able to connect.

---

### Post by underkz on 2012-04-02
Thank's for all your nice suggestions!

Yes I'm using a broadband router.

I now block the port with my router. My tests shows that it's closed to others.

I didn't know about bitnami-lampstack, it seems like Xampp with more features :). But I'm wondering if there's any advantage using those programs instead of using the wonderful packages of ubuntu?

---

