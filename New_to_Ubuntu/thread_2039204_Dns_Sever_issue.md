---
title: "Dns Sever issue"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by ProCon on 2012-08-08
I wanted to make my own DNS server using ubuntu and I think I am a bit confused. I was on the ubuntu wiki and im a bit lost.
I was using this guide [HTML]https://help.ubuntu.com/8.04/serverguide/dns-configuration.html[/HTML]

Now the idea is to have a DNS sever for my DHCP sever.  The new ISP that I am getting will not have its own DNS and we rather just have our own anyway.  So I was following these these steps on how to built it and I am not quite sure on what I need exactly.

If I have my own DHCP and I want my own DNS do I need a caching nameserver BIND9, primary master server BIND9, or a secondary master configuration BIND9.

---

### Post by HermanAB on 2012-08-08
You need two: Primary and secondary BIND version 9.

---

### Post by ProCon on 2012-08-15
Alright I have a few questions.  First off I'm totally new at this and have no idea on what I am doing.
I went and purchased a domain from godaddy.com.  So I've got that now.  Now I just need to know how to set that up with this new domain sever I'm trying to build.

lets say that i purchased test1.com and that is my domain

I am at the following step and I am lost;

"dit the new zone file /etc/bind/db.example.com change localhost. to the FQDN of your server, leaving the additional "." at the end. Change 127.0.0.1 to the nameserver's IP Address and root.localhost to a valid email address, but with a "." instead of the usual "@" symbol, again leaving the "." at the end. Change the comment to indicate the domain that this file is for.

Create an A record for the base domain, example.com. Also, create an A record for ns.example.com, the name server in this example:"

```
;
; BIND data file for example.com
;
$TTL    604800
@       IN      SOA     example.com. root.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       192.168.1.10
;
@       IN      NS      ns.example.com.
@       IN      A       192.168.1.10
@       IN      AAAA    ::1
ns      IN      A       192.168.1.10
```

Where did this ns.example.com come from?  When they say make a record... is this somthing I need to do with godaddy?  What do they mean create a record file?  so mine would be ns.test1.com?  Totally lost here :(

---

### Post by SeijiSensei on 2012-08-15
Let GoDaddy host your DNS.  [Running a bind9 nameserver]("http://tools.ietf.org/html/rfc1912") is not something you should be doing if you describe yourself as "totally new at this and not sure on what I am doing."  Plus, if you read section 2.8 of that RFC I linked to, you need to be running two nameservers to conform to Internet protocols.

---

### Post by ProCon on 2012-08-15
Well that is why I was trying to follow the directions and why I came here for help.  I am new and want to learn :)

Thanks for the link.  
I got the impression on the 1st reply that I needed to be running 2 nameservers.  
That is what I am trying to do, just needed some input on my confusion.

But my question was never answered
Where did this ns.example.com come from? When they say make a record... is this somthing I need to do with godaddy? What do they mean create a record file? so mine would be ns.test1.com?

---

