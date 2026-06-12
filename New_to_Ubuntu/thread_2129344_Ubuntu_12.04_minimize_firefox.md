---
title: "Ubuntu 12.04 minimize firefox"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by rod52 on 2013-03-25
A couple of times firefox would not unhide after minimizing. When this happens, I cannot start any application from the side bar. Ant thoughts?

---

### Post by DuckHook on 2013-03-26
I'm not sure what you mean. Can you cycle to Firefox through <Alt>+<Tab>? Do you mean that the <Super> key refuses to work? Please provide much more explanation, else no data to help with. Generally, the best way to start chasing down oddball behaviour of any kind is to go through your logs, especially dmesg and syslog.

---

### Post by El Tito on 2013-03-26
Does it happen everytime?, try alt+f2 and type system monitor. Find the running instance of firefox and terminate it.
If the gui is not responding, try ctrl+alt+f1, and after logging in, type:
```
ps aux | grep firefox
```
this will give you the PID of the proccess and:
```
kill PID
```

---

### Post by rod52 on 2013-03-26
What I mean is that when I minimize, I usually click on fire fox on the left side bar to maximize it again. But when it freezes, you can click on the dash and nothing happens. Dash does not start. None of the side bar applications will start. LibreOffice, nothing.  I am new to ubuntu and Linux so I did not know about Alt+ tab and I am still learning my around it. It does not do this every time. If it happens again, I will try the above. Thank you both.

---

