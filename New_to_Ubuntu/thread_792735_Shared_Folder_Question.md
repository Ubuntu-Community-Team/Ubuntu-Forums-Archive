---
title: "Shared Folder Question?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by mapes12 on 2008-05-13
I right click on the folder I want to share.

Then "Share Folder"

Then Share through Unix networks NFS (from the drop down list. This is the only package I have installed because the two boxes I'm connecting are running Ubuntu, not XP).

Then Allowed Hosts "Add"

this is where I get stuck. It asks me to Specify Hostname.

What do I need to enter??

---

### Post by tacutu on 2008-05-13
the IP or hostname of the computer(s) allowed to access the shared folder.

Typically, in a home network it will be something loke 192.168.0.<something>

---

### Post by pedro_orange on 2008-05-13
Enter the hostname :)

eg. yourname-laptop

My laptop is pedro-laptop

If you open a terminal you get the prompt: pedro@pedro-laptop:~$

Which I think means: user@computer-name: dir shell

~ being home and $ being bash prompt.

EDIT: Entering IP can be dodgy on DHCP networks! :) (Unless you've set up Statics!)

---

### Post by mapes12 on 2008-05-13
The terminal prompt on the machine I want to share the folder with is:

```
mark@ubuntu:~$
```

so the hostname I need to type us "ubuntu", yes?

The only problem I can see is that the terminal prompt name on this machine is the same  :(  Will this cause a problem.

Thanks for the heads up re IP addresses and yes IP's are assigned by DHCP.

---

### Post by pedro_orange on 2008-05-13
Two identical hostnames on the same network can cause problems yes. 

You may be better off assigning them static IP addresses (go into your router and assign them via MAC address) and then you can map to the other hosts via the IP address.

I'm not sure about the implications of having 2 identical hostnames on a network.
Perhaps the hosts may get confused and try and send the request to themselves!

---

### Post by mapes12 on 2008-05-13
These machines are only test boxes for messing around so I'm happy to change the hostname on one of them to avoid any network configuaration issues.

Problem is, how do I change one of my boxes hostnames?

Any idease?  :?:

---

### Post by tacutu on 2008-05-13
Let's say you have 2 PCs: one has the hostname "laptop" and one "desktop". From "desktop" you can't just reach "laptop". The name must be first translated into an IP address. THis can be achieved by adding, on "desktop" an entry in /etc/hosts which reads:
```
192.168.0.X laptop

```
so you're back to IP addresses basically. Just assign them static IPs (from the router), I don't know if you can do what you want with dynamic IPs)

---

