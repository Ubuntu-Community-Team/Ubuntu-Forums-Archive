---
title: "network address"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by squrl on 2013-06-12
Can someone give me an easy way to obtain the url of a network printer?

Thanks

---

### Post by dan08 on 2013-06-12
Usually you can print out a Test/Configuration page and it will tell you the IP Address.
 
If your on a small home network you can use arp-scan ([http://linux.die.net/man/1/arp-scan](http://linux.die.net/man/1/arp-scan)) to see the stuff on your network and maybe deduce which one is your printer
```
 
sudo apt-get install arp-scan
sudo arp-scan --interface=eth0 xxx.xxx.xxx.0/24 
```

To give any further help you would have to supply some info about the printer.

---

### Post by howefield on 2013-06-12
Try running this command in a terminal...

```
CUPS_DEBUG_LEVEL=2 /usr/lib/cups/backend/snmp 2>&1 | tee snmp.log
```

This will put a log file in your /home folder as well as print to the terminal and you should find the ip address toward the end of the output.

---

### Post by ajgreeny on 2013-06-12
You may also be able to find it from your router's configuration page, so in your web-browser go to whatever your router IP is (often 192.168.0.1 or 192.168.1.1, but usually noted on router label) and see if there is a "Connected devices" section.

---

