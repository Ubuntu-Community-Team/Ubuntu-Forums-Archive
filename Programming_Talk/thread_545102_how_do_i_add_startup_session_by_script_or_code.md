---
title: "how do i add startup session by script or code"
date: 2007-09-07
forum: Programming Talk
---

### Post by neimasilk on 2007-09-07
how to add my program to startup session  by using script or code? 
anyone know where is configuration file or something related to startup session?
when im using /etc/rc.local to start my program its doesn't work since my program must run after user login, its work when i add manually to startup session, but i want to automatically add it when i install the programs.. 
thanks in advance

---

### Post by gnusci on 2007-09-07
Check this link:

[http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/](http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/)

---

### Post by neimasilk on 2007-09-07
thanks for the answer, i already know that, but you have to manually add to the session list,

i found interesting quote on the article :
> 
And yes, for the more technical users, you can modify the startup script and accomplish the same thing.


but how?, where is the startup script? or script that automatically run after user login, ( rather then /etc/rc.local )

thanks in advance

---

### Post by finer recliner on 2007-09-07
there is no "single" startup script. there are lots of scripts that are executed are startup which call more scripts, and those scripts call more scripts. so you just need to pick the most appropriate place to call the startup you want to create. i personally usually just add a startup entry in cron.

more info to read about ubuntu startup scritps:
[http://www.extremetech.com/article2/0,1697,2114121,00.asp](http://www.extremetech.com/article2/0,1697,2114121,00.asp)

---

### Post by neimasilk on 2007-09-07
> **finer recliner said:**
> 
more info to read about ubuntu startup scritps:
[http://www.extremetech.com/article2/0,1697,2114121,00.asp](http://www.extremetech.com/article2/0,1697,2114121,00.asp)

wow thanks... great info, this is what im looking for..

---

