---
title: "Desktop loading problem (Gnome Daemon)"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by yizuman on 2008-09-15
Every time I boot up I get this error as pictured below....

[[IMG]http://img291.imageshack.us/img291/626/screenshothi2.th.png[/IMG]](http://img291.imageshack.us/my.php?image=screenshothi2.png)

Any idea how to fix this? Some themes end up missing as a result.

---

### Post by yizuman on 2008-09-15
Anyone help?

---

### Post by jken146 on 2008-09-15
I've seen this before, but the details have slipped my mind.  Perhaps I'll remember tomorrow when I'm not so tired.  More probably, though, someone else will come along soon with your answer :)

---

### Post by yizuman on 2008-09-16
Anybody got time to help me out with this problem?

---

### Post by yizuman on 2008-09-19
help please?

---

### Post by benny bronx on 2008-09-19
I had the same problem, and it appeared to be caused by using the automatic login function.  If you are using this, try going back to having to login, and see if it solves the problem.  
 
   Another trick I tried was to reinstall dbus in synaptic (do not uninstall-just mark "reinstall").

---

### Post by yizuman on 2008-09-19
> **benny bronx said:**
> I had the same problem, and it appeared to be caused by using the automatic login function.  If you are using this, try going back to having to login, and see if it solves the problem.  
 
   Another trick I tried was to reinstall dbus in synaptic (do not uninstall-just mark "reinstall").

My login wasn't automatic, I had to manually login myself each time.

I reinstalled the dbus like you asked and it didn't fix it. The same problem pops up as usual.

Anyone else have a solution?

Thanks

---

### Post by yizuman on 2008-09-23
help?

---

### Post by solitaire on 2008-09-25
I'm having the same error!!

Check your "System Logs"
Goto "System" / "Administration" / "System Logs"  
check "syslog" for any errors or failures.
The only error i can see in my syslog is:
```

Sep 25 13:58:45 Callisto dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Sep 25 13:58:45 Callisto dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep 25 13:58:45 Callisto dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep 25 13:58:45 Callisto dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

```
and
```
Sep 25 14:15:34 Callisto NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

```

The desktop does eventually come up but it takes about 5 mins. (wating for a timeout?)
With me it happened when i tried to set up "OpenDNS" ip addresses to my router and desktop.

Anyone else got any ideas?

---

