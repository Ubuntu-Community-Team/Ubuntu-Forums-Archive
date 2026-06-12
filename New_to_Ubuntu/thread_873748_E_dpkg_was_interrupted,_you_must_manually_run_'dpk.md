---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct..."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by greenpeach on 2008-07-29
Hi,

I have had Ubuntu 8.04 installed for a month now. I know get the following error when I try to install updates in the update manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  E: _cache->open() failed, please report.

And when try to run dpkg --configure -a in Terminal I get the following message:

requested operation requires superuser privilege

Please help me out, I don't know where to start.

Thanks.

---

### Post by tuxxy on 2008-07-29
Try running at as root,
```

sudo dpkg --configure -a
```

---

### Post by greenpeach on 2008-07-29
> **tuxxy said:**
> Try running at as root,
```

sudo dpkg --configure -a
```

Wow, thanks so much for you help. You made my day.

Can you please explain what the "dpkg was interrupted" message means?

Thanks again

---

### Post by tuxxy on 2008-07-29
Certainly, 

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.


Your automatic dpkg process was interrupted, so you you needed to manually run the dpkg as admin user, the sudo at the start of the command tells it to run the command as admin.

---

### Post by greenpeach on 2008-07-29
> **tuxxy said:**
> Certainly, 



Your automatic dpkg (damaged packages) process was interrupted, so you you needed to manually run the dpkg as admin user, the sudo at the start of the command tells it to run the command as admin.

I see.

Thanks again.

---

### Post by northern lights on 2008-07-29
> **greenpeach said:**
> Can you please explain what the "dpkg was interrupted" message means?

> **tuxxy said:**
> Your automatic dpkg (damaged packages) process was interrupted, so you you needed to manually run the dpkg as admin user, the sudo at the start of the command tells it to run the command as admin.

'dpkg' is the lower level package management utility in Debian and Debian-based distributions.

You usually don't need to use it, unless you want to install single .deb packages and even for that there's a front-end (GDebi) nowadays.

```
dpkg --configure PACKAGE
```the '--configure' flag let's 'dpkg' (re)configure an unpacked package.

```
dpkg --configure -a
```configures all unpacked but unconfigured packages.

In this process dpkg unpacks the configuration files, backs the old ones up and runs a postinst script if one came with the package.

Some package you had left unconfigured --> had to do it yourself now.

---

### Post by billgoldberg on 2008-07-29
> **tuxxy said:**
> Certainly, 



Your automatic dpkg (damaged packages) process was interrupted, so you you needed to manually run the dpkg as admin user, the sudo at the start of the command tells it to run the command as admin.

I'm pretty sure you didn't understand what he meant.

This error happens when you close the window when you are installing something (updates, software, ...).

---

### Post by Barrucadu on 2008-07-29
Also, "dpkg" is not "damaged packages".

---

### Post by greenpeach on 2008-07-29
> **billgoldberg said:**
> I'm pretty sure you didn't understand what he meant.

This error happens when you close the window when you are installing something (updates, software, ...).

Not really, but he helped me fixed my problem :-)

But I do remember trying to update something a few days and did close the window because I changed my mine.

---

### Post by Joeb454 on 2008-07-29
> **greenpeach said:**
> Not really, but he helped me fixed my problem :-)

But I do remember trying to update something a few days and did close the window because I changed my mine.

It's probably updated now... :p

---

### Post by greenpeach on 2008-07-29
> **Joeb454 said:**
> It's probably updated now... :p

It's all just fabulous! - I certainly don't miss Windows!

---

