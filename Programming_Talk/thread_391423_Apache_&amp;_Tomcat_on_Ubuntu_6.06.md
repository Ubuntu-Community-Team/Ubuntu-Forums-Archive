---
title: "Apache &amp; Tomcat on Ubuntu 6.06"
date: 2007-03-23
forum: Programming Talk
---

### Post by Ranganaths on 2007-03-23
Hi all,

          I am caught up with confusion. I already have apache 2.0 and 1.3 up and running in my system(ubuntu 6.06).  I ust Apache for my Python (CGI). Now i am developing the spring/jsp apps for which i need Apache Tomcat6.0 to be installed.  I  know that for this purpose i cant use Apache2.0 which i have installed, because its not having the servlet container. So my question is as follows
1) Should i uninstall the existing apache 2.0 and 1.3 webserver in my system? If so after the apache 6.0 installation, can i use the same webserver for the my python cgi scripts? (which i really doubt).

2) Is there a possibility to have a servlet container with the apache 2.0 to have my java webapp running.

3)Also  Please let me know if apache tomcat5.5 or 6.0 is available at synaptic manager.

 I need to  have cushion to work on both python, php  and also with java.. so how do i go with this.. please help me out.

Thank you

---

### Post by pmasiar on 2007-03-23
This is non-expert answer - better experts will move in to criticize my advice, but without my entry they might be slower to comment :-)
> **Ranganaths said:**
>  If so after the apache 6.0 installation, can i use the same webserver for the my python cgi scripts? (which i really doubt).

Apache 6.0? You mean Tomcat 6.0? 

To avoid confusion, don''t call Tomcat "Apache Tomcat". "Apache" is name of the foundation. It is branding excercise, like "Microsoft Excell" or "Adobe acrobat". With the difference that Adobe does not have also product "Adobe 2.0" ;-) Product name is Tomcat.

Tomcat runs java-style web applications (Java marketoids  invented cute names "servlet" for CGI application, and "container" for server).

> 2) Is there a possibility to have a servlet container with the apache 2.0 to have my java webapp running.

Apache web server can continue to handle your Python CGI apps, and will coexist with Tomcat handling your Java "servlets". They should have different URL subdirectories.

> 3)Also  Please let me know if apache tomcat5.5 or 6.0 is available at synaptic manager.


synaptic has "search" function - its answer will be faster and more accurate :-)

>  I need to  have cushion to work on both python, php  and also with java.. so how do i go with this.. 

I did not found any "cushion" project on sourceforge :-) Sounds like good name, maybe I should register it before is taken? :-)

---

### Post by Ranganaths on 2007-03-24
well, thanks for that so called non expert answer.

 I installed the tomcat 5 from the synaptic manager
 but when is start the tomcat.. its not starting.. plz let me know whts wrong with this..

----------------------------------------------------------------------------------------------------------------------------------
ranganaths@Gizmo:~$ sudo /etc/init.d/tomcat5 start
Starting Tomcat 5 servlet engine using Java from /usr/lib/jvm/java-6-sun/bin: ranganaths@Gizmo:~$ sudo /etc/init.d/tomcat5 status
Tomcat 5 servlet engine is not running.
ranganaths@Gizmo:~$

----------------------------------------------------------------------------------------------------------------------------------

Thank you,.

---

