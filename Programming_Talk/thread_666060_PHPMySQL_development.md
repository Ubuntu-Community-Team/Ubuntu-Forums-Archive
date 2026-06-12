---
title: "PHP/MySQL development"
date: 2008-01-12
forum: Programming Talk
---

### Post by canyoncat on 2008-01-12
Hi,

I am new to Ubuntu... new to Linux. I am a software developer and would like to start developing PHP/MySQL code under Ubuntu. I have been using the Windows environment for many years and I am tired of it.

I have Ubuntu itself installed but where do I get the other stuff I need? The PHP site says it does not have binaries for Linux and points to other sites. Some discussion on other sites says that PHP is included with some Linux distribtutions? Is this true for Ubuntu? I don't see it on my install. Is there someplace I can find everything I need to start doing this... is there any one-stop-shopping for the rest of the LAMP environment?

Any help would be appreciated. I am sure many people here have already been through this.

---

### Post by Naddiseo on 2008-01-13
I don't think it's included, but it's not hard to install. Open up a console and type

```

sudo aptitude install apache2 libapache2-mod-php5 php5 php5-mysql  mysql-client mysql-server

```

and that should have your basic LAMP setup, you can also look in the package manager for all the packages avalable (System->Administration->Synaptic Package Manager) and install from there.

And I would suggest quanta plus for developing ;) that's the best IDE I've found for web dev, though gedit seems to be quite able now.

---

### Post by 23meg on 2008-01-13
Moved to Programming Talk.

In Synaptic, click Edit / Mark Packages by Task and choose LAMP server. You can do the same in the CLI with *tasksel*.

---

