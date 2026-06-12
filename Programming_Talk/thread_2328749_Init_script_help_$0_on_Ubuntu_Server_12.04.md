---
title: "Init script help: $0 on Ubuntu Server 12.04"
date: 2016-06-24
forum: Programming Talk
---

### Post by 1clue on 2016-06-24
Hi.

I have several tomcat7 services on an Ubuntu Server 12.04.5 box. Some of them are based on the Ubuntu-provided package, and others are based on standalone zips downloaded from tomcat.apache.org.

I modified the original init script provided by tomcat7 package such that:
```

NAME=`echo $0 | sed 's/\/etc\/init.d\///'`

```

and then I use a symbolic link to tomcat7 for each tomcat service.  The defaults are read from /etc/default/<service> and the world is great.

So for the longest time I had a problem.  Services would start or stop manually (service 8081 start) but would never start automatically on boot.  I've been using Ubuntu for years and Linux for much longer, but this one stumped me.

Then I realized I'm using $0 to get the script name. /etc/init.d/<port> is the init script, but that's a symbolic link to tomcat7. Then, in /etc/rc?.d/ I have a (for example) S209092 which is a symbolic link to /etc/init.d/9092 which is in turn a symbolic link. During manual start/stop I'm starting or stopping based on port number, and it works.  During boot the name of the script is different so I fail.

Is there a clever way to get $0 for only one level of indirection?

Maybe I need to dust off my regex and remove the [SK][0-9][0-9] from the beginning?  I was hoping for something handier than that.

Thanks.

---

### Post by steeldriver on 2016-06-24
I don't really understand what you're trying to do - in any case, Sys5 init files are going the way of the dodo

However, the readlink command might help you achieve what you want e.g.

```

$ readlink -f /etc/rc5.d/S20screen-cleanup
/etc/init.d/screen-cleanup

```

I'd also suggest using basename (or shell parameter substitution) instead of trying to trim the path using sed

```

$ basename $(readlink -f /etc/rc5.d/S20screen-cleanup)
screen-cleanup

```

---

### Post by 1clue on 2016-06-24
Yes, I still have to get my head around the new init systems. Systemd especially makes my head hurt, it's overly complicated for an init system. Frankly I think we're better off without it.

readlink -f is definitely not what I want.  I want the name of the symbolic link which points to /etc/init.d/tomcat7. So once removed from the final point, but not twice removed if that makes sense.

---

