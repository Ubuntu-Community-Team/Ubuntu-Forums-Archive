---
title: "Eclipse Error - Security Component?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-04-28
When I start Eclipse (3.3) and select a Workspace it gives me this message:

Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.

I looked this up and only found one solution:

create 

/home/thomass/.mozilla/eclipse

directory


This did not work for me.  Has anyone else run into this problem?

---

### Post by ghjf345 on 2008-05-02
Is thomass your ubuntu username?

---

### Post by schkovich on 2008-05-02
> **TMcKSmith said:**
> 
create 

/home/thomass/.mozilla/eclipse

directory



It worked for me as well. :confused:

Although I have to admit that I did not create /home/thomass/.mozilla/eclipse but /home/myusername/.mozilla/eclipse :-)

Running Eclipse 3.3.2 Build id: M20080221-1800 on Kubuntu Hardy on HP 8710w

---

### Post by thebrotherofasis on 2008-05-06
Yes, worked for me too, huh?

Kinda weird...

P.S. I run ubuntu, not kubuntu.

---

