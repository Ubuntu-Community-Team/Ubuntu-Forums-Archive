---
title: "Troubles with ipvsadm running on Ubuntu 14.04.4 x64"
date: 2016-05-10
forum: New to Ubuntu
---

### Post by smitty2 on 2016-05-10
First off, I'm trying to create a "cloud-based" load balancer to pass traffic back and forth between two Icecast2 servers (both hosting content on port 8000 on different networks than my load balancer). I have searched and searched the Internet and can't find the resolution to my problem.

I'm a newbie so please be gentle. :)

Jumping ahead a bit... ipvsadm is installed and "seems" to be working.

The following is my ipvsadm.rules file (located /etc/ipvsadm.rules)

```

-A -t icy.hostedbysmitty.com:8000 -s rr
-a -t icy.hostedbysmitty.com:8000 -r icynyc1.hostedbysmitty.com:8000 -g -w 25
-a -t icy.hostedbysmitty.com:8000 -r 66-237-51-34.starstream.net:8000 -g -w 75

```

Explanation of the above code.
-A is the server where ipvsadm is installed (14.04.4 x64 - the load balancer/director and same place ipvsadm is installed)
-a Server #1 hosting content on port 8000
-a Server #2 hosting content on port 8000

I'd like 25% of the traffic to go to server 1, 75% to server 2.

When I type command "root@icy:~# nano /etc/default/ipvsadm this is what I see:

```

# ipvsadm


# if you want to start ipvsadm on boot set this to true
AUTO="true"


# daemon method (none|master|backup)
DAEMON="master"


# use interface (eth0,eth1...)
IFACE="eth0"


# syncid to use
SYNCID="1"

```

When I type command "root@icy:~# ipvsadm -l" this is what I see:

```
IP Virtual Server version 1.2.1 (size=4096)
Prot LocalAddress:Port Scheduler Flags
  -> RemoteAddress:Port           Forward Weight ActiveConn InActConn
TCP  icy.hostedbysmitty.com:8000 rr
  -> icynyc1.hostedbysmitty.com:8 Route   25     0          0
  -> 66-237-51-34.starstream.net: Route   75     0          0

```

When I visit [http://icy.hostedbysmitty.com:8000](http://icy.hostedbysmitty.com:8000) I get nothing.  What I should see either server 1 or server 2's status page (seen here: [http://icynyc1.hostedbysmitty.com:8000/](http://icynyc1.hostedbysmitty.com:8000/))... 

What am I missing? I feel like I'm VERY close!

Any help is appreciated and please be gentle. Been learning Ubuntu on my own like many others.

---

### Post by smitty2 on 2016-05-10
Hoping someone will see this and know what's up. Still having what appears to be a timeout issue. I'm pretty sure the requests on port 8000 are working.

As you can see:
```

root@icy:~# ipvsadm -L -n --stats
IP Virtual Server version 1.2.1 (size=4096)
Prot LocalAddress:Port               Conns   InPkts  OutPkts  InBytes OutBytes
  -> RemoteAddress:Port
TCP  198.211.116.166:8000               16       49        0     2556        0
  -> 198.211.110.129:8000                8       26        0     1388        0
  -> 66.237.51.34:8000                   8       23        0     1168        0

```

However when I hit [http://198.211.116.166:8000](http://198.211.116.166:8000) from a browser, I never get redirected.

---

