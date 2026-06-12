---
title: "Open a port on a router on the network."
date: 2009-09-09
forum: Programming Talk
---

### Post by NESFreak on 2009-09-09
Hi, I'm writing a small python script. Part of it needs to listen on a predefined port for incoming messages from over the Internet. The problem is that it would most of the time be behind a router. How do i tell the router to forward the port to me (many p2p programs for instance already support this, however i couldn't find a singe bash, nor python function for this)?

thanks in advance.

---

### Post by dwhitney67 on 2009-09-09
Configure your router to forward the data coming in on port "A" to the port "B" that your app is listening on.

The port "A" that you advertise to your peers does *not* have to be the same as the port "B" that your app listens on, however it can be the same.

If your router is "lame" (such as mine, which is the Linksys WRT54G) and it does not permit port-forwarding from a port "A" to a port "B", then you can consider using the application called "redir".  I believe the following is needed, and then you will need to reference the help-manuals to setup the configuration:
```

sudo apt-get install redir

```


P.S.  If you have a Linksys Router (WRT54G), then there exists a special OS for it called "tomato".  I have not used it, but I have heard good things about it.

---

### Post by mikewhatever on 2009-09-09
You can do it using the router's interface, which is different on every model. The site below might help.
[http://portforward.com/](http://portforward.com/)

---

### Post by Can+~ on 2009-09-09
Old Linksys (not wireless) have that option under:

Application & Gaming > Port Range Forwarding.

It's a common procedure, you code with ports as you would normally, and then redirect ports accordingly.

---

### Post by johnl on 2009-09-09
I believe what you are referring to is uPnP.  If your router supports this, you can request that it automatically set up port forwarding for you (see: [uPnP NAT traversal](http://en.wikipedia.org/wiki/Universal_Plug_and_Play#NAT_traversal).  As for how you would code this, I haven't the foggiest idea.  Try googling for uPnP, IGD, NAT Traversal, etc.

Hope this helps.

---

### Post by NESFreak on 2009-09-09
> **johnl said:**
> I believe what you are referring to is uPnP.  If your router supports this, you can request that it automatically set up port forwarding for you (see: [uPnP NAT traversal](http://en.wikipedia.org/wiki/Universal_Plug_and_Play#NAT_traversal).  As for how you would code this, I haven't the foggiest idea.  Try googling for uPnP, IGD, NAT Traversal, etc.

Hope this helps.

I was indeed referring to upnp. However i was wondering if there wasn't just a simple program available that would just do something like
 
forward [router ip] [router port] [my ip] [my port]

and that being all.

---

### Post by johnl on 2009-09-09
Hi, 

try downloading miniupnp**c** (not d) from here: [http://miniupnp.free.fr/files/](http://miniupnp.free.fr/files/) and compiling it.  It should generate a file 'upnpc-shared'


```

./upnpc-shared
upnpc : miniupnpc library test client. (c) 2006-2009 Thomas Bernard
Go to [http://miniupnp.free.fr/](http://miniupnp.free.fr/) or [http://miniupnp.tuxfamily.org/](http://miniupnp.tuxfamily.org/)
for more information.
Usage : ./upnpc-shared [options] -a ip port external_port protocol
                Add port redirection
        ./upnpc-shared [options] -d external_port protocol [port2 protocol2]Â*[...]
                Delete port redirection
        ./upnpc-shared [options] -s
                Get Connection status
        ./upnpc-shared [options] -l
                List redirections
        ./upnpc-shared [options] -r port1 protocol1 [port2 protocol2] [...]
                Add all redirections to the current host

```

It looks like the "-a" option will do exactly what you want.  It will automagically discover your router IP if the router is UPnP compatible.

Hope this helps.

---

