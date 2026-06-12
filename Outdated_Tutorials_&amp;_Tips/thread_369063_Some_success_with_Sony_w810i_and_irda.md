---
title: "Some success with Sony w810i and irda"
date: 2007-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by tgalati4 on 2007-02-24
Had some success connecting a Dell Inspiron 7500 using built in irda port to a Sony Ericsson w810i phone.  Dapper 6.06.1 LTS. 

Followed these instructions:
[http://www.ubuntuforums.org/showthread.php?t=202863&highlight=openobex](http://www.ubuntuforums.org/showthread.php?t=202863&highlight=openobex)

Added:

sudo chmod 777 /dev/ttys0            (need to loosen up your first serial device)
sudo ln /dev/ttys0 /dev/palm3     (the instructions are designed for syncing a Palm 3rd generation--I'm not sure how to change this, but it works and the phone doesn't really care what it is called.)

I downloaded a file called IRFC.jar  (from the link reference above).  This is a little utility in Spanish that runs on the phone to give you rudimentary control over other IR devices.

go to the directory where your file is located:

obexftp_palm3 IRFC.jar

The phone chimes with an Accept message.  Hit yes and it downloads.  Store in Applications and run it.  

Your mileage may vary.

I will update this as I get more functionality tested.
:) :) :)

---

