---
title: "Shell scripting help"
date: 2011-10-03
forum: Programming Talk
---

### Post by KamakazieX on 2011-10-03
I've written a bash shell script that queries a database based on IP and returns VLAN/VLID/Netmask/Gateway. I'd like to add functionality to this so I can type in a hostname and have it resolve to IP and execute, if an IP is supplied skip hostname resolution. Can someone help with this? This is the string I had in mind to dump to a variable, but I'd like to retain IP resolution as well:

```
host $1.fqdn.domain.com |cut -f4 -d' '
```

Thanks for the help!

---

### Post by ofnuts on 2011-10-03
> **KamakazieX said:**
> I've written a bash shell script that queries a database based on IP and returns VLAN/VLID/Netmask/Gateway. I'd like to add functionality to this so I can type in a hostname and have it resolve to IP and execute, if an IP is supplied skip hostname resolution. Can someone help with this? This is the string I had in mind to dump to a variable, but I'd like to retain IP resolution as well:

```
host $1.fqdn.domain.com |cut -f4 -d' '
```Thanks for the help!
```

if [[ $1 =~ [0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3} ]]
then
    echo "IP address"
else
    echo "Name"
fi

```

Regexp above isn't perfect, it will accept 999.999.999.999, for instance.

---

### Post by KamakazieX on 2011-10-12
Thanks for what I need to accomplish this works great!

---

