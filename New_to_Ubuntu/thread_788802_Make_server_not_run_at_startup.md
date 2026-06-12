---
title: "Make server /not/ run at startup"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by yc2 on 2008-05-10
Hi,

I have just installed apache2, MySQL and ssh servers. When I try the apache2 it is running also after restart of my system. I want to be able to control this. I want to be able to decide if these servers shoud be automatically started by the system at startup of Ubuntu or not.

As I remember from earlier versions of Ubuntu, this could be controlled under System > Preferences > Sessions. One could find the installed servers and choose which ones to start at Ubuntu startup.

I now use Hardy. I cannot find these servers under "Sessions".

Please tell me a simple way to control whether these servers are activated at Ubuntu startup or not.

Thanks :)

---

### Post by magnumbonum on 2008-05-10
I would use the command line utility **update-rc.d **script for this purpose.

Start a ssh session, or use Terminal and run this command to prevent the apache2 service from starting at startup. ```
sudo update-rc.d -f apache2 remove
``` . You can still start it by using either: 

```

sudo /etc/init.d/apache2 start
sudo apache2ctl start

```

---

### Post by sdennie on 2008-05-10
I think you are looking for System->Administration->Services and not System->Preferences->Session.

---

### Post by ezak on 2008-05-10
Yes, navigate to System > Administration > Services

There you will be able to globally enable and disable any services.

"Sessions" applies to the basic services for your account only on the machine.

---

### Post by yc2 on 2008-05-10
> **vor said:**
> I think you are looking for System->Administration->Services and not System->Preferences->Session.
I think you are right :redface: Sorry for my poor memory
Thread solved :rolleyes:
Thanks everyone.

---

