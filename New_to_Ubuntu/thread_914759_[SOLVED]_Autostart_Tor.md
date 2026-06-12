---
title: "[SOLVED] Autostart Tor ?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by WorldTripping on 2008-09-09
I've recently started using Tor with the Firefox Torbutton extension. (Didn't like Vidalia.)

How do I get the Tor daemon to start when I boot up, and get the Torbutton extension to read 'Tor Active'.

Cheers.

---

### Post by forger on 2008-09-09
You might want to edit rc.local
```
gksu gedit /etc/rc.local
```

place your application to start **before** the exit line

---

### Post by vishzilla on 2008-09-09
Install privoxy too. This guide will help you [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by WorldTripping on 2008-09-09
> **forger said:**
> You might want to edit rc.local
```
gksu gedit /etc/rc.local
```

place your application to start **before** the exit line

I couldn't get that to work for me.

So I set up a Startup Program in the Sessions preference to start tor.

I can now see that Tor is running if I 'ps -ef' in a terminal to list all the running processes.

But I still can't get the Torbutton to say 'Tor Enabled' in Firefox, even though the process is running.

Also, when I go to [http://check.torproject.org](http://check.torproject.org) It only says that I am using Tor after I have clicked the Torbutton.

So I guess my question has been slightly revised in that how do I get Torbutton to autostart when Firefox opens ??

Any ideas ?

---

### Post by WorldTripping on 2008-09-09
> **vishzilla said:**
> Install privoxy too. This guide will help you [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

Cheers,

I've got Privoxy running too.

What I want is when I open Firefox for the Torbutton to be saying "Tor Enabled"

I guess that it's not that big a deal if it can't be done. It's only a click..

Cheers.

---

### Post by WorldTripping on 2008-09-09
I just found a great big onion button in the Firefox 'Customize' menu.

That'll be fine.

Cheers everyone.

---

### Post by Randomperson_1000 on 2009-05-21
if u set up custom settings in the network tab in firefox the tor button will read that tor is disabled. 

If howveer u havent then the tor button shoukd say its active

---

