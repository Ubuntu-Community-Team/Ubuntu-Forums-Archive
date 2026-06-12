---
title: "Ubuntu PID question"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by Grigoriy on 2016-01-12
Hello!

I need some explanation as to why in Ubuntu the Process ID (PID) differs when it's being checked in different ways.
For example, crond. When I do this:
     Quote:
     [TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"]                              sudo service cron status                      [/TD]
[/TR]
[/TABLE]
 
I get:
     Quote:
     [TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"]                              cron start/running, process **5610**                      [/TD]
[/TR]
[/TABLE]
 
But when I do that:
     Quote:
     [TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"]                              ps aux | grep crond                      [/TD]
[/TR]
[/TABLE]
 
I get:
     Quote:
     [TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"]                              myusername      ** 5647**  0.0  0.0  17164  2412 pts/11   S+   08:12   0:00 grep --color=auto crond                      [/TD]
[/TR]
[/TABLE]
 
And when I run this command again and again I'm getting different  PID each time (first 2 digits remain the same though, like 56xx).
     Quote:
                                                 myusername      **5658**  0.0  0.0  17164  2400 pts/11   S+   08:13   0:00 grep --color=auto crond

---

### Post by HermanAB on 2016-01-12
myusername 5647 0.0 0.0 17164 2412 pts/11 S+ 08:12 0:00 grep --color=auto crond

That is the PID of grep which is looking for crond.

Use this instead:
ps -e|grep crond

---

### Post by Grigoriy on 2016-01-12
Thanks!

I ran this command this time:
     
   ps aux | grep cron
 
And I got the same PID in both cases.

---

