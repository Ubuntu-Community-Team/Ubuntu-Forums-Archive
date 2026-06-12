---
title: "Tomcat, Apache folder and port"
date: 2007-05-17
forum: Programming Talk
---

### Post by wacind on 2007-05-17
Hi 

Im currently running Edgy. I have apache set up, and i just set up Tomcat5. Tomcat works fine on localhost:8180.
I changed the port to 80 in the server.xml file and pretty much used this tutorial for my setup [http://doc.gwos.org/index.php/Install_tomcat_5.5](http://doc.gwos.org/index.php/Install_tomcat_5.5)

However tomcat still seems to be running on 8180.

Also I would like to be able to use jsp files like regular users ( from /home/user/public_html/ ) and not have to store my files in the tomcat webapps folder. Is that possible?

Thanks
wacind

---

### Post by idn on 2007-06-10
+1 

I would also like to know how to do this, I have installed tomcat through the repos and everything is working, however I would really like to access it through apache.

---

### Post by nimrod_abing on 2007-06-11
Are you trying to setup a production server or just doing local web development and testing?

To be able to run any program that listens on the first 1024 ports, you need to run the program as root. I guess the tutorial you followed neglected to mention that. You are also running Apache as you have said. Apache makes use of port 80 by default and only one program may use a port number on an IP address. So if you are already running Apache by the time you run Tomcat, then it will also fail since Apache has already taken over port 80.

You need to do one of these:

1. Shutdown Apache.
2. Enable mod_proxy for Apache and set it up to proxy requests to port 80 to port 8081.
3. Install and configure mod_jk.

It's generally a bad idea to run programs as root so I strongly advise against running Tomcat as root for the sole purpose of having it listen on port 80.

What you can do, assuming you shutdown Apache, is continue to run Tomcat as a regular user. Then as root, create an iptables rule to redirect request to port 80 over to port 8081 where you have Tomcat listening:

```
*sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8081*
```

You can add that line to your /etc/rc.local file (before the exit 0 line) if you want that rule to be loaded on startup.

> Also I would like to be able to use jsp files like regular users ( from /home/user/public_html/ ) and not have to store my files in the tomcat webapps folder. Is that possible?See:

[http://tomcat.apache.org/tomcat-5.5-doc/config/context.html](http://tomcat.apache.org/tomcat-5.5-doc/config/context.html)

docBase attribute.

---

