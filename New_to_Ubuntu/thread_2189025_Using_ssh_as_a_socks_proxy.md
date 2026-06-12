---
title: "Using ssh as a socks proxy"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by wolfenstein538 on 2013-11-20
Hello,

I know it is possible, but is there an tutorial which explains everything? I only find websites, which explains which command you will need to use in order to use it securely. I mean, you obviously need to configure ssh and a proxy server right? And do I need to forward some ports in order to use it externally?

Once again, many thanks in advance.

---

### Post by Lars Noodén on 2013-11-20
If you mean using it with your web browser, then there are only two things you need to do.  You need to set up an SSH connection, which creates a SOCKS proxy, and then point your browser at it.  

```
 
ssh -D 9876 server.example.org

```

That gives you a SOCKS proxy locally (localhost) at port 9876.  Set your browser to use it.  

Then go into about:config and set *network.proxy.socks_remote_dns* to **true**.  

In that way all your web activity will come from the server rather than locally.  

There is little written because it is not complicated to set up.

---

### Post by wolfenstein538 on 2013-11-20
But what do I have to do, if I want to connect to the ssh proxy, externally? Do I need to forward any ports? I have a crappy homerouter, on which it is nearly impossible to forward any ports.

---

### Post by Lars Noodén on 2013-11-20
The proxy is local to your ssh client which then tunnels the connection to the remote computer. 

If you want your notebook or whatever to have its web activity come via your home computer, you'll have to set up port forwarding from your router: you need a connection from wherever you are to the machine you will ssh into.  Alternately you can rent a VPS.

The proxy is good to have when using public wi-fi and such.

---

