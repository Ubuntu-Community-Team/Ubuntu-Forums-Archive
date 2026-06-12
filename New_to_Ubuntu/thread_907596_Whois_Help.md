---
title: "Whois Help"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Swenghk on 2008-09-01
In the terminal when I use whois. i get nothing but a blinking cursor. Not even a "$" symbol.

---

### Post by halitech on 2008-09-01
are you entering any more then just 'whois'?

---

### Post by Swenghk on 2008-09-01
Yes.
 
```
whois "google.com"@whois.networksolutions.com
```

---

### Post by perlluver on 2008-09-01
The normal way of whois is ```
whois www.name.com
```

Without the @ sign

---

### Post by Swenghk on 2008-09-01
Ok...Now it's saying there is no server for this...

---

### Post by halitech on 2008-09-01
worked fine for me
```
daryl@ubuntu:~$ whois www.google.com

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

   Server Name: WWW.GOOGLE.COM.VN
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.TW
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.TR
   Registrar: TUCOWS INC.
   Whois Server: whois.tucows.com
   Referral URL: http://domainhelp.opensrs.net

   Server Name: WWW.GOOGLE.COM.SA
   Registrar: OMNIS NETWORK, LLC
   Whois Server: whois.omnis.com
   Referral URL: http://domains.omnis.com

   Server Name: WWW.GOOGLE.COM.PE
   Registrar: ABACUS AMERICA, INC. DBA NAMES4EVER
   Whois Server: whois.names4ever.com
   Referral URL: http://www.names4ever.com

   Server Name: WWW.GOOGLE.COM.MX
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.CO
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.BR
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.AU
   Registrar: MELBOURNE IT, LTD. D/B/A INTERNET NAMES WORLDWIDE
   Whois Server: whois.melbourneit.com
   Referral URL: http://www.melbourneit.com

   Server Name: WWW.GOOGLE.COM.AR
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

>>> Last update of whois database: Mon, 01 Sep 2008 17:13:34 EDT <<<

NOTICE: The expiration date displayed in this record is the date the 
registrar's sponsorship of the domain name registration in the registry is 
currently set to expire. This date does not necessarily reflect the expiration 
date of the domain name registrant's agreement with the sponsoring 
registrar.  Users may consult the sponsoring registrar's Whois database to 
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois 
database through the use of electronic processes that are high-volume and 
automated except as reasonably necessary to register domain names or 
modify existing registrations; the Data in VeriSign Global Registry 
Services' ("VeriSign") Whois database is provided by VeriSign for 
information purposes only, and to assist persons in obtaining information 
about or related to a domain name registration record. VeriSign does not 
guarantee its accuracy. By submitting a Whois query, you agree to abide 
by the following terms of use: You agree that you may use this Data only 
for lawful purposes and that under no circumstances will you use this Data 
to: (1) allow, enable, or otherwise support the transmission of mass 
unsolicited, commercial advertising or solicitations via e-mail, telephone, 
or facsimile; or (2) enable high volume, automated, electronic processes 
that apply to VeriSign (or its computer systems). The compilation, 
repackaging, dissemination or other use of this Data is expressly 
prohibited without the prior written consent of VeriSign. You agree not to 
use electronic processes that are automated and high-volume to access or 
query the Whois database except as reasonably necessary to register 
domain names or modify existing registrations. VeriSign reserves the right 
to restrict your access to the Whois database in its sole discretion to ensure 
operational stability.  VeriSign may restrict or terminate your access to the 
Whois database for failure to abide by these terms of use. VeriSign 
reserves the right to modify these terms at any time. 

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.daryl@ubuntu:~$ 


```

---

### Post by Swenghk on 2008-09-01
> **perlluver said:**
> The normal way of whois is ```
whois www.name.com
```

Without the @ sign

Thank you! I was reading the book Haking Exposed, and the author said that, what I thought, was the correct syntax. Thanx for your help!

---

