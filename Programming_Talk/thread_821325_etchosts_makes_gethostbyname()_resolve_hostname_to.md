---
title: "/etc/hosts makes gethostbyname() resolve hostname to 127.0.1.1"
date: 2008-06-07
forum: Programming Talk
---

### Post by dtk_ on 2008-06-07
Hey guys.
I'm doing some network programming in C with raw sockets (as I need to send ICMP packets).

In order to fill out the IP header, I need to know the IP of the box that is executing the code.
So I fetch the hostname with gethostname() and resolve it with gethostbyname(), which returns (a struct holding the IP) 127.0.1.1.
That's not too useful because I find it hard to receive responses to packets with that source IP ;P 

If I'm not absolutely wrong, this is due to the hostname alias in the /etc/hosts that is meant to avoid DNS requests for every call to gethostbyname() on machines that have dial-up connections.
If I delete that entry from the /etc/hosts, I get the error that the hostname couldn't be resolved as the connection timed out (_very_ quickly).

Can anybody tell me how to find out the IP of the current box in C?

TIA!
dtk

---

### Post by ul1984 on 2009-03-27
bump

---

### Post by bapoumba on 2009-03-28
Hmm..
Moved to PT.

---

### Post by init1 on 2009-03-28
> **dtk_ said:**
> Hey guys.
I'm doing some network programming in C with raw sockets (as I need to send ICMP packets).

In order to fill out the IP header, I need to know the IP of the box that is executing the code.
So I fetch the hostname with gethostname() and resolve it with gethostbyname(), which returns (a struct holding the IP) 127.0.1.1.
That's not too useful because I find it hard to receive responses to packets with that source IP ;P 

If I'm not absolutely wrong, this is due to the hostname alias in the /etc/hosts that is meant to avoid DNS requests for every call to gethostbyname() on machines that have dial-up connections.
If I delete that entry from the /etc/hosts, I get the error that the hostname couldn't be resolved as the connection timed out (_very_ quickly).

Can anybody tell me how to find out the IP of the current box in C?

TIA!
dtk
What IP are you looking for? The one you get from ifconfig? I can't say I know anything about gethostbyname(), but I think you need to specify the network interface. 127.0.1.1 is the IP of loopback. You would need to get the IP of eth0, or whatever your interface is named.

---

### Post by The Cog on 2009-03-28
I think you probably need to get a list of all IP addresses on all interfaces, and pick one. I forget what the call is to do this, but I know there is one. gethostaddresses or something like that maybe.

---

### Post by wmcbrine on 2009-03-28
What I do in this situation is to make a connection to some known site on the wider Internet -- which will use the default route, so it will use the correct interface -- and take the address from that. Yeah, it sucks, but it's the easiest way AFAIK.

Here's an example in Python. I know you were looking for C, but I don't have a C version handy. It would be pretty similar:

```

def get_address():
    try:
        address = socket.gethostbyname(socket.gethostname())
        # On my system, this always gives me 127.0.0.1. Hence...
    except:
        address = ''
    if not address or address.startswith('127.'):
        # ...the hard way.
        s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        s.connect(('4.2.2.1', 0))
        address = s.getsockname()[0]
    return address

```

---

### Post by tturrisi on 2009-03-29
[http://beej.us/guide/bgnet/output/html/multipage/gethostbynameman.html](http://beej.us/guide/bgnet/output/html/multipage/gethostbynameman.html)

---

### Post by SKLP on 2009-04-06
I've been having this problem with the mono call Dns.GetHostEntry(Dns.GetHostName()).AddressList[0]. It's been returning 127.0.1.1 which it shouldn't... Tried it today in my mono 2.5(trunk) installation, and now I'm getting the proper answer ;-)

Any ideas what to do as a jaunty quirk though? ( for mono server apps )

---

### Post by SKLP on 2009-04-06
I've now made a function based on what wmcbrine did in python:
boo function:
```
def GetLocalAddress():
		ip = Dns.GetHostEntry(Dns.GetHostName()).AddressList[0]
		if ip.ToString().StartsWith("127."):
			print "warning: using quirk"
			s = Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
			s.Connect( IPEndPoint(IPAddress.Parse("4.2.2.1"), 0 ) )
			l = s.LocalEndPoint as IPEndPoint
			ip = l.Address
		return ip
```

---

