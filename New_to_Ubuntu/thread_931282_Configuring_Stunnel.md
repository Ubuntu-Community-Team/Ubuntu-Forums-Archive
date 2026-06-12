---
title: "Configuring Stunnel"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by j3z on 2008-09-27
Hi, How do I know if stunnel is running in ubuntu? I created "stunnel.pem file and stunnel.conf which are located in /etc/stunnel. Running the following command seems to work but I have no indication that stunnel is running and firefox doesn't work using proxy settings. "sudo /etc/init.d/stunnel4 start". I've read several post including info on stunnel's website but nothing that shows me stunnel is running. Any suggestions or more info I need to include? Thanks!

---

### Post by j3z on 2008-09-28
Any one? Thank you!

---

### Post by deadite66 on 2008-09-28
you can run 
```
ps -A |grep stunnel
```
to see if its running

you'll also need to edit /etc/default/stunnel and change to ENABLED=1 to get it running if you haven't already done so.

---

### Post by j3z on 2008-10-03
Thank you deadite66. Sorry for taking so long to respond. This is the output after command  ps -A |grep stunnel in terminal:

:~$ ps -A |grep stunnel
 4611 ?        00:00:00 stunnel4
 4612 ?        00:00:00 stunnel4
 4613 ?        00:00:00 stunnel4
 4614 ?        00:00:00 stunnel4
 4615 ?        00:00:00 stunnel4
 4616 ?        00:00:00 stunnel4


Does this mean it is running? I also edited /etc/default/stunnel and change to ENABLED=1

When I type command sudo /etc/init.d/stunnel4 start now I get the following error: "Starting SSL tunnels: [Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file". What does that mean and how do I specify the "pid"? 


Thanks!

---

### Post by deadite66 on 2008-10-03
> **j3z said:**
> 
Does this mean it is running?


yes

> **j3z said:**
> 
When I type command sudo /etc/init.d/stunnel4 start now I get the following error: "Starting SSL tunnels: [Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file". What does that mean and how do I specify the "pid"? 


it says that when its already running, ENABLED=1 turns on starting on boot.

---

### Post by j3z on 2008-10-03
Got it! Thank you for your help deadite66. Stunnel is now up and running. :)

---

