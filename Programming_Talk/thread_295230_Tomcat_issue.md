---
title: "Tomcat issue"
date: 2006-11-07
forum: Programming Talk
---

### Post by themusicwave on 2006-11-07
Hey everyone,

I'm in a database/internet programming class here at college.  For this week we need to use MYSQL with Tomcat and JSP.

Well I got tomcat up and running with jsp.  All the tomcat example jsp programs run just fine.  I also have mysql working and have the java driver for it working just fine too.

My only problem is I seem to be putting my own jsp files in the wrong folder or something.  I currently have them in /var/lib/tomcat5/webapps/myfolder/  but when I open a browser and type localhost:8180/webapps/myfolder/file.jsp

I get a 404 error.  I have no idea why.

Any insights would be really great as I need to get this done for tomorrow.  I'm going to go dig through manuals and google. 

Thanks!

---

### Post by yaaarrrgg on 2006-11-08
Try:

    [http://localhost:8180/myfolder/file.jsp](http://localhost:8180/myfolder/file.jsp)

Also, is 8180 the correct port?  I think by defuault, it should be 8080 or 80.

---

