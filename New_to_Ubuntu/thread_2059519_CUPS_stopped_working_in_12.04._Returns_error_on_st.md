---
title: "CUPS stopped working in 12.04. Returns error on start"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by androssofer on 2012-09-18
I Installed 12.04 in July, worked with the office printer perfectly. tried to print today and it wont. 

in the printer settings dialog it says:

> printing service not available. Start the service on this computer or connect to another server

so i attempted to start cups and got:

```
$: service cups start

start: Rejected send message, 1 matched rules; type="method_call", sender=":1.153" (uid=1000 pid=17105 comm="start cups ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```

any ideas how to fix it?

---

### Post by androssofer on 2012-09-19
bumpy bump

---

### Post by androssofer on 2012-09-25
So I just completely removed Cups and the cups client via the synaptic package manager. 

Then reinstalled it and all its dependencies..

then started it with:

```
sudo service cups start
```

and now it works as normal :-)

---

