---
title: "anyone knows what this command does?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Sec Expert on 2008-05-27
hi
is there anyone who knows what this command does?:

echo "nameserver 4.2.2.4" | sudo tee /etc/resolv.conf 


is resolv.conf a file in my OS how can I reach that?

thanx in advance:popcorn:

---

### Post by Joeb454 on 2008-05-27
It looks like it will add "nameserver 4.2.2.4" to the file at /etc/resolv.conf

You can view the file by using ```
cat /etc/resolv.conf
```

---

### Post by Sukarn on 2008-05-27
it puts "nameserver 4.2.2.4" into the file "/etc/resolv.conf"

/etc/resolv.conf contains list of DNS servers, which are the servers that are contacted when you try to visit a website, to translate the website address into DNS address. For example, when you type [www.ubuntu.com](www.ubuntu.com), a DNS server will be contacted and asked what IP address [www.ubuntu.com](www.ubuntu.com) translates to. The DNS server replies with an IP address, and then your computer visits that IP address.

What the above command is doing is adding 4.2.2.4 as a DNS server.

DNS servers are specified in /etc/resolv.conf by saying "nameserver [IP address of DNS server]" on a new line.

---

### Post by sdennie on 2008-05-27
It should also print "nameserver 4.2.2.4" to your screen!  ;)

---

### Post by Sukarn on 2008-05-27
> **vor said:**
> It should also print "nameserver 4.2.2.4" to your screen!  ;)

Yes, its supposed to do that.

By the way, I forgot to mention earlier that the command will wipe the entire contents of /etc/resolv.conf and replace them with "nameserver 4.2.2.4" because it uses tee. It could have used cat instead to catenate the nameserver line to the end of the file, but because it uses tee, it will just replace /etc/resolv.conf

---

### Post by sdennie on 2008-05-27
Depending on who suggested the command, that may be the goal of it (the /etc/resolv.conf clobber).  The stdout output of the tee might just be for user confirmation.

---

