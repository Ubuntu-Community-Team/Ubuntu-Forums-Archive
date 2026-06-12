---
title: "Python Regex to match specific domains"
date: 2016-12-06
forum: Programming Talk
---

### Post by astingengo on 2016-12-06
Hi,
Could you please help me with a regex to match domains like this one:
```
yyj295r3a231.com
98xas123d23.com
yy2x112.com
ly23avro1233lop.org
a54pd151op.com
027168152.com
crm97mt49.com
ko3663a40w.com
p71ce1xm.com
```
... etc.

Regards,
Ciprian

---

### Post by Rocket2DMn on 2016-12-06
I don't see any discernible pattern in these (presumably spam) domains, except that none of them appear to have any dictionary words (say, larger than 2 or 3 characters) in them.  A simple regex won't detect that though.  Are you trying to build some kind of spam filter?

---

### Post by SeijiSensei on 2016-12-06
I tested three of them with whois, and none of them proved to be a valid domain.  The all-digits domain violates the DNS standard.  Rather than using a regex you'd be better off testing with the "host" command:
```
$ host -t soa ly23avro1233lop.org
Host ly23avro1233lop.org not found: 3(NXDOMAIN)

```
That asks for the "statement of authority" record for one of your phony domains.  Any query for the mandatory SOA record that returns "NXDOMAIN" indicates the domain is clearly bogus.

As our emeritus master says, there is no regex that can do what you want, though 
```
^[0-9]+\.[a-z]{3}$
```
would match 027168152.com.  That doesn't get you very far.

---

### Post by astingengo on 2016-12-07
Yes, I'm trying to filter spam domains.
Well, this one for example will pass the MX check: cr97mt49.com
And there are a lots like this one.

If there isn't any regex that can match this type of domains, then there is no solution for these :(.

Thank you for your time.

---

### Post by SeijiSensei on 2016-12-07
Frankly, I'd rely on the vast array of online databases that vet domains and URLs which are consulted using "RBL" requests.  [SpamAssassin]("http://spamassassin.apache.org/") uses a bunch of these.  

I've relied on [MailScanner]("http://www.mailscanner.info/") for many years now.  It integrates virus and spam scanning and is very configurable.  Writing something from scratch to tackle spam doesn't make much sense to me when we have organizations like the Apache Foundation supporting software like SpamAssassin.

---

### Post by vasa1 on 2016-12-07
I tested ```
grep -Ein "^[[:alnum:]]+\.(com|org)" dom.txt
``` and it picks up all of the "domains" provided by OP.

dom.txt being
yyj295r3a231.com
98xas123d23.com
yy2x112.com
ly23avro1233lop.org
a54pd151op.com
027168152.com
crm97mt49.com
ko3663a40w.com

I don't know about "Python Regex" though.

---

### Post by SeijiSensei on 2016-12-07
Won't that regex also match "ubuntuforums.org" though?  I think he wanted a regex that could discriminate between legitimate domain names using words and bogus ones using random collections of letters and numbers.  I don't think that's possible myself.

---

### Post by vasa1 on 2016-12-07
> **SeijiSensei said:**
> Won't that regex also match "ubuntuforums.org" though?  ...
Oops!

---

### Post by astingengo on 2016-12-08
@SeijiSensei thank you for your info.
I'll have a look.

Regards,
Ciprian

---

