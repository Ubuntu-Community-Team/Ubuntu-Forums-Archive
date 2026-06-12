---
title: "docBase Apache2 Tomcat5"
date: 2006-12-05
forum: Programming Talk
---

### Post by al001 on 2006-12-05
Hi,

I have installed Tomcat5 and Apache2 on Ubuntu Edgy. Everything is fine except for when I try to load a page via [http://myHostName](http://myHostName).

I get the right result with [http://myHostName/jsp-examples](http://myHostName/jsp-examples), and [http://localhost:8080](http://localhost:8080) (the default tomcat page). In the server.xml file from the tomcat installation I have:

       <Host name="localhost" appBase="webapps"
        unpackWARs="true" autoDeploy="true">

        <Context path="" docBase="jsp-examples" debug="1"   reloadable="true"/>

        
      </Host>


which is the same setup I have on a FC5 installation and works fine. When I try to load [http://myHostName](http://myHostName) I get 

[B]Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.[/B]

However the error.log file in apache2 does not show anything, neither does catalina.out from tomcat or the mod_jk.log file.


Anyone has an idea what the problem could be?

Thanks,

Alain

---

### Post by lloyd mcclendon on 2006-12-05
i know how to do this

i'm posting this now to remind myself to answer it when i have the time.  i've got to run now

basically you have to put something in server.xml to tell tomcat to connect to apache, & then a couple lines in httpd.conf  and it should work.  when i get back i'll give you a run down

---

