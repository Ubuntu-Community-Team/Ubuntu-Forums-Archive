---
title: "Keep daemon command"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by danielv42 on 2008-07-08
Does anyone know the command that is executed when you click the Backup daemon Load button in the "keep" backup program?

Or more generally, does anyone know how to find out the command executed when you click Start or Stop in the System Settings > Advanced > Service Manager > Startup Services?  Where can I find more details about the Service Manager, like what is the difference between the Load-On-Demand Services and Startup Services, and how do you add or remove entries to either of these lists of services?

Thanks!

---

### Post by erginemr on 2008-07-10
My two cents:
To start a service manually, you can normally issue:
```
sudo /etc/init.d/*service_name* start
```
and to stop it:
```
sudo /etc/init.d/*service_name* stop
```

There are two tools that I know to selectively enable and disable startup services:
1. **sysv-rc-conf** (a terminal application)
2. **bum** (bootup manager, a graphical application)

Both are installable via Synaptic.

---

