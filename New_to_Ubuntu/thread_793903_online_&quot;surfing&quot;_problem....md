---
title: "online &quot;surfing&quot; problem..."
date: 2008-05-14
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-14
whenever i go somewhere online i always get a connection from 
s.ytimg.com and akamai
also i see these connections the moment i open my browser
as for the default page is the default ubuntu page
so how and why this is happening?

---

### Post by Joeb454 on 2008-05-14
Well you may want to check out [http://www.akamai.com/](http://www.akamai.com/) and as for s.ytimg.com ```
Registrant:
	Google Inc.
	(DOM-1723647)
	1600 Amphitheatre Parkway Mountain View
	CA
	94043 US

    Domain Name: ytimg.com

	Registrar Name: Markmonitor.com
	Registrar Whois: whois.markmonitor.com
	Registrar Homepage: http://www.markmonitor.com

    Administrative Contact:
	DNS Admin
	(NIC-14290822) 
	Google Inc.
	1600 Amphitheatre Parkway Mountain View
	CA
	94043 US
	dns-admin@google.com +1.6506234000 Fax- +1.6506188571
    Technical Contact, Zone Contact:
	DNS Admin
	(NIC-14290820) 
	Google Inc.
	1600 Amphitheatre Parkway Mountain View
	CA
	94043 US
	dns-admin@google.com +1.6506234000 Fax- +1.6506188571

    Created on..............: 2007-Dec-11.
    Expires on..............: 2008-Dec-11.
    Record last updated on..: 2008-May-09 21:14:30.

    Domain servers in listed order:

    DNS1.SJL.YOUTUBE.COM		
    DNS2.SJL.YOUTUBE.COM		
    DNS3.SJL.YOUTUBE.COM		
    ASH-NS1.ASH.YOUTUBE.COM		
    DAL-NS1.DAL.YOUTUBE.COM		
    MIA-NS1.MIA.YOUTUBE.COM		
    NYC-NS1.NYC.YOUTUBE.COM		

MarkMonitor.com - The Leader in Corporate Domain Management
----------------------------------------------------------
For Global Domain Consolidation, Research & Intelligence,
and Enterprise DNS, go to: www.markmonitor.com
----------------------------------------------------------
```

So that's some sort of Google/YouTube address.

Also does it happen when you use a different browser?

---

### Post by lunaluna on 2008-05-14
i have the same connections when i close firefox

---

### Post by Joeb454 on 2008-05-14
I'd imagine it's not really much to worry about (I don't tend to monitor the incoming connections, so I may get them too).

I meant do you still get them when using another browser?

---

### Post by chewearn on 2008-05-14
It could be a firefox plug-in.  Take a look at what you have installed.

---

### Post by lunaluna on 2008-05-14
i get them when i open the browser,while surfing and when i'm closing it

---

### Post by Joeb454 on 2008-05-14
Do you have any plugin's enabled?

---

### Post by billgoldberg on 2008-05-14
Block those addresses in your /etc/hosts file.

And the "problem" will go away.

I guess it's plugin related, because I don't have it.

---

### Post by lunaluna on 2008-05-14
well i've done my checks ...it was my fault ( configuring a plug in)

---

