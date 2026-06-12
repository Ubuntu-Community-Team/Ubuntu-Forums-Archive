---
title: "[SOLVED] Cannot open bandwidthd"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by sharks on 2008-07-11
I Cannot open bandwidthd . i installed it. when i open it in terminal via the command:

bandwidthd

it says Cannot open ./etc/bandwidthd.conf

---

### Post by ChameleonDave on 2008-07-11
> **sharks said:**
> I Cannot open bandwidthd . i installed it. when i open it in terminal via the command:

bandwidthd

it says Cannot open ./etc/bandwidthd.conf
I imagine that it is not a user app, but a system app (a daemon, in fact).

Try putting "sudo" before the command.

---

### Post by freedomAboveAll on 2011-04-03
The package writes its configuration file to unusual location on install, then looks for it in a different location.

So to get it to run , I copied to where it was looking:

```
sudo cp /usr/share/doc/bandwidthd/bandwidthd.conf /etc/bandwidthd/bandwidthd.conf
```

---

### Post by freedomAboveAll on 2011-04-03
Also note that install of bandwidthd writes its own little apache 2 configuration file, :

/etc/apache2/conf.d
```
:/etc/apache2/conf.d$ more bandwidthd
<Directory /var/lib/bandwidthd/htdocs>
        Options +FollowSymLinks
        AllowOverride All
        order allow,deny
        allow from all
</Directory>

```

I would have expected to find this in /etc/apache2/site-available, if at all.

In any event, removing/editing this file is necessary to get bandwidthd running on apache.

Looks like really cool software!

---

### Post by Hector23 on 2011-05-03
> **freedomAboveAll said:**
> The package writes its configuration file to unusual location on install, then looks for it in a different location.

So to get it to run , I copied to where it was looking:

```
sudo cp /usr/share/doc/bandwidthd/bandwidthd.conf /etc/bandwidthd/bandwidthd.conf
```

Are you really sure you can to use a software that installs conf files in /usr/share/doc/ ? What kind of looney wrote this? I'll continue using iftop.

I checked later and it was installed:

locate bandwidthd.conf
/etc/bandwidthd/bandwidthd.conf

I still prefer iftop!

---

