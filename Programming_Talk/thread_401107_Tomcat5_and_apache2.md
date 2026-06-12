---
title: "Tomcat5 and apache2"
date: 2007-04-04
forum: Programming Talk
---

### Post by Ranganaths on 2007-04-04
HI all,

         I have been tryin to install the apache2 and tomcat5 or 6 webserver, but still not accomplished with it.

         Firstly apache2- The problem is that when i start the apache2 its fine it will start and when i type [http://127.0.0.1/apache2-default/](http://127.0.0.1/apache2-default/) url. the apache test page is viewed saying that the installation is successful. 
           but when i create my own php page and deploy in /var/www and type [http://127.0.0.1/mypage.php](http://127.0.0.1/mypage.php). its not displaying the page instead, the default ubuntu download manager pops up to download. I was wondering wht might be the problem with this? the php page which i have written is as simple as <?php echo("welcome to php");?>. 

      Secondly  the tomcat webserver, i installed the tomcat5 from synaptic manager. when i start the tomcat5 webserver. its as follows.
++++++++++++++++++++++++++++++++++++++++++++++++
sudo /etc/init.d/tomcat5 start
Starting Tomcat 5 servlet engine using Java from /usr/lib/jvm/java-6-sun/bin: ranganaths@Gizmo:~$ sudo /etc/init.d/tomcat5 status
Tomcat 5 servlet engine is not running.
ranganaths@Gizmo:~$

++++++++++++++++++++++++++++++++++++++++++++++++
as the output says that tomcat5 servlet engine is not started. and obviously the [http://localhost:8080/](http://localhost:8080/) doesnt show up the test page.


 Please kindly help me out to resolve the above explained problem

Thank you
Regards

---

### Post by smokey edgy on 2007-04-06
There should be some log files detailing Tomcat's startup. I don't recall where they live in the Linux world (should be easy enough to find out). They may give you some insight as to why it didn't start. 

An interesting thing to try would be to use an earlier JDK version (1.5 or 1.4) and try restarting tomcat. If you can quickly point your JDK to an earlier version that was installed, it may be worth it. The log files though are probably your best bet.

---

