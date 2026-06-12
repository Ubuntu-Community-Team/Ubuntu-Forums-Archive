---
title: "Descriptors and Speed"
date: 2010-06-17
forum: Programming Talk
---

### Post by Daemn on 2010-06-17
Hi all,

Okay so I'm not trying to complain. I'm just mystified. Why is it that Ubuntu (and all operating systems I've tried) take forever to process 300+ sockets. I have a scripts that do updates and at any time I'll be using 50-300 descriptors according to netstat.

netstat -naptul | wc -l

When it starts to hit around 250, the internet drastically slows down *on that computer*. The internet is super responsive on my other computers connected to the same router. It's not my internet connection or my router. It's the operating system I believe. Even though it's only using 5% cpu, and less than 10KB/s, it still stalls up.

Why? I don't see any reason for it. I must be doing something wrong or have something set wrong. I can't even load google.com with 300 descriptors.

I should be able to run 1000 without problems I'm pretty sure.

Maybe it has something to do with half-open descriptors, but I don't remember there being a low limit on those like there is with windows, and I don't believe my application is using many (right now it's set to have 50 open connections most).

Thanks for any info you can provide me ):P

---

### Post by soltanis on 2010-06-17
Just guessing here, but it's not like it's easy to keep track of 300 connections at one time.

---

### Post by Daemn on 2010-06-17
> **soltanis said:**
> Just guessing here, but it's not like it's easy to keep track of 300 connections at one time.

Shouldn't CPU take care of that? CPU is only 5%.

Plenty of people host IRC with ~1000 connections.

All it has to do is select/poll the ACK/etc of the list.

I can also run like 10 VM's each with 50 connections no problem. But can't run 500 connections on one.

I'm not running this on VM btw, it has a dedicated server.

I've read it IS hard to keep track of 2000-5000+ connections though.

---

### Post by doas777 on 2010-06-17
well, i think the key, is that sockets operations are all asynchronous. polling a port doesn't typically happen in realtime, so the requests are run on a separate thread so that the host app can keep doing other things (like polling another port on another thread). this means that you could  concievably have 300 threads running concurrently all using the same subsystems needed to access a port. since threads have trouble sharing resources, many objects must be duplicated for each. this takes time, and tracking. 

additionally, the kernel has some protection against the rapid creation of large numbers of threads to prevent thread or fork bomb DOS attacks. 

thats just a guess though, based on the network services i've created in past.

---

### Post by Daemn on 2010-06-17
Well this is no good, lol. I used to run over 1000 sockets on a buddy's server in 2007. Proxy checker among other things. Those things use hundreds of threads. Must be something abnormal in my network/config/maybe server specs.

---

### Post by soltanis on 2010-06-18
You might be hitting the maximum number of file descriptors open. Try some of the stuff on this page:

[http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/](http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/)

You may also be running out of kernel buffer memory.

---

### Post by Daemn on 2010-06-18
My ulimit and other limits are 65000+
My buffers are 50mb, and 300mb swap
My memory is 1GB, and 2GB swap

Something I noticed is "netstat -naptul" reports the process that is using the socket of course. When curl closes the socket, it shows up with no process as TIME_WAIT or LAST_ACK etc. and remains there for a while (30 seconds, a minute? more?). Why can't it just close the connection immediately? What purpose does it serve using a descriptor when no process is using the socket anymore? I was thinking about using something like tcpkill to clean the sockets every few seconds. Or find a config or something that handles this. Or figure out if this is a curl problem.

Thanks

Edit: changed net.ipv4.tcp_fin_timeout to 15, see if that helps

I read it keeps the socket open incase the application wants to reuse the socket. I've set curl to not reuse sockets.

---

