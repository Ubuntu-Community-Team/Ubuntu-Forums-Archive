---
title: "prelink HOWTO and benchmarks"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Quintin Riis on 2008-06-17
I have used prelink in the past, but I've never actually done any tests to see how much it speeds things up.

I had some spare time a few days ago, so I decided to write an article on my website with some benchmarks.  

You can check it out at [http://www.quintinriis.com/speed-up-application-load-time-in-ubuntu-linux-using-prelink-howto-and-benchmarks/](http://www.quintinriis.com/speed-up-application-load-time-in-ubuntu-linux-using-prelink-howto-and-benchmarks/)

I also thought it might be fun to submit to digg..  if you think it's worthy, you can digg it here:
[http://digg.com/linux_unix/Faster_Linux_Prelink_in_Ubuntu_benchmarks_and_HOWTO](http://digg.com/linux_unix/Faster_Linux_Prelink_in_Ubuntu_benchmarks_and_HOWTO)

To install prelink, simply :
```
$ sudo aptitude install prelink
$ sudo nano /etc/default/prelink.conf
```
change "unknown" to "yes"
Then:
```
$ sudo /etc/cron.daily/prelink
```

The first run is the longest.  It took about twenty minutes for me.

---

### Post by baracuda68 on 2008-06-29
Hi.
I installed prelink on Hardy about a month ago, and since not noticing any real gains on my system, I uninstalled (purged)via Synaptic. Now when I use apt-get, or any other package manager, it tries to run prelink, but it's obviously not there.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Running prelink, please wait...
sh: /etc/cron.daily/prelink: not found
E: Problem executing scripts DPkg::Post-Invoke 'echo Running prelink, please wait...;/etc/cron.daily/prelink'
E: Sub-process returned an error code


What can I edit to remove the connection between prelink and the package managers?
Is there a stray "symlink" or something?

---

### Post by Quintin Riis on 2008-06-29
Here is what I would do...

Install prelink.
Edit /etc/default/prelink and set PRELINKING=no
sudo /etc/cron.daily/prelink
Purge prelink

---

