---
title: "trying to run a webapp on my server"
date: 2009-09-20
forum: Programming Talk
---

### Post by badperson on 2009-09-20
I got tomcat 6 installed on my server, 
so the address http://<server ip>:8080/
gives me the tomcat page, that's good. 

I created a simple test app for tomcat that I run on my ubuntu desktop (tomcat is also installed on the desktop machine) so the link:

[http://localhost:8080/EclipseServletTest/EclipseFirstSevlet](http://localhost:8080/EclipseServletTest/EclipseFirstSevlet)

gives me the proper output (note the misspelled "sevlet", whoops...)

however the link:

http://<ip address of server>:8080/EclipseServletTest/EclipseFirstSevlet

does not give me the correct output. I have the Webapp folder copied to the tomcat/webapps folder and I restarted the server...any idea what the problem might be? 
bp

---

### Post by bogdan.veringioiu on 2009-09-20
Hi.

Is there the firewall enabled??
If yes, try to enable access to port 8080. Just a thought...
Bogdan

---

### Post by Joeb454 on 2009-09-20
The firewall should only become an issue if you try to access it from your public IP - in which case port-forwarding is almost definitely required.

In your LAN however, you should be able to type something like 10.0.1.100:8080 or 192.168.1.37:8080 and access it (whatever the IP is :))

---

### Post by badperson on 2009-09-22
just to be clear...is it possible to copy a webapp folder from the tomcat/webapps folder on one machine, and copy it to the tomcat/webapps folder on another machine and have it run ok? 
bp

---

### Post by myrtle1908 on 2009-09-22
> **badperson said:**
> just to be clear...is it possible to copy a webapp folder from the tomcat/webapps folder on one machine, and copy it to the tomcat/webapps folder on another machine and have it run ok? 
bp

Yes.  You may need to re-start Tomcat (or the application in question with the Manager) so that it reloads the context etc. described by the web.xml.  You could also export your application as a WAR file using Eclipse and deploy it on the new server.  However, this is really no different to copying the application from one place to another.  After all a WAR file is basically a ZIP archive and the Manager simply explodes it into the webapps folder.

---

