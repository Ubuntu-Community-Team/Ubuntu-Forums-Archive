---
title: "Cannot access synaptic repositories"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Joe Soap on 2008-11-18
I'm running Hardy Heron on my laptop which I use at home and at work.  

When I access the internet from work, I have to provide a username and password (different to the un and pwd that I use to logon to the laptop).

When I try to install anything via synaptic (or via Ubuntu's add/remove and update manager), I get an error message that the archive could not be fetched.  
```
W: Failed to fetch http://ch.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kdeedu-data_3.5.10-0ubuntu1~hardy1_all.deb
  302 Found
```

I assume that the reason is because of the difference in un and pwd as said above.

How can I provide a un and pwd to synaptic (or add/remove or update manager) to access the archives?

Thanks
Joe

---

### Post by Thelasko on 2008-11-18
Ok, I'm not on my Ubuntu machine right now, and I've never done this.  It looks like you have to go to system>preferences>network proxy.  You will have to enter some information about your network, you might be able to get that information from Firefox's proxy settings, or those on another computer.

In the end, your network administrator may be blocking the communication to your Ubuntu machine needs to update, but try the instructions above first.

---

### Post by Joe Soap on 2008-11-25
Thanks Telasko, I'll give it a shot.

---

