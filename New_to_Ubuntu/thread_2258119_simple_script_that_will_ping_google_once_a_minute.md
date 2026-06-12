---
title: "simple script that will ping google once a minute"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by chickenlips3822 on 2014-12-24
hello all i am looking for a simple script that will ping google every so often and when no responce is recevied will restart the computer. prefurably one made in nano as i am more capable with nano then any other editor. I am downloading quite a bit and my wireless always seems to disconnect every now and again i can find no way of reconnecting without a restart, any other suggestions how to solve the dissconection issue would be lovely.

---

### Post by chickenlips3822 on 2014-12-25
Hello all i am looking for a simple script that will ping google every  so often and when no responce is recevied will restart the computer.  what ive tryed to make is

 #!/bin/bash         

sleep 20
 
echo 'hello' 

ping -i 5000 [www.google.com]("http://www.google.com")

if
ping: unknown host [www.google.com]("http://www.google.com")
then
reboot 

also my next problem will be the reboot ive tryed to make the reboot passwordless by typing

[B]sudo ALL = NOPASSWD: /sbin/reboot

[/B]to no avail help on that would be lovely

what i think its doing is the **if** is not the correct way to monotor pings output?
sorry i am new i understand this is not the fancy way to post nor the most puzzling problem

---

### Post by The Cog on 2014-12-25
How about this command:
```
while true ; do ping -c 3 www.google.com || sudo reboot ; sleep 60 ; done
```

Or if you want to do it once a minute, add a line like this to /etc/crontab:
```
* * * * * root ping -c 3 www.google.com || /sbin/reboot
```

---

### Post by tgalati4 on 2014-12-25
To improve your wifi connection, you need to look for interference, nearby access points (your neighbors wifi routers), and your wfi card settings.

Install *wifi-radar* and count the number of neighbors.

Seach the web for articles on how to improve wifi signal through better antenna placement.  With phones and tablets all connecting to wifi, trying to maintain a dedicated connection is becoming more difficult.

Use a wired connection instead.  Bothering google every minute is not really the way to solve this problem.

---

### Post by vasa1 on 2014-12-25
And why do you need to reboot if your wireless drops? I think that should be looked into as well. My wireless is far from perfect but it reconnects without any action from me.

---

### Post by yancek on 2014-12-25
You might take a look at the link below, particularly posts 4 and 9.  You will need to modify it to suit your needs, change halt to reboot, etc.  If your network is disconnecting frequently you most likely have other problems.

[http://www.linuxquestions.org/questions/programming-9/problem-bash-script-to-check-the-internet-connection-4175433467/](http://www.linuxquestions.org/questions/programming-9/problem-bash-script-to-check-the-internet-connection-4175433467/)

---

