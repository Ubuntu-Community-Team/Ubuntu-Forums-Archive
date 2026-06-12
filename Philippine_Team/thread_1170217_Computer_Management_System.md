---
title: "Computer Management System"
date: 2009-05-26
forum: Philippine Team
---

### Post by pinoyskull on 2009-05-26
Hi,

  	Is there a suitable desktop management system that can 



1) Remotely manage software inventory, installations and removal.
2) Keeps inventory of system name, hardware info and software.

3) Has a place for current assignee and possibly department.


a GUI solution is preferred.

---

### Post by loell on 2009-05-26
if it's for enterprise, in ubuntu that would be [landscape]("http://www.canonical.com/projects/landscape")

but if it's only for SOHO then maybe Mandriva Directory Server will do.

---

### Post by pinoyskull on 2009-05-26
> **loell said:**
> if it's for enterprise, in ubuntu that would be [landscape]("http://www.canonical.com/projects/landscape")

but if it's only for SOHO then maybe Mandriva Directory Server will do.
@loell

Yeah, something like MDS but I need something that can remotely manage softwares too (install / uninstall)

---

### Post by jsgotangco on 2009-05-26
How about something that provides FCAPS? There's a bunch of stuff out there and could be complex though. Zenoss comes to mind, but there are also stuff like opennms, pandora fms, etc.

---

### Post by pinoyskull on 2009-05-28
any more suggestions?

---

### Post by loell on 2009-05-28
webmin? ;)

---

### Post by pinoyskull on 2009-05-28
btw laptops ang ima manage ng software. So I need something that can keep track of the laptop's softwares and changes.

---

### Post by jsgotangco on 2009-05-28
You need something that does FCAPS. If the FCAPS concept is too complex, perhaps OCS Inventory NG can be useful to you.

In the Microsoft world, I used to do this with Systems Management Server.

Usually these kind of software require a client to be installed into every machine.

---

### Post by pinoyskull on 2009-05-29
Thanks Jerome

---

### Post by jdarias on 2009-05-29
AFAIK Landscape is not free, it is a commercial application and service offered by canonical. Is this correct?

---

### Post by loell on 2009-05-29
> **jdarias said:**
> AFAIK Landscape is not free, it is a commercial application and service offered by canonical. Is this correct?

yes, that is correct.

---

### Post by jsgotangco on 2009-05-30
If you are to manage 100+ machines in an enterprise environment, the cost of Landscape is peanuts.

---

### Post by pinoyskull on 2009-05-30
> **jsgotangco said:**
> You need something that does FCAPS. If the FCAPS concept is too complex, perhaps OCS Inventory NG can be useful to you.

In the Microsoft world, I used to do this with Systems Management Server.

Usually these kind of software require a client to be installed into every machine.
We are testing OCS Inventory NG now, a bit not user friendly at first but I think this is the one that we are looking for :)

---

### Post by steve_c on 2009-06-24
Inquiring minds want to know what you think of your testing of OCS-inventory NG.

Another alternative I'm considering myself is open-audIT:
[http://www.open-audit.org/index.php]("http://www.open-audit.org/index.php")

Anyone have any experience with both of these products and care to give feedback?

---

### Post by kiminaiseah on 2009-07-01
use OpenNMS, it can barely look any application installed on client side, supported windows,linux,mac,sun

---

