---
title: "Making the sed | egrep | cut | tr line smaller"
date: 2008-12-21
forum: Programming Talk
---

### Post by PryGuy on 2008-12-21
Good day, everyone!
I'm about to make a program that would record interface traffic statistics. I get data from /proc/net/dev. The line that does it seems awkward to me, any suggestions how to make it smaller?
```
#!/bin/bash

iface=eth0

# That's what we get before we take the lines we want out of it
#cat /proc/net/dev | egrep "($iface)" | sed -e 's/|/:/' | sed -e 's/|/ /' | cut -d ":" -f 2 | tr -s " " " " | sed -e 's/^[ \t]*//' | sed 's/\([^ ]*[^ ]*[^ ]*\)/&\n/g' |  sed -e 's/^[ \t]*//'

function getinfo()
{
  bytes=`cat /proc/net/dev | egrep "($iface)" | sed -e 's/|/:/' | sed -e 's/|/ /' | cut -d ":" -f 2 | tr -s " " " " | sed -e 's/^[ \t]*//' | sed 's/\([^ ]*[^ ]*[^ ]*\)/&\n/g' |  sed -e 's/^[ \t]*//' | sed -n $1p`
}  

getinfo 1
sent=$bytes
getinfo 9
rcv=$bytes

echo "sent: "$sent" bytes"
echo "received: "$rcv" bytes"

sleep 10

exit 0
```Thank you in advance!

---

### Post by ghostdog74 on 2008-12-21
too many pipes. Makes your code slow, and ugly. Use awk.
```

awk 'BEGIN{ FS="[:]| +"}
/eth0:/{  
    print "bytes sent: ",$3
    print "bytes recv: ",$11
}' /proc/net/dev


```

---

### Post by PryGuy on 2008-12-21
Thaaank you! I would thank you twice if I could! But, there's one thing that worries me, that's a bug possibly, the /proc/net/dev file is generated a bit different from boot to boot (that's how I explain it), so the values can move one position, that's why I remove whitespaces twice.
Your code worked for me when I made these corrections but it's unpredictable what position the values will be on next boot:
```
awk 'BEGIN{ FS="[:]| +"}
/ath0:/{  
    print "bytes sent: ",[COLOR="Red"]**$4**[/COLOR]
    print "bytes recv: ",[COLOR="Red"]**$12**[/COLOR]
}' /proc/net/dev

```

---

### Post by ghostdog74 on 2008-12-21
you might want to try using netstat instead. read the man page of netstat. It can show you statistics as well, with options to format your output as needed.

---

