---
title: "Integrating php with java"
date: 2007-08-02
forum: Programming Talk
---

### Post by shivani on 2007-08-02
I am not able to run my php files from the browser which uses java classes its give me error that java class not found. I am using ubuntu 7.04 and  installed 
java version "1.6.0"

and I configured my eclipse for java 1.6 and also I configured my jvm for java version 1.6 .Although I am not getting any problem in running java program  from eclipse but I am getting problem in running php files from the browser. 

The error I am getting is as Fatal error: Class 'Java' not found in /var/www/phpinfotest.php the code I am using is as 

$system = new java('java.lang.System');

can any one help me out where the probl;em exactly is

shivani

---

### Post by nitro_n2o on 2007-08-02
do you have the PECL extension for php?

---

### Post by shivani on 2007-08-03
how to know PECL is installed or not and what is the use of it.
here one more thing I wan to mention that tomcat is not installed on my  system and I am using the tomcat of server .Only apache is installed on my system

---

### Post by nitro_n2o on 2007-08-03
I haven't done Java with PHP integration i just know some people doing this 
this is about pecl 
[http://pecl.php.net/](http://pecl.php.net/) 
I'll ask some questions/find resources and get back to you


here is a more details explanation [http://www.phpbuilder.com/manual/en/ref.java.php](http://www.phpbuilder.com/manual/en/ref.java.php)

---

### Post by dootzky on 2007-08-06
hi people, i was having the same problem, and i solved it ALL with only one click installation. 

it's called **php-java bridge**.

great stuff. saves me a lot of effort, and further more, it's compile time is 10 times faster, and more reliable, or at least the authors say so :)

ok, here's the link: 
[http://php-java-bridge.sourceforge.net/pjb/](http://php-java-bridge.sourceforge.net/pjb/)

hope to help someone :)
ch33rzs. 

:guitar:

---

### Post by Sailme on 2012-04-26
Apart from PHP java bridge you can also use web services to exchange data. Use localhost for performance purpose [facejar]("http://www.facejar.com") uses the same technique.

---

