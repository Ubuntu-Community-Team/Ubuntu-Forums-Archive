---
title: "remote desktop for XP"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Garthhh on 2011-10-16
I have a both my ubun machines able to be  accessed remotely
how do I add my XP machine to the mix?

---

### Post by sadaruwan12 on 2011-10-16
What are you using VNC or something else to get the remote connection ?

what I use is combination of VNC and TeamViwer I use TeamViwer mostly 'cos it's  very easy once you program all the clients with a permanent password and add them to my client list where ever I log in I've my list select them and start simple as that.

---

### Post by d4m1r on 2011-10-16
> **Garthhh said:**
> I have a both my ubun machines able to be  accessed remotely
how do I add my XP machine to the mix?

No need for VNC or Remote Viewer!!! Simply allow remote desktop connections on the XP machine and use "terminal server client" (search for it on your PC, if you don't have it, try the Ubuntu Software Centre) to connect to it from Ubuntu!

---

### Post by Garthhh on 2011-10-16
> **d4m1r said:**
> No need for VNC or Remote Viewer!!! Simply allow remote desktop connections on the XP machine and use "terminal server client" (search for it on your PC, if you don't have it, try the Ubuntu Software Centre) to connect to it from Ubuntu!

I've enabled the XP box for remote

how do I find it from the ubuntu side
or more importantly the ubun boxes from the windows side?

---

### Post by d4m1r on 2011-10-16
> **Garthhh said:**
> I've enabled the XP box for remote

how do I find it from the ubuntu side
or more importantly the ubun boxes from the windows side?


Find what? The Windows PC? Well, if you have Terminal Server Client installed (it's installed by default in 11.04 at least) simply enter the IP address (or localhost name if internal network) and it will connect.

As for connecting Windows XP->Ubuntu I am not sure about a built in method, but VNC and TeamViewer (easier to setup) will work, just you'll have to install them separately in both XP and Ubuntu.

---

