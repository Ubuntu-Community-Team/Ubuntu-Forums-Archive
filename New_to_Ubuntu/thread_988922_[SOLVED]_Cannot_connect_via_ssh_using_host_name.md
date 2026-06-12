---
title: "[SOLVED] Cannot connect via ssh using host name"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Maverick1712 on 2008-11-21
Hi all

I have been tinkering away at my setup for a few months now, and now something that was relatively low priority (but always kind of inconvenient) has reached the top of my list. I've got a laptop and a desktop as many people do, with an ssh server on the desktop. I only access the ssh server from within my own wireless network so I haven't setup static IPs or things of that nature yet (that's a few more items down my action list). The problem I am having is that I cannot connect via ssh using the host name. Using the IP address will work however. Any idea why my laptop cannot seem to resolve the host name of my desktop? I figure this is a simple configuration issue but haven't been able to find it.

Cheers and thanks,
Adam

---

### Post by iponeverything on 2008-11-21
just add the machines to the hosts file on each machine. ;) I know that doesn't sound right.. just trying to get it in as few words as possible.

---

### Post by Maverick1712 on 2008-11-21
I don't stray too far from the home folder, in all of it's cozziness. Where is the hosts file located? And do I need to add machine name and IP?

Cheers,
Adam

---

### Post by Maverick1712 on 2008-11-21
Ok so I found a file named host in /usr/bin, but when i try to open it with evim, I get a bunch of gibberish characters. When I try to open it with gedit, it won't even let me due to a character encoding issue. How would I go about adding my desktop's hostname to the file?

Cheers,
Adam

---

### Post by iponeverything on 2008-11-21
> **Maverick1712 said:**
> I don't stray too far from the home folder, in all of it's cozziness. Where is the hosts file located? And do I need to add machine name and IP?

Cheers,
Adam

It's  /etc/hosts on linux and I don't know where it lives in windows -- but I pretty sure it has one.

oh.. and the format will be easy to understand when you look at the file.

---

### Post by Maverick1712 on 2008-11-21
Good thing both my machines are Ubuntu :P. Thanks for the help.

Cheers,
Adam

---

### Post by Zack McCool on 2008-11-21
/etc/hosts

But this may present a problem if your ip changes frequently.  The mapping in the hosts file is a static mapping, so you should also consider setting static IPs on each of the machines.

The reason it cannot resolve it now is that you do not have a DNS server for your local network.  The router forwards DNS requests out to the ISP, but the ISP does not know the host names of the machines on your local LAN.

---

