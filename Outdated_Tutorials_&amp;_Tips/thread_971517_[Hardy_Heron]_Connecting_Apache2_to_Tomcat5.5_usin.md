---
title: "[Hardy Heron] Connecting Apache2 to Tomcat5.5 using mod_jk"
date: 2008-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by kulshoks2121 on 2008-11-05
This tutorial is for people who wants to make a web server using Ubuntu 8.04 or Hardy Heron that runs both PHP and JSP files together by using apache2 and tomcat5.5


In the terminal:

1. sudo apt-get install apache2-mpm-prefork apache2.2-common apache2-utils

2. sudo apt-get install sun-java6-jdk tomcat5.5 tomcat5.5-admin tomcat5.5-webapps

3. sudo apt-get install libapache2-mod-jk

4. sudo a2enmod

5. type in: jk

6. sudo gedit /etc/apache2/mods-enabled/jk.load

7. add these lines:

JkWorkersFile /etc/apache2/workers.properties
JkLogFile /var/log/apache2/mod_jk.log
JkLogLevel debug
JkMount /jsp-examples worker1
JkMount /jsp-examples/* worker1
JkMount /servlets-examples worker1
JkMount /servlets-examples/* worker1

8. save and exit

9. sudo gedit /etc/apache2/workers.properties

10. add these lines:

    workers.tomcat_home=/usr/share/tomcat5.5
    workers.java_home=/usr/lib/jvm/java-1.5.0-sun
    ps=/
    worker.list=worker1
    worker.worker1.port=8009
    worker.worker1.host=localhost
    worker.worker1.type=ajp13
    worker.worker1.lbfactor=1

11. save and exit

12. sudo gedit /etc/environment

13. add these lines:

PATH=\u201d/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games\u201d
LANG=\u201den_IN.UTF-8\u2033
LANGUAGE=\u201den_IN:en\u201d
CLASSPATH=.:/usr/lib/jvm/java-6-sun/bin:/usr/share/tomcat5.5/common/lib/servlet-api.jar
 JAVA_HOME=/usr/lib/jvm/java-6-sun

14. save and exit

15. sudo gedit $HOME/.bashrc

16. add these lines:

export JAVA_HOME=/usr/lib/jvm/java-6-sun
export CATALINA_HOME=/usr/share/tomcat5.5
export CLASSPATH=/usr/share/tomcat5.5/common/lib/servlet-api.jar
export PATH=$PATH:$JAVA_HOME/bin:$CLASSPATH:$CATALINA_HOME

17. save and exit

18. sudo gedit /etc/apache2/sites-available/default

19. add these lines between </Directory> and </VirtualHost> :

<Directory "/usr/share/tomcat5.5-webapps/ROOT/WEB-INF/">
    AllowOverride none
    deny from all
   </Directory>   
    JkMount /* worker1

20. change the /var/WWW from Document Root and Directory to :

/usr/share/tomcat5.5-webapps/ROOT/

21. save and exit

22. sudo /etc/init.d/tomcat5.5 stop
 
23. sudo /etc/init.d/apache2 stop

24. sudo /etc/init.d/tomcat5.5 start

25. sudo /etc/init.d/apache2 start

Try opening your browser and type your ip address or [http://localhost](http://localhost) Tomcat page should show up. To test if it is running with apache, type [http://localhost/server-staus](http://localhost/server-staus)

Note:I did this 4 times with different servers using Ubuntu Hardy Heron on it so it should absolutely work but im not quite familiar with other versions so i can do it only on hardy heron, to do this in Ubuntu Server Edition 8.04 just change the gedit command to vi

---

### Post by aranor on 2008-12-07
I found needful add the following row in /etc/apache2/sites-available/default:

JkUnMount /*.php  worker1

in order to make php files served by apache

see [http://tomcat.apache.org/connectors-doc/webserver_howto/apache.html#Configuring%20Apache%20to%20serve%20static%20web%20application%20files](http://tomcat.apache.org/connectors-doc/webserver_howto/apache.html#Configuring%20Apache%20to%20serve%20static%20web%20application%20files)

10x 4 d post

---

