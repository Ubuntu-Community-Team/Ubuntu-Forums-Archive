---
title: "Perl script help!"
date: 2006-10-16
forum: Programming Talk
---

### Post by nexus024 on 2006-10-16
When I try and execute this perl script it gives me this error message each time: "Reason: invalid argument"  I executed this script fine on my windows box but when I try to run it on ubuntu it gives that error message.  Anyone know why its doing this?

```
#!/usr/bin/perl

use IO::Socket;
$port=27960;
$count=0;

while (count <= 1) {
$sock=new IO::Socket::INET (PeerAddr=>monster.idsoftware.com, PeerPort=>27950, Proto=>'udp', LocalPort=>$port) or die ("Reason: $!\n");
print $sock "\xFF\xFF\xFF\xFFheartbeat QuakeArena-1\x0A";
close ($sock);
$count++;
sleep(2);
}
```

---

### Post by girishv on 2006-10-16
Hi, a simple quoting of the url seems to solve the problem. Please check it out

girish

---

### Post by bswilson on 2006-10-16
Have you run this through **perl -wc** on your Linux box to collect the specific errors and line numbers?

---

### Post by souki on 2006-10-16
there is also a '$' missing
while (**$**count ...

---

### Post by nexus024 on 2006-10-16
Ok i fixed those errors and it now says "Reason: address already in use" and also perl -wc says it is using correct syntax.

---

### Post by nexus024 on 2006-10-16
I believe the problem is that I am running a game server on port 27960.  When I change the localport in the script to 27961 it runs fine.... but I need to be able to run it on the same port 27960.  Is there anyway to do this while also running a server on the same port?

---

### Post by souki on 2006-10-17
you cannot run two listeners on the same port
instead, you have to catch every packet and displatch/relay them
maybe you can also multicast them : [http://www.foo.be/scripts/mcast2bcast/mcast2bcast.pl](http://www.foo.be/scripts/mcast2bcast/mcast2bcast.pl)

---

