---
title: "libexpect configure problems"
date: 2005-05-04
forum: Programming Talk
---

### Post by jer006 on 2005-05-04
Hi, this is probably a simply problem but it is driving me nuts...

So I downloaded the gnome vpn dialer (gvpndialer), I extracted it and ran configure...  Everything looked good until it came to expect.h so I did an apt-get install expect-dev to install expect and all its related header files.  After installing expect I again ran configure and had the same problem, so using the Synaptic package manager I installed any other packages related to expect (expectk etc...)

So I then located the expect.h file and found it in /usr/include/tcl8.4 so tried passing this into configure like configure --includedir /usr/include/tcl8.4 and still no luck !

What gives, can anyone help ?

---

