---
title: "How to use JSPs with Apache2"
date: 2011-12-29
forum: Programming Talk
---

### Post by PaulM1985 on 2011-12-29
Hi

On my server I have apache2 installed.  I wondered if anyone has any info on how to get it to run JSPs and Java Servlets.

I read somewhere that I need to get Apache Tomcat and a tomcat connector, which I downloaded from here ([http://tomcat.apache.org/download-70.cgi](http://tomcat.apache.org/download-70.cgi)) and here ([http://tomcat.apache.org/download-connectors.cgi](http://tomcat.apache.org/download-connectors.cgi)) respectively.

Has anyone got any info?  What do I need to do with these?

Paul

---

### Post by r-senior on 2011-12-29
I did a blog article on how to do this, but it's a couple of versions old now. Nevertheless, the principle should be the same:

[http://explodingjava.blogspot.com/2010/03/configuring-apache-and-tomcat-on-ubuntu.html](http://explodingjava.blogspot.com/2010/03/configuring-apache-and-tomcat-on-ubuntu.html)

---

### Post by PaulM1985 on 2011-12-29
Ok, I followed that, but it doesn't seem to have worked....

Is there any reason why:
1 - uninstalling apache2
2 - converting tomcat to run on port 80 instead of 8080

Would be a bad idea?

Paul

---

### Post by r-senior on 2011-12-29
If the bulk of the content is dynamic, i.e. JSP/servlet, and user volumes are relatively small, there's no problem serving everything off Tomcat.

The main reason for sitting Tomcat behind Apache is if you have a large amount of traditional web content to serve to a high volume of users, you want to use other Apache modules as part of the site or you want to have a stable front-end to a cluster of Tomcat instances.

Did you figure out how to edit [FONT="Courier New"]server.xml[/FONT] to make Tomcat listen on 80?

What didn't work, out of interest? Did you download everything from the Ubuntu repos?

---

### Post by PaulM1985 on 2011-12-29
I assumed that I would only have to change the:
```

<Connector port="8080" protocol=....

```
section to be 80 rather than 8080.  Is this correct?

I don't aim for this to be a very large website.  I am researching AI and I am looking to make a facebook web app.  Facebook would redirect to a page on my website which contained a poker game in the form of an applet no more than 2MB in size.  On finishing the game, the applet would post the information to a servlet which would save the info in a MySQL database so I can analyse game information.

I don't really know why it doesn't work.  Downloads of tomcat and libapache2-mod-jk2 (now libapache2-mod-jk since libapache2-mod-jk2 doesn't seem to exist) were from repos and seemed to work ok.  There was some warning to do with certificates, but I also got the warning when installing openjdk, so I didn't think it was a big problem.  Apache2 and Tomcat both seem to work independently (port 80 handles normal .html and 8080 will handle .jsp when the files are in the appropriate places), but when I put my .jsp files in the area for Apache2, the files aren't handled correctly, it displays the raw .JSP code.

Would Tomcat on it's own be suited for my project?  I guess in an ideal world Apache2 would handle the applet download and Tomcat would handle the database stuff.  Any ideas on why the two aren't playing together?

Paul

---

### Post by 1clue on 2011-12-29
If you run as port 80 then the tomcat will need to be started as root.  Better to set up a rule in your firewall to forward incoming port 80 requests to 8080.

---

### Post by PaulM1985 on 2011-12-29
One thing I didn't do was:
```

JkWorkersFile /etc/apache2/workers.properties
JkShmFile     /var/log/apache2/mod_jk.shm
JkLogFile     /var/log/apache2/mod_jk.log
JkLogLevel    error
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
JkMount /MyWebApplication/* tomcat

```

I have now added this to my apache2.conf.

I already made the changes to /etc/apache2/sites-available/default and /etc/apache2/workers.properties as you suggested.

I put my files in /MyWebApplication/web/ and when I go to [http://address/web](http://address/web) I get a "files not found" message.

Paul

---

### Post by PaulM1985 on 2011-12-29
IT WORKS!!!

I didn't realise that the /MyWebApplication/* was the area in tomcat where my files should be.  I was initially thinking that was the exact path, or they should be in /var/www/MyWebApplication.

I have put my files in the correct area of tomcat and it is now working.

For people in future, the line:
JkMount /MyWebApplication/* tomcat
means that any request going to [http://youraddress/MyWebApplication/](http://youraddress/MyWebApplication/) will be forwarded on to tomcat rather than dealt with by apache2.

Thanks for helping.

Paul

---

