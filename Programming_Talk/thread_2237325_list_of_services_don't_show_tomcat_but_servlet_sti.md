---
title: "list of services don't show tomcat but servlet still works fine"
date: 2014-08-01
forum: Programming Talk
---

### Post by IAMTubby on 2014-08-01
Hello,
 I haven't installed tomcat7 in my system. (Confirmation : When I type [http://localhost:8080/](http://localhost:8080/) , I do not get the tomcat7 home page.

However, I am developing a servlet using eclipse(Eclipse Web Tools Platform, to be precise) and at the time of configuring eclipse for first time use, there was this step to create a new Server. At this stage, I browsed and gave the path to the downloaded tomcat 7.(_Please see attached screenshot for this step_). And so, my servlet works.

However, my questions are as follows : 
1. When I do a sudo service --status-all, it doesn't show any tomcat
2. When I type [http://localhost:8080/](http://localhost:8080/) , I do not get the tomcat7 home page. Although my servlet at [http://localhost:8080/MyProject/servletname](http://localhost:8080/MyProject/servletname) shows up correctly even in the browser outside of eclipse.(The moment I close eclipse - server/tomcat is off, I cannot access it even from the browser outside of eclipse)
**Does all this mean that tomcat is not running as a service, but is controlled by eclipse?**
 
Basically, I would like to know how the servlet works, although tomcat7 is not installed in the system. 

Thanks.

PS : I am sorry for posing this question on another forum, as initially I thought it was related to servlet programming and not systems.

---

