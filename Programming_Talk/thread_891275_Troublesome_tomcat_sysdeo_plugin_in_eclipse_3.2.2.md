---
title: "Troublesome tomcat sysdeo plugin in eclipse 3.2.2"
date: 2008-08-15
forum: Programming Talk
---

### Post by iubun2 on 2008-08-15
I have installed eclipse 3.2.2 and tomcat sysdeo plugin.

I'm using Ubuntu 8.04 LTS Hardy

The trouble is, nothing happens when i click the tomcat start/stop/restart buttons.. :confused:

The logs suggest that :

```

!ENTRY com.sysdeo.eclipse.tomcat 4 4 2008-08-16 07:25:18.974
!MESSAGE Impossible to start Tomcat
Check home directory setup in Tomcat preference page/n

```

I have set the tomcat home directory in window>preferences>tomcat page as:

```
/usr/share/tomcat5.5/bin
```


I think the plugin is unable to read the tomcat home directory i am specifying. 

Does sysdeo require any env variables set as well?

Any pointers would be very useful, as i'm new to linux and have been trying to figure this out since the last 2 days (unsuccessfully, of course).

---

### Post by iubun2 on 2008-08-16
i think i'll have to re-install ubuntu and start over.:( There's not much i think i can do from where i have reached.. :confused:

has no one ever faced this problem in eclipse+sysdeo+hardy combo ??

---

### Post by iubun2 on 2008-10-05
For all those who faced this problem, the solution was to STOP trying to install eclipse 3.2.2 or 3.3 on Hardy Heron ;)

Installing eclipse "3.4" Ganymede and sysdeo tomcat plugin did the trick. 

Hope this helps. 

Regards!

---

### Post by mhdazeem on 2009-02-23
I am using eclipse 3.2 and if I upgrade to 3.4 does my stuff get deleted or not....becoz i want to save my data...thanks

---

