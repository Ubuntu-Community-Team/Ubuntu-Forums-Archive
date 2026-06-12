---
title: "java using log4j"
date: 2009-03-03
forum: Programming Talk
---

### Post by badperson on 2009-03-03
Hi,

I have the latest version of log4j from the repositories, but I was getting classpath problems...That means I need to add it to my bashrc, right? 
bp

---

### Post by digital_x on 2009-03-03
This depends.  I assume you are tyring to use it from a standalone app.  If so you will need to add it to your classpath.  You can use the -classpath jvm argument, or you can set the CLASSPATH environment variable.  I wouldn't suggest setting this in your .bashrc since you may run something else that requires a different version and you could have a version clash.

---

### Post by badperson on 2009-03-04
thanks,
so that needs to be added to /etc/environment? 

do I add CLASSPATH = /path/to/jar?

bp

---

