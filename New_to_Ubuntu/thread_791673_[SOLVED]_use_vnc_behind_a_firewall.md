---
title: "[SOLVED] use vnc behind a firewall"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by philphil on 2008-05-12
Hi,

I'm trying to set up my remote desktop so I can access my computer from university.  I can set it up so it works on port 5900 and other people can connect to this and all works fine.  Unfortunately, this port is blocked when I try to remote desktop to my pc from uni using VNCViewer on a uni machine.  So, my solution is to use a port under 1024, right? I think that should work.  If not, let me know.  I'm trying to use it on port 22 (SSH) at the minute but I can't get it to work.  

If I set up remote desktop to use 5900 and I run "vncviewer localhost:5900" from a terminal then it works and I connect.  If I set it up to use port 22, port 80, or a whole bunch of other ports I've tried it says "connection error: connection refused".

I've opened the port using Firestarter so that port 22 can be accessible by anyone but still nothing, I can't connect.  It's clearly not my netgear router getting in the way (though I have port 22 forwarded to my local IP address), it must be something on my laptop that's stopping it from working.

Any ideas?

Cheers.

---

### Post by gr@nt on 2008-05-12
> **philphil said:**
> Hi,

I'm trying to set up my remote desktop so I can access my computer from university.  I can set it up so it works on port 5900 and other people can connect to this and all works fine.  Unfortunately, this port is blocked when I try to remote desktop to my pc from uni using VNCViewer on a uni machine.  So, my solution is to use a port under 1024, right? I think that should work.  If not, let me know.  I'm trying to use it on port 22 (SSH) at the minute but I can't get it to work.  

If I set up remote desktop to use 5900 and I run "vncviewer localhost:5900" from a terminal then it works and I connect.  If I set it up to use port 22, port 80, or a whole bunch of other ports I've tried it says "connection error: connection refused".

I've opened the port using Firestarter so that port 22 can be accessible by anyone but still nothing, I can't connect.  It's clearly not my netgear router getting in the way (though I have port 22 forwarded to my local IP address), it must be something on my laptop that's stopping it from working.

Any ideas?

Cheers.

I would suggest using port 21, as this is used for ftp, most likely it is open at your varsity, alternatively you could try using port 25, but i would recommend using port 21 first.

Cheers

---

### Post by philphil on 2008-05-13
thanks, I have it working now, it was done to some retarded firewall issue, port forwarding wasn't forwarding to the right IP as for some reason when I connect to my router sometimes it knows who I am and assigns me the requested IP address i.e. 192.168.0.2 other times it doesn't know who I am and assigns me a different number.  Weird and it's because sometimes I have a different MAC address when I connect, which is also weird and I can't explain.

---

