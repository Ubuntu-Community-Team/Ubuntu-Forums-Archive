---
title: "vnstat"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by bu2971x on 2008-09-28
i got this from Syn,    where is it,it doesnt show up anywhere, and how do you use it?

---

### Post by engtg on 2008-09-28
go to terminal and type vnstat

yourname@your-desktop:~$ vnstat --help
 vnStat 1.6 by Teemu Toivola <tst at iki dot fi>

         -q,  --query          query database
         -h,  --hours          show hours
         -d,  --days           show days
         -m,  --months         show months
         -w,  --weeks          show weeks
         -t,  --top10          show top10
         -s,  --short          use short output
         -u,  --update         update database
         -i,  --iface          select interface (default: eth0)
         -?,  --help           short help
         -v,  --version        show version
         -tr, --traffic        calculate traffic
         -l,  --live           show transfer rate in real time

See also "--longhelp" for complete options list and "man vnstat".

A new database can be created with the following command:    [COLOR="Red"]vnstat -u -i eth0[/COLOR]
A list of available interfaces can be seen with the 'ifconfig' command.  Check you ifconfig to make sure it is eth0 mine is eth1.

---

### Post by LittleJakub on 2011-02-14
I get this when try to use vnstat:

```
Error: Database load failed even when using backup. Aborting.
```

Any suggestions?

---

