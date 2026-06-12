---
title: "Java Servlets"
date: 2007-08-04
forum: Programming Talk
---

### Post by aktiwers on 2007-08-04
Hi,

Hope this is not too offtopic, but could someone send me a guide to how I would need to upload my JavaServlets to a webserver (apache)? 

Is it enough with FTP access and cPanelX?

Im struggling to get this to work, and have a hard time finding any guides :(

Could anyone point me in the right direction?

Thanks

---

### Post by tenmillionmilesaway on 2007-08-04
As far as i know apache (i presume that you mean the apache http server) does not support Java servlets,  not out of the box anyway.  You might want to look at tomcat [http://tomcat.apache.org/](http://tomcat.apache.org/) which is the apache software foundation's official Java servlet container. Setting up and using tomcat is well documented on the internet and a web search should provide you with multiple guides.

---

### Post by aktiwers on 2007-08-04
Thanks!
After more reading I found out that apache doesnt support  servlets.
I know about Tomcat, but its a rentet dedicated server, so I guess I will have to find a new Host. 

Then if I understand currectly, I simply upload the servlets to /servlets/ folder and everything else is preconfigured.

Thanks for the reply though :)

---

### Post by pmasiar on 2007-08-04
It is confusing that there are Apache web server (== CGI web server) as a project og Apache foundation, and Tomcat servlet container (== java web server), which is also project of Apache Foundation, and confusingly called Apache Tomcat. 

Oh the pleasures of marketing and branding, even for free software!

---

