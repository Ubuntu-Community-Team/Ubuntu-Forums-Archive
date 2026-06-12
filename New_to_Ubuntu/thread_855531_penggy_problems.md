---
title: "penggy problems"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by safetycopy on 2008-07-10
Hi,

OK, I'm trying to connect through AOL dial-up (it's my only option at the moment) in Ubuntu 8.04.I've installed martian and penggy. I run martian_modem from the command line, then, in a new terminal, run penggy. It gets so far, and then I get a 'Segmentation fault'. Output from penggy is below, can anyone help? I'm so close...

Dialing provider...
Dialing **********
Connection at 19200b/s done.
Executing chat script (/usr/share/penggy/chat/aolnet.scm)...
Script: String 'UQKT2' matched
Script: String 'Username' matched
Script: Send 'aol '
Script: String 'Password' matched
Script: Send 'aol '
Script: String 'Connected' matched
Script: Chat success
Chat success, connected...
Segmentation fault

---

### Post by safetycopy on 2008-07-11
OK, I have to admit to making a mistake here. When I first installed penggy, I tried running it with the default 'protocol' configuration of p3. I got an error message, so I changed 'protocol' to FLAP, which is the configuration I was using when getting the above 'Segmentation fault'.

I've been playing around trying to get it working this morning, and noticed a comment in the penggy.cfg file saying FLAP support wasn't implemented. Doh. So...

I changed 'protocol' back to p3 and am now getting the same error message I was getting upon first installing and running penggy. Command line output is below:

Using /dev/ttySM0 device...
Dialing provider...
Dialing **********
Connection at 16800b/s done.
Executing chat script (/usr/share/penggy/chat/aolnet.scm)...
Script: String 'UQKT2' matched
Script: String 'Username' matched
Script: Send 'aol '
Script: String 'Password' matched
Script: Send 'aol '
Script: String 'Connected' matched
Script: Chat success
Chat success, connected...
Unable to register P3 protocol functions, access is not connected
engine - No data to wait
Server drop the connection.

---

