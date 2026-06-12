---
title: "Problem on autostarting tomcat as another user"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by frustr8ed on 2008-09-12
Hello!

I hope one of you has came across and solved this problem. I simply wanted to autostart tomcat as another user and not as a root which i already did successfully using the script below.

In my /etc/init.d/tomcat, i have the following commands:

export JAVA_HOME=<my java path>
export CATALINA_HOME=<my tomcat path>


case $1 in
start)
sudo -u <user i want> sh $CATALINA_HOME/bin/startup.sh
;;

stop)
sudo -u <user i want> sh $CATALINA_HOME/bin/shutdown.sh
;;

restart)
sudo -u <user i want> sh $CATALINA_HOME/bin/shutdown.sh
sudo -u <user i want> sh $CATALINA_HOME/bin/startup.sh
;;

esac


exit 0


The problem: According to some forums i've read, sudo command disables some environment variables such as LD_LIBRARY_PATH, etc which i badly needed. Does somebody know how to revise the script so sudo command restores my environment variables? I've found out about using -e parameter but i got no idea how to use it. Help please.

Thanks.

---

### Post by prshah on 2008-09-12
> **frustr8ed said:**
> 
The problem:Does somebody know how to revise the script so sudo command restores my environment variables? I've found out about using -e parameter but i got no idea how to use it. 

The correct parameter is (note the case!) -E (preserve environment); so you will have to revise the "sudo" lines to include the "-E" switch, Eg,

```
sudo -E -u <user i want> sh $CATALINA_HOME/bin/startup.sh
```

---

### Post by frustr8ed on 2008-09-12
Using **sudo -E -u <user i want> sh $CATALINA_HOME/bin/startup.sh** does not start tomcat after reboot anymore :(

I am using Ubuntu 7.04 and sudo version 1.6.8p12 if these informations are relevant.

Is there any other way that i can stop sudo from removing LD_ environment variable? Or is there any other way to autostart an application like tomcat in another user (not as root) without using the sudo command?

Appreciate your help.

---

