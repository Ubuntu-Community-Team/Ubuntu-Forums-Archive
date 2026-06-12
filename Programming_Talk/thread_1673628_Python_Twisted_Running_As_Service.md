---
title: "Python: Twisted Running As Service"
date: 2011-01-22
forum: Programming Talk
---

### Post by Sailor5 on 2011-01-22
Greetings!

So I'm nearing completion of my Python written, Twisted engine'd application (Huraaa!). However I've hit what I hope to be my very last snag. My native OS is the ever so great Ubuntu. However my application is intended for Windows. I usually both write and test my application on my native Ubuntu and don't try it on my Windows VM. Atlas the time came to try it on Windows. Although on Ubuntu my Python application (Server - Client based app) the Server can connect fine to the Client both over localhost and indeed external IP.

On Windows only the former is true. The Server can only connect to the Client through localhost. The Firewall is off and everything is forwarded correctly yet when attempting to connect via external IP we get an connection timed out error.

Now this can't be because of the firewall due to it's state being off upon testing. Nor can't it be my script as testing the Twisted echo Client and Server examples also can't connect via external IP. Is this a Twisted issue or something to do with my router configuration? Has anyone else got their Twisted written script to connect via external IP?

Thanks bye!

---

### Post by Sailor5 on 2011-01-23
Anyone have any info on this? I'm really needing it.

---

