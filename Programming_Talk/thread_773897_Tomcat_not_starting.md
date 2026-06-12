---
title: "Tomcat not starting"
date: 2008-04-29
forum: Programming Talk
---

### Post by Turk on 2008-04-29
Hello everyone.

I want to use Tomcat and installed it.
When I use **sudo /usr/share/tomcat5.5/startup.sh**I get the following error:
```

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
```

I added the following commands in the same shell session:
```
export JAVA_HOME=/usr/lib/jvm/java-6-sun/
export JRE_HOME=/usr/lib/jvm/java-6-sun/jre/
```
But I still get the same error.

Thanks!

---

### Post by misforturob on 2008-05-01
I have the same problem. It is definitely something that has happened since I upgraded to 8.04.

If you do

```
$ sudo -s
```

to switch to a root shell then tomcat starts up fine though...

---

