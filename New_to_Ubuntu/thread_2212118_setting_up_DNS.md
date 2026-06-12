---
title: "setting up DNS"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by dom172 on 2014-03-19
Hi i hope i dont get in trouble for posting homework but i cant see where i am going wrong , i have been following the Ubuntu 12.04 server guide so not looking for people to do do this for me but point out where im going wrong.

I am running 12.04 ubuntu server in vmware
addressing is

[www.engine.com]("http://www.engine.com")   192.168.1.10
mail      "       "     192.168.1.15
mail1     "      "      192.168.1.20
ns        "      "       192.168.1.25
ns1      "      "       192.168.1.30   

this is my zone file

[I]$TTL    604800
@       IN      SOA     engine.com. root.engine.com. (
                              5 ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       192.168.1.10
;
@       IN      NS         ns.engine.com.
@       IN      A          192.168.1.25
@       IN      NS         ns1.engine.com.
@       IN      A          192.168.1.30
@       IN      NS   5    mail.engine.com.
@       IN      A          192.168.1.15
@       IN      NS   10  mail1.engine.com.
@       IN      A          192.168.1.20  [/I]
  
and i get this error when i run the checkzone

[I]zone engine.com/IN:  NS 'ns.engine.com' has no address records (A or AAAA)
zone engine.com/IN:  NS 'ns1.engine.com' has no address records (A or AAAA)
zone engine.com/IN:  not loaded due to errors[/I]

My reverse zone file comes back ok


Any help would be greatly appreciated

thanks Dom

---

### Post by Mark Phelps on 2014-03-19
> Hi i hope i dont get in trouble for posting homework

Unfortunately, the Forum Rules prevent us from helping you:

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued

---

### Post by bapoumba on 2014-03-19
^
And thread closed.

---

