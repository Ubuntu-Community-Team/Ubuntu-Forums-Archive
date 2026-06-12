---
title: "Mount Box.com at login"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2012-12-26
Hi Guys,

I've followed the instructions [***[COLOR="Blue"]here[/COLOR]***]("http://dev.modmancer.com/index.php/2011/12/17/access-box-com-box-net-from-your-ubuntu/") and am able to mount Box.com from 12.04.

I'm pretty happy with that since this is a supplement to my Dropbox account.

My question is:

Is there a way I can automount Box.com at login?  Currently, I'm typing 
```
mount box.com/

```
in a terminal then putting in my email address and password.

---

### Post by GrouchyGaijin on 2012-12-26
I found a solution based on the answer provided in this thread:
[http://ubuntuforums.org/showthread.php?t=702639]("http://ubuntuforums.org/showthread.php?t=702639")

It turns out that there is a program called expect that makes this type of script possible.

Step 1: Install expect from synapitc

Step 2: Use this script
```
#!/usr/bin/env expect

set username Your-Email-Address
set pass Your-Password
set host https://www.box.com/dav

spawn mount ${host}

expect -re "login:"
send "${username}\r"

expect "Password:"
send "${pass}\r"


expect eof  

```

Step 3: Make the script executable and add to your start up applications.

*The first time I rebooted something went wrong and there was no box.com folder in my home.  I don't know why.  Subsequent reboots have mounted box.com without incident.

---

