---
title: "[python] Time offset via NTP server"
date: 2011-10-13
forum: Programming Talk
---

### Post by pokerbirch on 2011-10-13
I have a project which connects to a server via an official API, however they provide no means of time synchronisation and rely on the user having an NTP sync'd pc clock. I don't want to force the the users of my script to keep their systems updated via NTP, so instead I want to calculate the offset within my script. All time objects of the API default to UTC/GMT.

Here's my code so far:
```
import struct
from time import time
from socket import socket, AF_INET, SOCK_DGRAM
from datetime import datetime

def send_ntp_request(self):
    """gets NTP time and returns a datetime object"""
    try:
        sock = socket(AF_INET, SOCK_DGRAM)
        sock.settimeout(5)
        data = '\x1b' + 47 * '\0'
        start_time = time()
        sock.sendto(data, ('uk.pool.ntp.org', 123))
        data, ip = sock.recvfrom(1024)
        req_time = time() - start_time
        if data:
            timestamp = struct.unpack('!12I', data)[10]
            timestamp -= 2208988800L # = date in sec since epoch
            timestamp += req_time / 2
            return datetime.utcfromtimestamp(timestamp)
    except:
        return 'ERROR: socket request failed'
```

Does this appear to be correct? It seems OK but I'm a little unsure of my handling of the actual request time. Is *timestamp += req_time / 2* sufficient? I don't need micro second accuracy but would like to be within 0.5 seconds.

---

### Post by karlson on 2011-10-13
> **pokerbirch said:**
> I don't want to force the the users of my script to keep their systems updated via NTP


Any reason why not?

> , so instead I want to calculate the offset within my script. All time objects of the API default to UTC/GMT.

Here's my code so far:
```
import struct
from time import time
from socket import socket, AF_INET, SOCK_DGRAM
from datetime import datetime

def send_ntp_request(self):
    """gets NTP time and returns a datetime object"""
    try:
        sock = socket(AF_INET, SOCK_DGRAM)
        sock.settimeout(5)
        data = '\x1b' + 47 * '\0'
        start_time = time()
        sock.sendto(data, ('uk.pool.ntp.org', 123))
        data, ip = sock.recvfrom(1024)
        req_time = time() - start_time
        if data:
            timestamp = struct.unpack('!12I', data)[10]
            timestamp -= 2208988800L # = date in sec since epoch
            timestamp += req_time / 2
            return datetime.utcfromtimestamp(timestamp)
    except:
        return 'ERROR: socket request failed'
```

Does this appear to be correct? It seems OK but I'm a little unsure of my handling of the actual request time. Is *timestamp += req_time / 2* sufficient? I don't need micro second accuracy but would like to be within 0.5 seconds.

Logic seems OK, but I still say make them configure NTP.

---

### Post by pokerbirch on 2011-10-13
> **karlson said:**
> Any reason why not?
The end users are not very computer literate so I need to keep things as simple as possible. So far my app has been written in pure python and has no dependencies. I'd like to keep it that way.

---

### Post by karlson on 2011-10-13
> **pokerbirch said:**
> The end users are not very computer literate so I need to keep things as simple as possible. So far my app has been written in pure python and has no dependencies. I'd like to keep it that way.

In my experience the users that are not that are not very computer literate don't run Linux/UNIX systems on their workstations actually running primarily Windows and most of those don't install Python on their systems.  Of those that actually do run Linux/UNIX on their workstations most are capable enough to put in place a simple ntp.conf file to get time synchronization going.

Of the ones that are running MACs they also are capable of following simple instructions on how to configure NTP as MAC seems to have a simple admin tools for just about everything it does.

So I don't see a reason to provide a supplemental mechanism for time checking but your logic seems to be OK for that purpose.

---

### Post by pokerbirch on 2011-10-14
> **karlson said:**
> In my experience the users that are not very computer literate...[snip]...are running primarily Windows and most of those don't install Python on their systems.Spot on. I've had to provide my app as a standalone using py2exe. I usually have to explain "double-click setup.exe with your left mouse button" as well. This is what happens when people who know nothing about computers buy a computer...

---

