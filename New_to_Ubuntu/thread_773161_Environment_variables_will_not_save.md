---
title: "Environment variables will not save"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by TomDaBomb2u on 2008-04-28
Hello all,

I'm using Hardy and trying to set environment variables for PATH, JAVA_HOME, and CATALINA_HOME. I've used the command

```
CATALINA_HOME=/etc/tomcat5.5 ; export CATALINA_HOME
```

When I ```
echo $CATALINA_HOME
``` it displays correctly, but only for that session. When I exit this terminal session and open it again, the echo command returns a blank line. 

This happens when I try to edit any environment variable - it is there for the current session, but not saved. 

Any suggestions?

Thanks!
-Thomas

---

### Post by ibutho on 2008-04-28
You need to edit ~/.bash_profile and add
```
export CATALINA_HOME=/etc/tomcat5.5
```

---

### Post by kerry_s on 2008-04-28
have you tried adding it to your ~/.bashrc ?
or /etc/environment (global) ?

---

### Post by kerry_s on 2008-04-28
> **ibutho said:**
> You need to edit ~/.bash_profile and add
```
export CATALINA_HOME=/etc/tomcat5.5
```

if you go with ~/.bash_profile, you need to exit or reboot to take effect.

---

### Post by TomDaBomb2u on 2008-04-28
COOL! Thanks guys! Got it to work now!

Thanks!
-Thomas

---

