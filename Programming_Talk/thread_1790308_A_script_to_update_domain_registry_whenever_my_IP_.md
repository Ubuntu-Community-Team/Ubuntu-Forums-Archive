---
title: "A script to update domain registry whenever my IP changes"
date: 2011-06-24
forum: Programming Talk
---

### Post by Dustin2128 on 2011-06-24
I'm just wondering if it would be possible to create a script that polls ifconfig for my ip address say, every 10 minutes, and if it changes update my co.cc registry. I run a small website on my dynamic IP server (can't afford a fixed IP) and this is a slight annoyance and contributes to a fair bit of downtime. I know a couple of scripting languages, but not deeply enough to know how to make a script that works with web interfaces on a machine with no gui installed.

---

### Post by boast on 2011-06-24
you can check out how ddclient was made (although it was written in perl)

[http://sourceforge.net/apps/trac/ddclient](http://sourceforge.net/apps/trac/ddclient)

maybe dig through the source code and get some idea

---

