---
title: "Getting access to server behind router remotely via SSH"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by iangarforth on 2012-03-05
Hi all,

I suppose I mainly want to ensure I understand this right.  I've been playing around with installing an Ubuntu server at my school.  I want to SSH in to work on it from home.  I can connect fine when in school, but from outside I can't.

Am I right in saying I need to get my Sysadmin to configure a port on the router that forwards to the IP of my server?

Further - and separately - is it correct to say that on the SSH server on my Ubuntu server, I should change the port from 22 to something else (which is quite separate to the port forwarding on the router).

Then, from outside, I just connect to the public IP of the router (found from whatsmyip.com) and the specified port, and that forwards me to my server, where I log in as usual (but not as root, which should be disabled?)

Have I got that right..?

---

### Post by jailbait on 2012-03-05
> **iangarforth said:**
> Hi all,

I suppose I mainly want to ensure I understand this right.  I've been playing around with installing an Ubuntu server at my school.  I want to SSH in to work on it from home.  I can connect fine when in school, but from outside I can't.

**1. **Am I right in saying I need to get my Sysadmin to configure a port on the router that forwards to the IP of my server?

Yes.

**2. **Further - and separately - is it correct to say that on the SSH server on my Ubuntu server, I should change the port from 22 to something else (which is quite separate to the port forwarding on the router).

Setup SSH Keys. Their much more secure than password based auth. See [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

**3. **Then, from outside, I just connect to the public IP of the router (found from whatsmyip.com) and the specified port, and that forwards me to my server, where I log in as usual (but not as root, which should be disabled?)

Depends.
Some schools have an corporate inbound filter, and or a non-static ip which they draw from an ip address pool belonging to the school board. They may also have packet-filtering on.

Even with my server at the University of Toronto, I ended up binding my own static ip pool (after banging heads with ARIN) because I was on a separate network.
Have I got that right..?


.

---

### Post by nd456 on 2012-03-05
That sounds correct to me, the difficult is getting access to port forwarding (assuming you're a student). I would highly recommend changing the port for security purposes... (here is a link to help)
[http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html](http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html)

---

