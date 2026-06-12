---
title: "couple questions re: eclipse -- servlet/jsp programming"
date: 2010-10-13
forum: Programming Talk
---

### Post by badperson on 2010-10-13
Hi,
I have two kind of basic questions I can't find the answer to...

[LIST=1]
[*]When I export a .war file to my tomcat/webapps folder, the previous file can only be deleted with root permission. So I have to go in and delete the old .war file before the new one becomes active. Do you know how to set the permissions so I don't need to do that?
[*]My project currently is divided in two eclipse projects; the core app and the web tier. The core app jar is in the class path of the web tier, and any time I make a little change I have to export the jar again...anyway to get around that? (I should have started them as a single project, Iknow....)
[/LIST]

thanks, 
bp

---

### Post by r-senior on 2010-10-14
1. For development, I usually download Tomcat from the Apache web site and unzip it in my home directory (under $HOME/Software but your choice). You can then set it up as a server in Eclipse and let Eclipse control it. 

Apart from making deployment a simple matter of running the web project (it will deploy the WAR then open a browser window to run it), it also makes things easier if you need to restart in debug mode.

You will probably need to edit the tomcat-users.xml to set up an admin user and set the username/password in the server config in Eclipse. See screenshots.

*$HOME/Software/apache-tomcat-6.0.26/conf/tomcat-users.xml*
```

<tomcat-users>
    <user password="manager" roles="manager,admin" username="admin"/>
</tomcat-users>

```

The install of Tomcat from the repos is really more suited for use as a production server. Eclipse doesn't expect it to be split across filesystems the way it is done according to the filesystem hierarchy standards.

Same comments apply to Netbeans.

2. IMO you are absolutely right to split the application into a core JAR and a separate web application. If you want to write a desktop application, or a web service, that uses the same core, you can do so easily.

If your development is very iterative, you can just add a dependent project on the build path rather than rebuilding a JAR file each time. See final screenshot.

---

