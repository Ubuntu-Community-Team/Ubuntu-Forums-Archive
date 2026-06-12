---
title: "mkahawa possible to run after boot automatically in ubuntu11.04?"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by jcka005 on 2012-08-30
need help! could it be possible for mkahawa to [COLOR=Green]**run automatically**[/COLOR] **after boot** in client's pc? meaning, without going to folder where it is located, double-clicking it and then run..or going to terminal and type the command "[COLOR=Blue]**mkahawa-client -nossl -host (IP) -name (comp name)**[/COLOR]" to run..
if it's possible, what are the steps to do??thanks!

---

### Post by coldcritter64 on 2012-08-31
You could try, 

Click the power button (top right of your screen on the panel) > Startup Applications. 

Click "Add". 

Put the apps name (Mkahawa) In "Name".

In the "Command" line place your command...
```
mkahawa-client -nossl -host <IP> -name <comp-name>
``` First replacing the <IP> and <comp-name> with the correct values of course :-). 

Click "Add".

Logout and log back in will test it. Cheers.

---

### Post by jcka005 on 2012-09-02
> **coldcritter64 said:**
> You could try, 

Click the power button (top right of your screen on the panel) > Startup Applications. 

Click "Add". 

Put the apps name (Mkahawa) In "Name".

In the "Command" line place your command...
```
mkahawa-client -nossl -host <IP> -name <comp-name>
``` First replacing the <IP> and <comp-name> with the correct values of course :-). 

Click "Add".

Logout and log back in will test it. Cheers.

****
thanks for the reply **coldcritter64** :) i have not tried it yet.. i will let you know if it works..thanks!

---

### Post by jcka005 on 2012-09-04
it's working.thanks a lot!):P

---

