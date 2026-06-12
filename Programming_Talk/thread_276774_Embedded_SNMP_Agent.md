---
title: "Embedded SNMP Agent"
date: 2006-10-13
forum: Programming Talk
---

### Post by GaryH on 2006-10-13
Does anybody out there have experience embedding an SNMP agent in a Ubuntu or Linux environment? Support of proprietary MIBS containing both scalars and tables is a requirement. Another requriement is that the agent be documented (comments within the source area of OID tables and instrumentation routine pointers etc. is acceptable) so proprietary OIDs and associated instrumentation can be added quickly w/o too much reverse engineering. Any tips as to what agent to use and any other advice would be appreciated.
Thanks in advance.
GaryH

---

### Post by steve.horsley on 2006-10-13
There is a package **snmpd** in the repositories. I believe that can do what you want. It includes tools that can retrieve data for SNMP requests, including launching scripts to get the required info (kinda like CGI). That's what I've heard - haven't ever done more than install the default package and enable public access myself. I think the package includes documentation.

---

### Post by GaryH on 2006-10-14
Thank you Steve:)

---

