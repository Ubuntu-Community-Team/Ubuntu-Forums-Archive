---
title: "Help Please Dovecot won't start"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by Stoffel69 on 2012-10-22
Hi, Please help, Dovecot won't start.

When I try to start dovecot I get the following:
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.79" (uid=1000 pid=3325 comm="start dovecot ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

So I checked the service (service dovecot status) and got reply (dovecot stop/waiting)

Then I tried following command: update-rc.d dovecot defaults
and is still getting the same error as mentioned above.

Any ideas???:(

---

### Post by daslinkard on 2012-10-22
What happens (if anything) when you run the following sudo command:
```
service dovecot start
```

---

### Post by Stoffel69 on 2012-10-23
I get the following:

start: Rejected send message, 1 matched rules; type="method_call", sender=":1.79" (uid=1000 pid=3325 comm="start dovecot ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

---

