---
title: "Command to resolve real hostname?"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by hkarn on 2012-01-23
Hello,

I need some general linux help. I have looked over the commands for dns lookup but can't seem to find one other then ping that does what I want.

Here is what I need:

- I know the no-ip service hostname
- I need the actual hostname not the IP of the IP the no-ip service is used to

ping will do this it shows the actual hostname and IP when it starts pinning but I would prefer not to use ping.

Also I need this done from a shell command file. So I can't simply take the IP and do another lookup manually cause that should work.

---

### Post by SuaSwe on 2012-01-23
What about nslookup? 

```

suaswe@lxpc~$ nslookup bbc.co.uk
Server:      192.168.0.1
Address:     192.168.0.1#53

Non-authoritative answer:
www.bbc.co.uk   canonical name = www.bbc.net.uk            <========
Name: www.bbc.net.uk  
Address: 212.58.244.71 

```

Is this what you mean?

---

### Post by hkarn on 2012-01-25
No, that doesn't work.

I have a no-ip host redirect and need the actual host name.

I need to get the host name that resolves backwards from the IP. By using another host alias that doesn't resolve booth ways but only to the I.

nslookup and everything else I have tried just give me the alias I enter and the ip. I need to run it again manually on the IP to reselve to the actual domain I want to know. 

But I need it to happen in one go in a script...

Ping will show the actual domain name when it starts pinging but nothing else I found.

---

### Post by hkarn on 2012-01-25
Solved it by installing nmap

nmap -sL host

responds with rDNS record line showing the IP and hostname I am looking for.

The -sL flag in nmap should be less then a ping right? It only does dns request?

---

