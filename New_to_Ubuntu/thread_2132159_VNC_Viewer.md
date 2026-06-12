---
title: "VNC Viewer"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by pimpn on 2013-04-03
I have used VNC viewer on my windows cpu to access my Ubuntu machine remotely for a few years now with no problems.  I installed the latest round of updates for Ubuntu 12 lts and all of a sudden i can no longer access my Ubuntu machine remotely or even on my LAN for that matter.  I have deleted my network wired connection and started a new one there and that fixed my network access locally but still can not access through VNC?  i have checked the ip in case that had changed but it's all the same still.  Any ideas?  Oh and i set up a VPN access for file access while on the road and that no longer works either.

---

### Post by pimpn on 2013-04-06
Anyone?  Am I missing some info that would help here?

---

### Post by steeldriver on 2013-04-06
(sorry if this is obvious) have you enabled Desktop Sharing? 

what does 

```
 sudo netstat -nlp | grep vino
```

say? do you have a firewall running on the target machine and if so is the VNC port open (unless you are tunneling VNC over SSH)? 

```
 sudo ufw status
```

---

### Post by pimpn on 2013-04-06
I do have a firewall and yes it's port is open.  I had DT operating just fine for a year or two until this update.  I will check and see if perhaps DT share got turned off during the update.

---

### Post by pimpn on 2013-04-06
Sorry... not DT VNC.

---

### Post by pimpn on 2013-04-06
> **steeldriver said:**
> (sorry if this is obvious) have you enabled Desktop Sharing? 

what does 

```
 sudo netstat -nlp | grep vino
```

say? do you have a firewall running on the target machine and if so is the VNC port open (unless you are tunneling VNC over SSH)? 

```
 sudo ufw status
```

vino shows up in red on the screen and IP address seem to show all 0's followed by a port number.

---

### Post by pimpn on 2013-04-07
Anyone know what this tells me?  Thank-you.

---

### Post by steeldriver on 2013-04-07
> **pimpn said:**
> vino shows up in red on the screen and IP address seem to show all 0's followed by a port number.

> **pimpn said:**
> Anyone know what this tells me?  Thank-you.

If you're seeing the vino-server listening at 0.0.0.0:5900 that means it should be accepting connections on port 5900 from any IP I think - so that's all as it should be - the red color is just the default highlighting from grep

Did you run the ufw command as well?

---

