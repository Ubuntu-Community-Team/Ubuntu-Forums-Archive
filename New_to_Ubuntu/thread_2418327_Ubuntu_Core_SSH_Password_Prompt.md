---
title: "Ubuntu Core SSH Password Prompt"
date: 2019-05-05
forum: New to Ubuntu
---

### Post by kriscii on 2019-05-05
I've installed Ubuntu Core 18 and the install progresses through smoothly. At the end I am told to logon with my account@ipaddr, I have already loaded the public SSH key in my ubuntu one account but when I connect with Putty or other SSH tools I get prompted for a password and told Server Refused key. If I look at the key fingerprint on the screen it is different to the public key fingerprint I get when I generate the key and both are different to the key fingerprint I get given from the SSH client. I've tried 3 different methods of generating the keys and all are giving the same problem. I'm finding this frustrating and ready to give up on Ubuntu as a bad choice. I've never used keys for logon before but Core doesn't seem to allow just a normal logon.

---

### Post by kriscii on 2019-05-05
Please ignore found a different linux distro supported for my hardware and was up and running ready to install apps in 20 mins. Ubuntu scores 0 for ease of use having spent 6 hours on it without being able to login.

---

### Post by TheFu on 2019-05-05
Ubuntu Core has some requirements that I was unwilling to agree to accept, so I moved on as well, before trying it.
Ubuntu Core is NOT a desktop nor server release. It is designed for extremely limited devices, IoT, where you'd like centralized management forced onto you.
[https://www.ubuntu.com/core](https://www.ubuntu.com/core)
> 
[B]Security first
[/B]Security is our job from the moment you power it on.
We redesigned the entire system from first boot to create the most secure embedded Linux for devices and connected things.

It is impossible for anyone, including Canonical, to support every SBC available today.

Please mark this thread as SOLVED using the thread tools button near the top.

---

### Post by kriscii on 2019-05-06
I chose core as I wanted to run a bare Linux to run docker with no overhead of a desktop or other feature wasting resources. I've used Centos minimal in the past with no problems but that isn't approved on the Intel NUC. Anyway installed Clear Linux which looks to be fast and supported. I've used multiple flavours of Linux in the past and this is the first time I've not been able to get it installed.

---

### Post by TheFu on 2019-05-06
For a container OS, I thought people were going with alpine? [http://containertutorials.com/alpine/get_started.html](http://containertutorials.com/alpine/get_started.html)  I wouldn't pull it from Docker repos, but I wouldn't pull anything from docker repos.

I see Clear Linux more for the Host OS.

But everyone has to find their own way. Nobody has all the answers.

---

