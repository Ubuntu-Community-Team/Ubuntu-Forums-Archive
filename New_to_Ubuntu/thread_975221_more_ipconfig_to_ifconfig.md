---
title: "more ipconfig to ifconfig"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by ant2ne on 2008-11-08
Ok, today I want to look at what my computer is using for a DNS IP. In a windows machine I would type ipconfig /all and there would be displayed the IP address of the DNS server.  What is the CLI to get that result in ubunut?

---

### Post by drakeman007 on 2008-11-08
> **ant2ne said:**
> Ok, today I want to look at what my computer is using for a DNS IP. In a windows machine I would type ipconfig /all and there would be displayed the IP address of the DNS server.  What is the CLI to get that result in ubunut?

Linux handles the ipconfig in the file
```
/etc/network/interfaces
```

and the dns in 
```
/etc/resolv.conf
```

you use CAT to see both files settings, or you can use a script, explained [here]("http://ubuntuforums.org/showthread.php?t=76078")

Hope this helps!

---

### Post by bodhi.zazen on 2008-11-08
sudo ifconfig

sudo iwconfig for wireless

---

