---
title: "Java Servlet Performance"
date: 2007-03-06
forum: Programming Talk
---

### Post by mikerogers74@mac.com on 2007-03-06
Hi All,

I have a very strange problem...

After installing a new Ubuntu server (6.10) running JDK1.5 I noticed terrible performance losses in my servlets. I traced it to the writing of the output of the servlet, i.e. response.getWriter().write()... or response.getOutputStream().write() etc. This new machine takes around 10 times longer to generate a servlet response than 2 other different Ubuntu 6.10 machines and a Mac on OS X (even though the server is much higher spec). I have also tried JDK 1.6 and different servlet containers (Tomcat and Jetty) but both are the same.

I have disabled all firewalls in the hopes of finding the problem but nothing is working. There are so many variables that I was hoping that someone might have stumbled upon something similar and might give me a pointer in the right direction.

Thanks

Mike

---

### Post by k_smolka on 2007-03-06
If you get really stuck you could try the profiler in netbeans, this may help you to pin point the problem.

More info at problem.
[http://www.netbeans.org/products/profiler/](http://www.netbeans.org/products/profiler/)

Maybe try deploying the Serverts to another servlet engine to see if they cause the same problems. 

Regards 

Karl

---

