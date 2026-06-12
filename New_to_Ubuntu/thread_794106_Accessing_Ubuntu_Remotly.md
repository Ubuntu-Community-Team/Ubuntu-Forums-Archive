---
title: "Accessing Ubuntu Remotly"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-14
Hi Guys,

I would like to access my Ubuntu machine remotely over the internet using SSH and VLC..

When i attempt to make a connection to my machine via PUTTY SSH i get "Connection Refused"

With regards to VLC... do I need to download a VLC Server for my machine, or is it simply a question of allowing VLC connections from somewhere in GNOME?

Thanks for your Tips PPL!

Mark :)

---

### Post by OffAxis on 2008-05-14
> When i attempt to make a connection to my machine via PUTTY SSH i get "Connection Refused"
Have you installed **ssh**?
```
sudo apt-get install ssh
```

it's a metapackage with both a client and server. Default uses port 22.

As for VLC, the standard install has a server built into it. It's not an issue of allowing connections through gnome (if you've got VLC installed and running then it's listening on the port you specified), it's your firewall that you'll need to make sure the ports are open on or forwarded, be it firestarter or a router based hardware one.

---

### Post by markbusu on 2008-05-14
Thanks for that m8... all sorted!

---

### Post by OffAxis on 2008-05-14
If you do have ssh installed on your ubuntu box then the port is probably not being properly forwarded through your firewall;

destination IP could be wrong in putty (are you using your router's WAN IP?)
the port could be blocked (remedy in the router setup page)
the port forward on your router might not be going to your ubuntu box (remedy in the router setup page)

[I]Edit:
Glad to hear you worked it out[/I]

---

