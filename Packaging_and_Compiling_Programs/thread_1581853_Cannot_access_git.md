---
title: "Cannot access git"
date: 2010-09-25
forum: Packaging and Compiling Programs
---

### Post by jfreak_ on 2010-09-25
so I am behind a proxy and I cannot access 
```

git clone http://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/libfm

```

It throws up this error
Initialized empty Git repository in /home/jfreak/libfm/.git/
fatal: [http://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/libfm/info/refs](http://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/libfm/info/refs) not found: did you run git update-server-info on the server?

I am pretty sure that nothing is wrong with the server

Output of echo $http_proxy is correct

I have tried replacing http with git  but that throws up
```

pcmanfm.git.sourceforge.net[0: 216.34.181.91]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)

```

---

### Post by gmargo on 2010-09-27
On sourceforge, you have to use the **git:** protocol, not the **http:** protocol.
```

git clone git://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/libfm

```Your firewall will need to unblock port 9418.

---

### Post by jfreak_ on 2010-09-27
When i use git: protocol, the second error is displayed.
I ran telnet localhost 9418 and it indeed says that the port is blocked. How do i open it?

---

### Post by gmargo on 2010-09-27
Why did you need an **http_proxy**?  Are you behind some corporate firewall?  Then you've got to talk to whoever's in charge of that.

---

### Post by jfreak_ on 2010-09-27
I am behind the college proxy. The college does not have any restrictions on content except porn and torrents. Hard to see why they would block this.

---

### Post by gmargo on 2010-09-28
Use telnet to test access to the foreign server, not localhost. localhost will fail unless you are running a local git server:
```

$ telnet pcmanfm.git.sourceforge.net 9418
Trying 216.34.181.91...
Connected to gitscm.sourceforge.net.


```

---

### Post by jfreak_ on 2010-09-29
telnet also giving connection refused.

---

