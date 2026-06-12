---
title: "Tor + Polipo+Vidalia issues xubuntu 12.04"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by zerobinary on 2012-09-09
The error I am getting 
```
Sep 09 09:45:52.953 [Notice] Tor v0.2.3.21-rc (git-defad94902bc2b5e) running on Linux.
Sep 09 09:45:52.953 [Notice] Tor can't help you if you use it wrong! Learn how to be safe at https://www.torproject.org/download/download#warning
Sep 09 09:45:52.953 [Notice] Read configuration file "/home/mr-fool/.vidalia/torrc".
Sep 09 09:45:52.961 [Notice] Initialized libevent version 2.0.16-stable using method epoll (with changelist). Good.
Sep 09 09:45:52.961 [Notice] Opening Socks listener on 127.0.0.1:0
Sep 09 09:45:52.962 [Notice] Socks listener listening on port 50681.
Sep 09 09:45:52.962 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 09 09:45:52.962 [Warning] Error creating directory ./Data/Tor: No such file or directory
Sep 09 09:45:52.962 [Warning] Failed to parse/validate config: Couldn't access/create private data directory "./Data/Tor"
Sep 09 09:45:52.962 [Error] Reading config failed--see warnings above.
```
My /home/mr-fool/.vidalia/torrc (I edited using a tutorial) output
```
# If non-zero, try to write to disk less frequently than we would otherwise.
AvoidDiskWrites 1
# Store working data, state, keys, and caches here.
DataDirectory ./Data/Tor
GeoIPFile ./Data/Tor/geoip
# Where to send logging messages.  Format is minSeverity[-maxSeverity]
# (stderr|stdout|syslog|file FILENAME).
Log notice stdout
# Bind to this address to listen to connections from SOCKS-speaking
# applications.
SocksPort auto
SocksListenAddress 127.0.0.1
ControlPort auto

```

I tried this tutorial as well
[http://ubuntuforums.org/showpost.php?p=9226418&postcount=3](http://ubuntuforums.org/showpost.php?p=9226418&postcount=3)
sudo sysv-rc-conf
```


tor          [ ]        []         []         []        []        [ ]        [ ]

```
All the X have been unchecked

---

