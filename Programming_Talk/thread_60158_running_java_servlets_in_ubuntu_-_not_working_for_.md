---
title: "running java servlets in ubuntu - not working for me"
date: 2005-08-26
forum: Programming Talk
---

### Post by raja_sekhar on 2005-08-26
the jsp's r working fine.

THIS IS CLASSPATH env :
/usr/java/jdk1.5.0_04/lib/tools.jar:/usr/java/jdk1.5.0_04/jre/lib/rt.jar:/etc/tomcat/common/lib/servlet-api.jar:/usr/java/jdk1.5.0_04/lib/dt.jar:/usr/java/jdk1.5.0_04/lib/mysql-connector-java-3.0.17-ga-bin.jar::/etc/tomcat/webapps/ROOT/WEB-INF/classes

i gave the <servlet> and <servlet-mapping> in web.xml file; have the context right for my application folder .

tried by putting in various folders (including default folder ...../ROOT/......) apart from special application folders with defined context.

seems to have everything required, but still the servlets don't work.

can someone give me the detailed way of running servlets; especially who have made it worked in ubuntu!

---

### Post by amohanty on 2005-08-27
What does your $CATALINA_HOME/conf/server.xml look like?

AM

---

