---
title: "Tomcat 6"
date: 2008-05-22
forum: Programming Talk
---

### Post by The Devil Is A Squirrel on 2008-05-22
Does anybody know when TOMCAT 6 get packaged for 8.04 SERVER? I installed it manually but now TOMCAT 6 runs with root privileges and I really don't like that...

---

### Post by xlinuks on 2008-05-22
It is interesting that allowing to run on port 80 using "sudo ufw allow 80/tcp" like on the page:
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)
doesn't seem to solve the problem, looks like the port 80 keeps being blocked.
Perhaps it gets allowed only to "root" users, thus not what I/we are looking for.
In System-Administration-Authorizations I couldn't find an option that would allow port 80 to run from a non-root user account.

---

### Post by ZylGadis on 2008-05-22
All ports below 1024 can only be opened by root. Apache, for example, uses some nice tricks to use port 80 and still be safe. I don't know about Tomcat (I always run it on 8080).

Allowing ports through a firewall (ufw seems to be a tool to control iptables) is something completely different.

---

### Post by The Devil Is A Squirrel on 2008-05-23
I do want to run Tomcat under 8080 (in fact it does already), but not under root. 

How can I change that?

---

### Post by ZylGadis on 2008-05-24
Create a user for it (probably named tomcat), make it safe (disallow logins with this user, remove the shell, etc), and start tomcat through that user with su.

Here is a script I wrote for myself to deal with automatically starting/stopping it (on Dapper Drake). You may want to make some changes to it, since probably things have changed in the way Ubuntu handles init scripts since 2006.

[PHP]/etc/init.d$ cat tomcat
#! /bin/sh

export JAVA_HOME="/usr/lib/j2sdk1.5-sun"

. /lib/lsb/init-functions

case "$1" in
  start)
    log_begin_msg "Starting servlet container (Tomcat)..."
    su -c"/usr/local/apache-tomcat/bin/startup.sh" -s/bin/sh tomcat
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping servlet container (Tomcat)..."
    su -c"/usr/local/apache-tomcat/bin/shutdown.sh" -s/bin/sh tomcat
    log_end_msg $?
    ;;
  force-reload|restart)
    sh $0 stop
    sh $0 start
    ;;
  *)
    exit 1
    ;;
esac

exit 0
[/PHP]

Once you have the script in place, you can simply do

[PHP]sudo /etc/init.d/tomcat start[/PHP]

and it's done. Or you can put it in the boot sequence.

Hope that helps.

---

### Post by The Devil Is A Squirrel on 2008-05-24
> **ZylGadis said:**
> Create a user for it (probably named tomcat), make it safe (disallow logins with this user, remove the shell, etc), and start tomcat through that user with su.


Thank you for the script, I guess I can handle that (didn't thought about this solution, but actually it's quite clear).

As for the disallow logins, remove shell and especially the 'etc' part, could you point me to a document or website, which describes all the steps in detail (I do want it done in a secure way).

---

### Post by ZylGadis on 2008-05-24
Locking a user is a matter of changing the password for that user in /etc/shadow to ! (or including !, which is a non-hash character, at the start of the password hash if you want to keep it). Or you can use
[PHP]passwd -l <username>[/PHP]
which does exactly the same thing. To be completely safe, I also recommend removing the login shell for that user. You can do that by editing /etc/passwd and changing /bin/bash (or whatever it is) for the user to /bin/false . It also makes sense to remove the user's homedir, because it will just waste space. Or, even better, don't create it when creating the user with useradd.
To edit Debian's services boot sequence, look at the manual page for update-rc.d . I assume that is what you mean by "etc part."

Finally, remember that your box's security ultimately depends on tomcat's security. No matter what you do, if someone gains access to a running process on your box, elevating permissions to root is a matter of time (the above measures only increase the required time). So patch regularly and religiously, and do not keep any important information in any machine that is world-accessible in some way.

---

### Post by The Devil Is A Squirrel on 2008-05-24
> **ZylGadis said:**
> Locking a user is a matter of changing the password for that user in /etc/shadow to ! (or including !, which is a non-hash character, at the start of the password hash if you want to keep it). Or you can use
[PHP]passwd -l <username>[/PHP]
which does exactly the same thing. To be completely safe, I also recommend removing the login shell for that user. You can do that by editing /etc/passwd and changing /bin/bash (or whatever it is) for the user to /bin/false . It also makes sense to remove the user's homedir, because it will just waste space. Or, even better, don't create it when creating the user with useradd.
To edit Debian's services boot sequence, look at the manual page for update-rc.d . I assume that is what you mean by "etc part."

Finally, remember that your box's security ultimately depends on tomcat's security. No matter what you do, if someone gains access to a running process on your box, elevating permissions to root is a matter of time (the above measures only increase the required time). So patch regularly and religiously, and do not keep any important information in any machine that is world-accessible in some way.

Thank you very much!

---

### Post by The Devil Is A Squirrel on 2008-05-24
Sorry to bother you again, I have a follow-up questions:

- How can I get rid of the additional output from the starting/stoping sequence ("Using CATALINA_BASE:" blabla)

---

### Post by ZylGadis on 2008-05-25
Redirect the output from Tomcat's startup/shutdown scripts to /dev/null, like this:

startup.sh > /dev/null

Alternatively, you can edit startup.sh and shutdown.sh themselves to achieve that, but then when you upgrade tomcat, probably your changes to its standard scripts will be lost.

---

### Post by anomalizer on 2008-10-28
> **ZylGadis said:**
> All ports below 1024 can only be opened by root. Apache, for example, uses some nice tricks to use port 80 and still be safe. I don't know about Tomcat (I always run it on 8080).


If you look at the tomcat that ships with 8.04 (tomcat 5.5), it runs as user tomcat55. The start/stop script is more complex and uses jsvc. Even if you needed to run tomcat directly on port 80; the daemon would start as root but quickly fall back to user tomcat55.

Running a web server as root is ultimately dangerous. What port it runs on is irrelevant as long as I can make your app do something malicious.

---

