---
title: "last trial on ubuntu as my primary os"
date: 2008-10-04
forum: Programming Talk
---

### Post by teenzonez on 2008-10-04
Hello all ubuntu masters,
please help me to configure my laptop.

whenever i try to configure eclipse+java+tomcat on my laptop, i end up with a lot of troubles. after a long try, i managed to configure tomcat6. i tried to install java and eclipse. at first java5 was correctly installed. then because of my sound card problems, i needed to re-install the os again. after that, i was never able to install java completely on my laptop. im able create programs which uses core java packages. but when i tried to use HttpServlet class it simply wasnt there. I tried to install and re-install java5 and java6 more than a dozen times. but nothing worked out. 
in short, i think i need to completely remove all java related directories, files or configuration information. and then i have to install java from scratch. 
another problem is my eclipse3.2.
whenever i try to open eclipse from application->Programming->eclipse it throws the error 'the custom vm you have installed is not a valid executable'. but if i go to the installed folder(usr/lib/eclipse) and start eclipse.jar from there, the IDE opens up i can run small programs, but cant  try any web applications like servlets from there.

please help me out. i am using ubuntu as my only os and i do not want to install windows on my machine. Im struggling for the past two months(ever since i got my laptop). Now my exam dates are coming nearer and i need to do something urgent about it.

are all these problems because of ubuntu? shall i change it to redhat enterprise server?

Thanks,
Teena

---

### Post by CptPicard on 2008-10-04
You describe your situation in too general terms, but I am almost completely certain that you just need to take a deep breath and not mess up your system further, as what you're planning to do sounds very drastic.

HttpServlet is part of servlet.jar, which comes with Tomcat or you can alternatively can get from Sun. You're most probably not seeing it because you are not including servlet.jar in your classpath.

Mind you, configuring Tomcat with Eclipse is a pain, I have never bothered with that but use Netbeans instead -- the web app development integration is totally superior to that of Eclipse, and if you just want to get stuff done, I would suggest ditching Eclipse for this completely.

Also make sure you're using the Sun JDK .. "sudo apt-get install sun-java6-jdk". Should work out of the box perfectly, and if it doesn't, give more specific details of the problem.

---

### Post by teenzonez on 2008-10-04
Hi,
Thanks for the reply. Yes im totally messed up with my ubuntu 7.10. I dont mind changing from eclipse to netbeans.i think i completed my java installation correctly now. just now i installed java6 using the command sudo apt-get sun-java6-jdk sun-java6-jre sun-java6-plugin. i verified it using java -version. i got 


java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

Now, how can i set the servlets.jar file visible when i develop web applications? i do not know where exactly i need to chage the classpath information. why is the class path getting updated automatically?

how to install netbeans IDE if i need to shift from eclipse?

thanks,
Teena

---

### Post by teenzonez on 2008-10-04
Hi thanks a lot for the help.
i can open my eclipse from the eclipse directory now and i wrote a servlet example also. im able to import my servlet jar. now i want to run my servlet on tomcat. can we run it on server from eclipse? i know we have an option to run as server. but in my eclipse 3.2 i cant find it. i am not getting that option when i go to 'Run As' menu. is there anything that can be done about it?

Thanks,
Teena

---

### Post by CptPicard on 2008-10-04
This is where we come to the point of you wanting to move over to Netbeans -- configuring Tomcat with Eclipse is a big annoyance, and I think you're n00b enough not to want to do that.

Netbeans is in the repositories, I suppose it's the easiest way to get it for you.

---

### Post by teenzonez on 2008-10-04
Thank you. Im trying to install netbeans now. once i install netbeans on my machine,how can i associate tomcat server with it?

Thanks,
Teena

---

### Post by Balazs_noob on 2008-10-04
Just grab it here
[http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/)
get the ALL version, it will have tomcat , glassfish and a lot more already configured,
no manual configuration needed after install.

I personally prefer 6.5 beta even if it still has few minor bugs ;)

---

### Post by teenzonez on 2008-10-04
Hi thanks for the help. im shifted to netbeans finally. everything is working fine in it. Thanks for the help both of you!
:popcorn:

Good night.
Teena.

---

