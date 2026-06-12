---
title: "I cant open any one of my local drives"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by aditya2 on 2013-08-01
I had windows 8 along with ubuntu 13.4 , i cannot open any local drive on ubuntu error says 
Error mounting , meta data kept in windows refused to mount shut down windows normally 
 but i shut downed windows normally:confused::confused:

---

### Post by slickymaster on 2013-08-01
In Windows 8, hybrid shutdown is enabled by default to make it boot faster. Thing is that it leaves the filesystem in a hibernated state, so it doesn't get closed properly at shutdown and you have to disable it.
Here's how to disable it: [http://www.techulator.com/resources/5201-How-enable-or-disable-Hybrid-Boot-Windows.aspx](http://www.techulator.com/resources/5201-How-enable-or-disable-Hybrid-Boot-Windows.aspx)

---

