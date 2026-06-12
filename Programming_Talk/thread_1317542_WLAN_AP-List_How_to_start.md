---
title: "WLAN AP-List How to start?"
date: 2009-11-06
forum: Programming Talk
---

### Post by tsg on 2009-11-06
Hello, I want to make a gtkmm based GUI, that lists available WLANs and some details like signal quality, encryption, etc. 

I know how to make a GUI with gtkmm, but I have no idea, where to get the wifi information from.

[B]Is there any c/c++ wifi library for that purpose?
Is there anything I can reuse?[/B]

I thought about searching the code of the network manager, but that will not be easy...
Can someone give me a hint to the right library, kernel/system call, or wuteva I might go for. Or at least some keywords for google I haven't thought of yet..

Thank you very Much!

---

### Post by jon zendatta on 2009-11-07
perhaps you could read this
[http://www.ebookee.com/TCP-IP-Illustrated-Volume-1-The-Protocols_81027.html]("http://www.ebookee.com/TCP-IP-Illustrated-Volume-1-The-Protocols_81027.html")
view the source code for wireshark

---

### Post by ssam on 2009-11-07
you could look at cnetworkmanager does it
[http://vidner.net/martin/software/cnetworkmanager/](http://vidner.net/martin/software/cnetworkmanager/)

---

### Post by tsg on 2009-11-09
@jon zendetta:

Thank you for you reply, but I'm a little confused: What has tcp/ip to do with wlan? and how can wireshark (ethernet analylis) help me with that?

@ssam:

Thank you as well I'll have a look at the cnetworkmanager source code, although I still think this might be not easy.

Does someone know of a general purpose wlan library?
Thank you very much so far

---

### Post by tsg on 2009-11-09
I had a first look at the cnetworkmanager sourcecode by now. Unfortunately it's python. I was hoping for a c/c++ solution *g*. So I also looked into the networkmanager/networkmanager-gnome source, where I found a reference to iwlib.h. Might that be what I'm looking for? I'll have a closer look at that lib in the meantime.

---

### Post by tturrisi on 2009-11-11
This may help:
> #!/bin/bash
# Find device used for wifi.
devlist=$(cat /proc/net/wireless | tail --lines=1) 2>/dev/null
devleft=${devlist#' '*}
devright=${devlist%%':'*}
echo $devright | grep "" > /tmp/dev_pure
device=$(cat /tmp/dev_pure)

# Get Quality
iwconfig $device | grep Link > /tmp/link
quality=$(cat /tmp/link | grep "Link")
echo $quality

# Get LAN IP
ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'

Check the Conky source code too.  It has built in support for wifi  variables.

---

### Post by tsg on 2009-11-11
I found that the iwlib.h can do the job for me. I havn't found a good tutorial yet, but I think it won't be too difficoult.

Another idea is to write my own lightwight kismet client, and get the information from kismet. I have absolutely no idea how this is done, but the idea sounds interesting.

Has anyone ever tried that? 

Thank you all for your hints!

---

### Post by cszikszoy on 2009-11-11
What about querying NetworkManager's DBUS interface to get that info?  I've written something before in C# that gets all info from DBUS.

---

### Post by tsg on 2009-11-30
Hi thank you for your replys. 

I don't know about that DBUS thing, but I found out that the iwlib would do exactly what I need. It's the lib that iwconfig is build on.
But just for the fun of it (and because I like the monitor mode*g*) I started to write a kismet client, which seems to work well. There is almost no documentation of the kismet protocoll, but it is quite simple and the kismet source code helps. I'm working on a VERY simple kismet client lib, when its finished, I'll publish it.

---

