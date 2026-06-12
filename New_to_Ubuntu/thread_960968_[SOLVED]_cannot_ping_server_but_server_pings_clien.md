---
title: "[SOLVED] cannot ping server but server pings client"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by TJCIB on 2008-10-27
I am running NIS for logging into a network of 10 computers

On bootup, the clients fail to Bind to YP server...
which I interpret as them not being able to communicate with the NIS server.

However the server can ping the clients, but the clients cannot ping the server

I've disabled the firewall on the router, but that shouldn't be the problem, we have had no hardware changes.  Perhaps an update messed something up.  I'm running Gutsy.

Here is the output of "rpcinfo -p"

```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  52304  status
    100004    2   udp    800  ypserv
    100004    1   udp    800  ypserv
    100004    2   tcp    801  ypserv
    100004    1   tcp    801  ypserv
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  52117  nlockmgr
    100021    3   tcp  52117  nlockmgr
    100021    4   tcp  52117  nlockmgr
    100005    1   udp  32771  mountd
    100005    1   tcp  51165  mountd
    100005    2   udp  32771  mountd
    100005    2   tcp  51165  mountd
    100005    3   udp  32771  mountd
    100005    3   tcp  51165  mountd

```

The clients have portmapper, status, and ypbind running from the same command

Any help would be great, my students are bugging me so they can get back to playing Mahjongg

PS - I booted into recovery mode on a client and tried commenting out NFS mounts in fstab, that didn't have an effect.

---

### Post by TJCIB on 2008-10-28
Does the server also need "ypbind" running?

Would ports be blocked on the server so they don't accept incoming, but still can communicate with an outgoing ping?

I'm not up to par on these network issues.

---

### Post by Sarmacid on 2008-10-28
Maybe there's a firewall running on the server?

To check for iptables rules
```
iptables -L
```

---

### Post by TJCIB on 2008-10-28
Output from iptables -L

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6112:6119 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:49200 
DROP       0    --  anywhere             anywhere            state INVALID,NEW 
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  localhost            anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            state INVALID,NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

It appears the first line is a Battle.net setting, since those are its ports
not sure what the second line is.

Other than that it is borderline greek to me...

---

### Post by TJCIB on 2008-10-28
I flushed my iptables with -F
and basically reset them.  This is what they look like now.

Server still is not accepting pings and the NIS clients are still not binding to the server.

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  localhost            anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

### Post by Sarmacid on 2008-10-29
You did flush iptables, but still the main policies are on drop> **TJCIB said:**
> Chain INPUT (policy DROP)

To fix this, just run this```
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F

```

So if this works for you, now you know you'll have to play around with iptables and adjust it to your needs.

---

### Post by TJCIB on 2008-10-30
Thank you, fixed that.  But the clients still cannot even ping the server.
I have tried disconnecting the lab from the router, just in case it has some hidden firewalls or settings I can't find, but same result.

Also, when starting NIS, the server attempts to bind to itself and fails to do so...weird.

So the question remains, why can't my clients talk to my server?


Here is iptables -L just in case again
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     0    --  localhost            anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by Sarmacid on 2008-10-31
Maybe the ip addresses or netmasks are set incorrectly. Can you post the output of ifconfig on the server and one of the machines?

---

### Post by TJCIB on 2008-10-31
If the net masks were wrong, would the server be able to ping the client?

I knew it was a setting somewhere on the server, because booting the server from LiveCD gave the ability to communicate freely between all the clients.

The server is basically a file server and NIS server, nothing else.  

So to resolve it, I backed up the /home directories of the 40 users and did a  full reinstall.  Which isn't bad because I use apt-cacher on a separate server, so updating takes no time.

I restored the /home directories and we're back up and running in about 3 hours.

Thanks for the help.  I couldn't waste any more time finding the problem.  A week of no computers in a school doesn't work.

---

