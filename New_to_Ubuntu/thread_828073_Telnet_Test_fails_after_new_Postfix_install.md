---
title: "Telnet Test fails after new Postfix install"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by newbiebird on 2008-06-13
Just installed Ubuntu server and walked through the steps to setup postfix.  For the installation I followed the documentation line for line and even on most of the commands did a copy and paste.  I have now reached the testing phase and when I try to connect to telnet it will not connect.  I get the error 

telnet:  Unable to connect to remote host:  Connection refused

Any help is greatly appreciated.

Thanks

---

### Post by awacs on 2008-06-13
> **newbiebird said:**
> Just installed Ubuntu server and walked through the steps to setup postfix.  For the installation I followed the documentation line for line and even on most of the commands did a copy and paste.  I have now reached the testing phase and when I try to connect to telnet it will not connect.  I get the error 

telnet:  Unable to connect to remote host:  Connection refused

Any help is greatly appreciated.

Thanks

Some things which may prove useful: what happens when you type
'postfix start' 

and 'lsof -i tcp:25'

?

Next, post (if it's long, just a sample) the results of
grep postfix /var/log/syslog

if nothing comes back, try 
grep postfix mail.err

---

### Post by cariboo on 2008-06-13
telnet is not enabled by default. Did you install telenetd on your server then enable it in inetd

Jim

---

### Post by awacs on 2008-06-15
> **cariboo907 said:**
> telnet is not enabled by default. Did you install telenetd on your server then enable it in inetd

Jim
You're confusing telnet (the client) with telnetd (the server). 
i believe ubuntu installs telnet (the client) by default.
And, you don't need telnetd (the server) to test postfix - postfix
should be answering on its own!

---

### Post by newbiebird on 2008-06-18
Thanks for the replies - here's where I am right now.  

#1  No I had not installed telnetd - - thought it was by default.  I have since installed telnetd and I'm able to telnet to my box on port 25

#2 Was this necessary to test my postfix installation?

Thanks - - I'm really new with this stuff and everyone's help is appreciated.

---

### Post by awacs on 2008-06-18
> **newbiebird said:**
> Thanks for the replies - here's where I am right now.  

#1  No I had not installed telnetd - - thought it was by default.  I have since installed telnetd and I'm able to telnet to my box on port 25

#2 Was this necessary to test my postfix installation?

Thanks - - I'm really new with this stuff and everyone's help is appreciated.

#2 - Nope, it's orthogonal to your problem. Telnetd (by default) listens on port 23 and has nothing to do with mail. That's why I said you don't need it. You *do* need Telnet, the client, but that *is* installed by default (else when you typed telnet, you'd get back a message command not found).

When you telnet-ed to port 25, what banner did you see?

---

