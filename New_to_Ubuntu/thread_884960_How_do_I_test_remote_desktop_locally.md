---
title: "How do I test remote desktop locally?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by anewguy on 2008-08-09
I have installed lamp, tightvnc and the tighvnc java.  It appears to work when I [http://192.168.1.2/remotedesktop](http://192.168.1.2/remotedesktop).  I would like to know if there is a way to "force" a test out across the internet and back in, and what the syntax would be.  Everytime I try to find my IP address it is just the IP address of the router.  I need to know how to go across the net, in my router and out to my PC.  I tried adding a port number on http request, but it still just sits there as it thinks it is trying to connect to just my router.

Thank you in advance! :)

---

### Post by bpowell2005 on 2008-08-09
> **anewguy said:**
> I have installed lamp, tightvnc and the tighvnc java.  It appears to work when I [http://192.168.1.2/remotedesktop](http://192.168.1.2/remotedesktop).  I would like to know if there is a way to "force" a test out across the internet and back in, and what the syntax would be.  Everytime I try to find my IP address it is just the IP address of the router.  I need to know how to go across the net, in my router and out to my PC.  I tried adding a port number on http request, but it still just sits there as it thinks it is trying to connect to just my router.

Thank you in advance! :)

You just need your external IP address...there are web sites ([www.showmyip.com](www.showmyip.com)) which can tell you your external IP address, or it can probably be found in your routers "status" page. Then just replace 192.168.1.2 with your external address...you'll probably need to forward some ports on the router as well.

---

### Post by anewguy on 2008-08-09
They are all internal router ip's.  When I try showmyip, it gives me the router ip, but I have never gotten anywhere using that.  I am already forwarding ports 80 and 5900-5905.  I have tried the router address with a port specified - still no go.  I have set up a free domain via no-ip.com, but again it only sees the router address.  Nothing ever connects when just going to the router address.  Is there some special syntax or something that I am missing?  What if I was on my friends' computer and wanted to get control over my home PC - how do I address it through the router?

Thanks! :)

---

### Post by MobiusNZ on 2008-08-09
A lot of routers won't handle forwarding through the external IP address when both the source and the destination is internal. The only way you could test remote access locally is by remoting on to a remote computer and trying to remote back to your one from there...

---

