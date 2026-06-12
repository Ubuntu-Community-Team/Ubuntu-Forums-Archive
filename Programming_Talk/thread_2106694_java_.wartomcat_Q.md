---
title: "java .war/tomcat Q"
date: 2013-01-19
forum: Programming Talk
---

### Post by badperson on 2013-01-19
Hi,
If I'm running an ubuntu server machine with tomcat installed, and a java .war file dropped in the webapps folder, and the webapp wants to write log files....what user is the webapp operating under and how should I set up the permissions to accomodate it?

thanks!
bp

---

### Post by greenpeace on 2013-01-19
hey! 

On my server, the .wars are dropped into the webapps folder by the *root* user, where the tomcat server then does the exploding/deploying and log writing for me.

The user is *tomcat6* here, and permissions are all taken care of in the process of installing the app

cheers!
gp

---

