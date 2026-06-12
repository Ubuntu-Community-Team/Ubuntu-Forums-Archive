---
title: "Writing a startup daemon"
date: 2010-04-02
forum: Programming Talk
---

### Post by aquavitae on 2010-04-02
Hi 

I'm trying to write a simple script to reconnect to the internet when the connection is dropped (which seems to happen quite often). This is what I've got so far:
```

#!/bin/sh

while [ true ]
do
    until ping -c 1 www.google.com
    do
        cd /sys/bus/pci/drivers/uhci_hcd

        for f in `ls -d  0000*`
        do
            echo -n $f > unbind
            echo -n $f > bind
        done

        sleep 1
        pon neotel
        cd
        sleep 10
    done
    sleep 60
done

```

The first thing is that I'm not familiar with bash scripting, so any suggestions on the actual syntax and structure would be greatly appreciated.

Secondly, my next step is to get it to automatically start at boot up. It would seem to me that the bast way of doing this is by adding it to /etc/init.d but this is where I get a bit lost. I've read that a script referenced in /etc/init.d/ should daemonize itself, and shouldn't have a "while true" loop in it. So how do I do this? I'm also a bit unclear of the distinction between upstart and start-stop-daemon - which should I be using? I think that I will manage to write the init.d script ok, but I want to be sure that I should be doing it that way first.

---

