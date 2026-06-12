---
title: "TIP: Monitoring MythTV backend process"
date: 2007-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by rbm0307 on 2007-08-15
Hi,

I've been experiencing random crashing of the mythtv-backend process on Ubuntu Feisty, mostly related to race conditions that upset the backend process.  When the backend dies, it is not automatically restarted, resulting in lost scheduled recordings and a poor wife acceptance factor (WAF). Rather than spend the time trying to isolate and debug the crashing (since it happens so seldomly), I decided to monitor the backend process to maintain its unattended operation.

I installed monit to perform the monitoring function. This is the clause for mythtv that appears in the /etc/monit/monitrc:


# Monitoring MythTV Service
check process mythtv with pidfile /var/run/mythtv/mythbackend.pid
    start program = "/etc/init.d/mythtv-backend restart"
    stop program  = "/etc/init.d/mythtv-backend stop"
    if failed port 6544 protocol http then restart
    if 5 restarts within 5 cycles then timeout
    group server

Rather than check the port the backend listens on, I'm monitoring the port the status reports on.  This way, the mythtv backend status log does not fill up with unsuccessful connection errors.

The mythtv-backend init script that comes with Ubuntu Feisty checks for the existance of a PID file during the start process.  This added some complication to the monit clause because a backend crash would leave an orphaned PID file and the init script would not restart properly.  Using the restart parameter on the command line for the "start program" fixed the complication.

In addition to monitoring mythtv-backend, I've added ssh (for ensured access to the box) and mysql (to ensure that the backend's repository is also available).

# Monitoring Mysql Service
check process mysql with pidfile /var/run/mysqld/mysqld.pid
    group database
    start program = "/etc/init.d/mysql start"
    stop program = "/etc/init.d/mysql stop"
    if failed host 127.0.0.1 port 3306 then restart
    if 5 restarts within 5 cycles then timeout
    group server

#Monitoring ssh Service
check process sshd with pidfile /var/run/sshd.pid
    start program "/etc/init.d/ssh start"
    stop program "/etc/init.d/ssh stop"
    if failed port 22 protocol ssh then restart
    if 5 restarts within 5 cycles then timeout
    group server

--
Robert

---

### Post by praet on 2007-08-16
Interesting. Thanks for sharing.

---

### Post by theonlyrealperson on 2008-09-22
I was doing the same thing, but as of last week monit refuses to admit mythbackend is running. It lists "not found" as a status even though mythbackend is running, and the .pid file is there. 

Anyone know if an update to monit has messed things up?

---

### Post by rbm0307 on 2008-10-04
I just upgraded my Myth backend machine and, simultaneously, upgraded from Feisty to Hardy and MythTV 0.20 to 0.21.  Using the monit package from Hardy, I have not encountered any problems monitoring the MythTV backend process.  The version of monit supplied through Hardy is 4.8.1.

---

