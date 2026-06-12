---
title: "Unable to edit tomcat-users.xml"
date: 2010-04-15
forum: Programming Talk
---

### Post by chiruu on 2010-04-15
Hi,

I am trying to edit tomcat-users.xml to get the admin console working. Created a symbolic link for my orginial tomcat installation.

The files in the /opt/tomcat/conf are marked with a little lock. How to edit it thru the terminal and add some tomcat admin privileges to it.

Kindly help.


Thanks in advance

---

### Post by PaulM1985 on 2010-04-15
Have you tried:

sudo gedit tomcat-users.xml

?

Paul

---

### Post by scawa on 2010-04-20
What I do is 
:sudo chmod 777 tomcat-users.xml

Make my changes with the editor I have and then change the permissions back.  

:sudo chmod 640 tomcat-users.xml

I KNOW this is not a great thing to do (especially if you don't change the permissions back), but it works...

Stephen McConnell

---

