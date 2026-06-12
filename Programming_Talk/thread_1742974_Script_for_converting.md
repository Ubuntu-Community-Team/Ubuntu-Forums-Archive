---
title: "Script for converting"
date: 2011-04-29
forum: Programming Talk
---

### Post by asai on 2011-04-29
Anyone who knows about a script for converting CSV files to other formats?

---

### Post by Arndt on 2011-04-29
> **asai said:**
> Anyone who knows about a script for converting CSV files to other formats?

I don't know what you need to do, but maybe this is useful: [http://docs.python.org/library/csv.html](http://docs.python.org/library/csv.html)

---

### Post by Desidero on 2011-04-29
Which formats are you looking to convert to?

Also, based on the way you worded your question, I can't tell if you want help making a script or if you just want the name of a program/script that can do it for you.

---

### Post by asai on 2011-04-30
Thanks for your replys. :)
I want to convert a cvs file containing addressbook entrys into a LDIF file to import into my openLDAP server. It can be a finished script or a script for another conversion that I can edit.

---

### Post by hakermania on 2011-04-30
Yes, thanks for the info, but can you provide us (at least me) a sample of both formats? I have not access of neither of them... :) Thank you!

---

### Post by Vaphell on 2011-05-01
csv stands for comma-separated values
[http://en.wikipedia.org/wiki/Comma-separated_values](http://en.wikipedia.org/wiki/Comma-separated_values)

ldif
[http://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format](http://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format)

---

### Post by hakermania on 2011-05-01
Ok, let's say we have the following CVS file:```
psmith01,CLASS2B,Peter Smith 1,YEAR2,1,N,ADVANCED,STAFF,1,Y,Y
smehta,CLASS3G,Smeeta Mehta,LOCAL,1,Y,STANDARD,PUPIL,2.1,N,Y
```
As I saw, at the start of each LDIF file there is **word:** like:
```
changetype:
```
and then a value. So, how is it possible to convert between these formats?

---

### Post by asai on 2011-05-02
Here is 2 lines from my CSV file:
```
Atle,Eide,Eide Atle,Parkett,907 69 429,post@parkett.no
Belinda,Ingebrigtsen,Ingebrigtsen Belinda,Kluge Advokat,922 49 713,belinda@kluge.no
```

If I understand the format for adding data to the LDAP server from a LDIF file (changetype is used when modifying data):
```
dn: cn=Eide Atle,dc=dyndns,dc=org
cn: Eide Atle
givenname: Atle
sn: Eide
l: Parkett
mail: post@parkett.no
mobile: 907 69 429
objectclass: inetOrgPerson

dn: cn=Ingebrigtsen Belinda,dc=dyndns,dc=org
cn: Ingebrigtsen Belinda
givenname: Belinda
sn: Fanuelsen
l: Kluge Advokat
mail: belinda@kluge.no
mobile: 922 49 713
objectclass: inetOrgPerson

```

---

### Post by Arndt on 2011-05-02
> **asai said:**
> Here is 2 lines from my CSV file:
```
Atle,Eide,Eide Atle,Parkett,907 69 429,post@parkett.no
Belinda,Ingebrigtsen,Ingebrigtsen Belinda,Kluge Advokat,922 49 713,belinda@kluge.no
```

If I understand the format for adding data to the LDAP server from a LDIF file (changetype is used when modifying data):
```
dn: cn=Eide Atle,dc=dyndns,dc=org
cn: Eide Atle
givenname: Atle
sn: Eide
l: Parkett
mail: post@parkett.no
mobile: 907 69 429
objectclass: inetOrgPerson

dn: cn=Ingebrigtsen Belinda,dc=dyndns,dc=org
cn: Ingebrigtsen Belinda
givenname: Belinda
sn: Fanuelsen
l: Kluge Advokat
mail: belinda@kluge.no
mobile: 922 49 713
objectclass: inetOrgPerson

```

If you google for "python ldif", you may come up with something.

---

