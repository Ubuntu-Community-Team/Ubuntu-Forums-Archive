---
title: "ssh Remote vncviewer not opening"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-26
Hi all,

Getting into the realms of ssh and finding it very interesting. Seems it can do a lot...

Anyway, so far i am logging into my server from a laptop, in a terminal; ssh [email]username@server.ip.addr[/email]ess

If I do this with ssh -X I believe I should be able to open graphical packages from the server on my remote client?

I type vncviewer localhost: :5900 for example and it says all the right things in the terminal, logging on etc, but no seperate viewer window opens?

What am I doing wrong?


Incidently, if I just try and remote desktop from the laptop by just going vncviewer ip.address.of.server it also does the same thing, the vncviewer window doesn't open?

Hope you can help.

---

### Post by eldragon on 2008-06-26
> **jcr1 said:**
> Hi all,

Getting into the realms of ssh and finding it very interesting. Seems it can do a lot...

Anyway, so far i am logging into my server from a laptop, in a terminal; ssh [email]username@server.ip.addr[/email]ess

If I do this with ssh -X I believe I should be able to open graphical packages from the server on my remote client?

I type vncviewer localhost: :5900 for example and it says all the right things in the terminal, logging on etc, but no seperate viewer window opens?

What am I doing wrong?


Incidently, if I just try and remote desktop from the laptop by just going vncviewer ip.address.of.server it also does the same thing, the vncviewer window doesn't open?

Hope you can help.

in order to tunnel vnc through ssh, you have to set the tunnel first. for this, you ought to do

```

$ ssh -L 5900:localhost:5900 username@server

```

THEN you have to do vncviewer localhost

that should do it.


make sure you have the vnc server running on the server first.

good luck

---

### Post by wormser on 2008-06-26
> **eldragon said:**
> in order to tunnel vnc through ssh, you have to set the tunnel first. for this, you ought to do

```

$ ssh -L 5900:localhost:5900 username@server

```THEN you have to do vncviewer localhost


When you run the vncviewer you need to specify the local port.  In this case it would be 5900.

```
vncviewer localhost:5900
```

---

### Post by eldragon on 2008-06-26
> **wormser said:**
> When you run the vncviewer you need to specify the local port.  In this case it would be 5900.

```
vncviewer localhost:5900
```

no you dont, not if you are using the default port which is 5900

Something should i add:

the -X option is for worwarding X server calls or whatever they are called from the server machine to the X client in the ssh client machine....
vnc is another protocol alltogether that sends screengrabs from the X client on the server side to the vnc client on the the other side.

i dont know if im clear enough....i thing i tangled the explanation somewhere....might be that extra glass of wine :(

---

### Post by jcr1 on 2008-06-30
Thanks for this!

Any ideas on the reason why my remote window isn't opening? This is nothing to do with network set up or anything I don't think, this seems to be a problem with vnc itself I think.

Within my lan, if I go 'vncviewer ip.of.server' it looks like it does all the right stuff in the terminal, but no remote window opens up?

Same if I do it from tsclient or via webpage and tightvncjava.

---

