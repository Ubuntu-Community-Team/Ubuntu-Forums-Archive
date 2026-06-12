---
title: "Need Help with Expect"
date: 2011-09-27
forum: Programming Talk
---

### Post by KamakazieX on 2011-09-27
I'm trying to convert a hostname to ip and resolve the ip's netmask and subnet information with bash/shell scripts and pass them to expect:

set mgtip [open |"[/usr/bin/host $fobject.some.domain.com |cut -f4 -d' ']"]
set mgtipm [open |"[/u/lmatthew/bin/netinfo $mgtip && printf "-addr=$IP -mask=$MASK -gw=$GW"]"]
send_user "Netboot using $mgtif with $IP on VLAN$VLAN ($OWNR)."

I get an error for "invoked within". How do I get around this so I can get automating!!

Thanks,

-Matt

---

### Post by KamakazieX on 2011-10-03
bump :popcorn:

---

