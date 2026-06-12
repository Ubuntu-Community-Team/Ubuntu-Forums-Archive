---
title: "How to permanently flush IPtables?"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by heebiejeebies on 2012-09-30
Hi all,

I tried to use firestarter to set up a whitelist for internet access.  It worked for a while then started blocking everything.  I have figured out how to whitelist using opendns instead, but the firewall keeps blocking all traffic upon reboot.  If I flush the IP tables in the terminal all is well, but I don't want to have to do this every time I restart.  Is there a way to permanently flush the IP tables, or can I set up a script to do this after reboot?  If I'm going the script route, it needs to be executable by any user without providing an admin password.

Any help is appreciated, thanks! :cool:

---

### Post by DaGeek247 on 2012-09-30
try reading this tutorial:
[http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/](http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/)

Or maybe reading this post:
[http://www.linuxquestions.org/questions/linux-software-2/run-shell-script-as-root-automatically-265253/](http://www.linuxquestions.org/questions/linux-software-2/run-shell-script-as-root-automatically-265253/)

Good luck. :)

---

### Post by ajgreeny on 2012-09-30
Did you purge firestarter and then restart networking after flushing iptables?  In previous ubuntu versions you could do this
```
sudo /etc/init.d/firestarter stop # (if you still run firestarter; ufw is now the preferred application)
sudo apt-get purge firestarter
sudo iptables -F 
sudo /etc/init.d/networking restart

``` but I'm not sure if the init.d commands to stop firestarter and restart networking work any more now upstart has taken on the services running.

---

### Post by heebiejeebies on 2012-09-30
Thank you both!!  I put the IP flush into a script then used the method in the first post to make it execute at boot time and it worked !! :D

---

