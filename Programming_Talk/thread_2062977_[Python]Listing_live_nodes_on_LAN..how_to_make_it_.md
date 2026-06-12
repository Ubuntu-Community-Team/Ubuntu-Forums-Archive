---
title: "[Python]Listing live nodes on LAN..how to make it fast?"
date: 2012-09-26
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2012-09-26
```

import socket 
from socket import gaierror,herror 
ip='192.168.0.' 
name={ ##name resolver 'Dhir':'Dhiraj PC'## } 
for i in range(100,110): 
    add=ip+str(i) 
    try: 
        up=socket.gethostbyaddr(add)[0] 
        if(name.has_key(up)): 
            print add+'--{'+name.get(up)+'} is up!' 
        else :  
            print up+' is up!' 
    except herror: 
        pass 
         

```This is my code...is there any way to make it fast....i can tolerate 3 sec delay but not more than 5 second when checking for every node..

---

### Post by Tony Flury on 2012-09-26
How many nodes on your network ?

I think 5 seconds to check on 10 potential nodes - i.e. 1/2 second for each node is not bad considering. 

I note that with your code it is actually only looking for one node (as defined in the name dictionary), so why not loop around the name dictionary and do a gethostbyname, rather than go through 10 IP addresses looking for one name ?

also strictly speaking you should be using 

```

if up in name:

rather than

if name.has_key(up): ## has_key is deprecated in Python 2.7 

and 

since you already know that the key exists, you can use : 

name[up]

rather than

name.get(up)

```

Also from what i understand (i might be wrong) that gethostbyname and gethostbyaddr don't actually tell you if the node is live - it simply resolves the dns lookup - or does a reverse DNS lookup, and the DNS entry can exists by the actual node could be dead - unless your network does some dynamic DNS deal.

To check if the node is alive you may well need to execute a ping or similar.

---

### Post by juancarlospaco on 2012-09-27
Talk to the Broadcast, not by range()

ie: ping to broadcast

---

### Post by Dhiraj Thakur(Invincible) on 2012-09-27
> **juancarlospaco said:**
> Talk to the Broadcast, not by range()

ie: ping to broadcast

You mean like this?
```
os.system("ping -b -c 3 192.168.0.255")

```


> **Tony Flury said:**
> How many nodes on your network ?

I think 5 seconds to check on 10 potential nodes - i.e. 1/2 second for each node is not bad considering. 

I note that with your code it is actually only looking for one node (as  defined in the name dictionary), so why not loop around the name  dictionary and do a gethostbyname, rather than go through 10 IP  addresses looking for one name ?

also strictly speaking you should be using 

```

if up in name:

rather than

if name.has_key(up): ## has_key is deprecated in Python 2.7 

and 

since you already know that the key exists, you can use : 

name[up]

rather than

name.get(up)

```Also from what i understand (i might be wrong) that gethostbyname  and gethostbyaddr don't actually tell you if the node is live - it  simply resolves the dns lookup - or does a reverse DNS lookup, and the  DNS entry can exists by the actual node could be dead - unless your  network does some dynamic DNS deal.

To check if the node is alive you may well need to execute a ping or similar.
I have to check for live nodes not particular nodes..and i have about 4-5 computers connected via a switch..
and my code is taking upto 5-6 seconds for every ip lookup..this is what's bugging me..
and about gethostbyname/addr...what else can i do to find names of comp. on my network?

---

### Post by ofnuts on 2012-09-27
> **Dhiraj Thakur(Invincible) said:**
> You mean like this?
```
os.system("ping -b -c 3 192.168.0.255")

```

I have to check for live nodes not particular nodes..and i have about 4-5 computers connected via a switch..
and my code is taking upto 5-6 seconds for every ip lookup..this is what's bugging me..
and about gethostbyname/addr...what else can i do to find names of comp. on my network?
Not expert enough in that side of Python, but I would definitely try to use one thread per host checked and start several threads in parallel.

---

