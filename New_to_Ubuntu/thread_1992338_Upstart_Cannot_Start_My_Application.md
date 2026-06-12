---
title: "Upstart: Cannot Start My Application"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by SwissCharm on 2012-05-31
Hello All,

I'm new to Ubuntu and am hoping you may be able to help me.

**Background info:**
I have been developing a simple application that connects to a USB-HID device and reads byte packets and places them into a PostgreSQL database.
The allpication name is "hb-coor-daemon". it can accept differnt "options" using "optget", one is that I fork to a child process and disconnect the partner and exit. Hence the name "hb-coor-daemon".

Anyhow...

The application works fine and all is well when I execut from the terminal like so: "sudo ./hb-coor-daemon", however I would like this application to start at "startup" in a sense as a daemon. Which I could do like this: "./hb-coor-daemon -d" (the -d is to fork etc...)

**Question:**
I have been trying to  get upstart to work by creating a file called: "hb-coor-daemon.conf" and placed the following two lines of code in it:

```
exec /HB/HB-Coor-Daemon/hb-coor-daemon -t 3 -l
start on startup
```When I execute: 
```
initctl list 
```I can find the entry:
```
hb-coor-daemon stop/waiting
```When I try: 
```
initctl start hb-coor-daemon
```I get:
```
initctl: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=2055 comm="initctl start hb-coor-daemon ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```I'm unsure what I may be doing wrong?

Any suggestions are very much appreciated - Thank you

---

### Post by SwissCharm on 2012-05-31
All,

I think I found the issue:

First:
I needed to change the "hb-coor-daemon.conf" file to the following to have the start up line before the exec line, not sure why but that helped.

```
start on startup exec /HB/HB-Coor-Daemon/hb-coor-daemon -t 1 -l
``` 

Second was that I need to make sure the application was not execution protected. I initially though that startup operated as root, but somehow still had a problem with executing my application.

Thank you

---

