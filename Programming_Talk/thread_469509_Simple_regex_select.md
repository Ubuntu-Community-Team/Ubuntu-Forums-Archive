---
title: "Simple regex select"
date: 2007-06-10
forum: Programming Talk
---

### Post by watricky on 2007-06-10
Hey guys. I'm trying to select specific words out of a line in bash using regexes to get rid of the wasted whitespace in my dns digs. I'm relatively new to this so please go easy on me. :)

#!/bin/bash
dig soa $1 | grep ^$1.*SOA

This gives me, for ubuntuforums.org:
ubuntuforums.org.       86400   IN      SOA     ns0.dnsmadeeasy.com. dns.dnsmadeeasy.com. 2003010205 43200 3600 1209600 180

Now I want to dig again, this time using ns0.dnsmadeeasy.com:

dig any $1 @ns0.dnsmadeeasy.com | grep -v ^; | grep .

which will give me all the records for the hostname according to the authoritative dns server (ie, not cached) and without lots of empty or meaningless lines.

In regex parlance, I could use ^$1.*SOA *\(\(\[a-z\-]?\\\.\)?\) .* and select the () group to get the nameserver, though I don't know how to do that using grep or sed. In fact I don't think my escapes in this particular case are 100% either but I can't get a simpler selection working properly yet anyway. :/

I'm sure this is *supposed* to be simple. :)

---

### Post by ghostdog74 on 2007-06-10
i assume your nameservers are at field 5
```

dig any ns0.dnsmadeeasy.com | awk '/[.]/ && !/[;]/{print $5}'

```
output:
```

# dig any ns0.dnsmadeeasy.com | awk '/[.]/ && !/[;]/{print $5}'
63.219.151.3
ns1.dnsmadeeasy.com.
ns2.dnsmadeeasy.com.
ns3.dnsmadeeasy.com.
ns4.dnsmadeeasy.com.
ns0.dnsmadeeasy.com.

```

---

### Post by watricky on 2007-06-10
> **ghostdog74 said:**
> i assume your nameservers are at field 5
```

dig any ns0.dnsmadeeasy.com | awk '/[.]/ && !/[;]/{print $5}'

```

Awesome! Now you can see what I was trying to achieve. :)

```

#!/bin/bash
if [ $# = 1 ]; then
dig soa $1 | grep SOA | grep -v "^;" | awk '/[.]/ && !/[;]/{print $5}' | xargs -i dig $1 any "@{}" | grep . | grep -v "^;"
else echo "Usage: diga example.com"
fi

```

output:
```

brendan@watricky:~$ diga ubuntuforums.org
ubuntuforums.org.       86400   IN      NS      ns3.xlogicdns.com.
ubuntuforums.org.       86400   IN      NS      ns4.xlogicdns.com.
ubuntuforums.org.       86400   IN      NS      ns2.xlogicdns.com.
ubuntuforums.org.       86400   IN      NS      ns1.xlogicdns.com.
ubuntuforums.org.       86400   IN      NS      ns5.xlogicdns.com.
ubuntuforums.org.       86400   IN      SOA     ns0.dnsmadeeasy.com. dns.dnsmadeeasy.com. 2003010205 43200 3600 1209600 180
ubuntuforums.org.       1800    IN      A       82.211.81.186
ubuntuforums.org.       1800    IN      MX      10 mail.ubuntuforums.org.
mail.ubuntuforums.org.  1800    IN      A       66.246.118.208
brendan@watricky:~$

```

Thank you very much.

---

