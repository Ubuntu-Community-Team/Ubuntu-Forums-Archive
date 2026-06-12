---
title: "modify dns zone file via bash/sed"
date: 2010-03-27
forum: Programming Talk
---

### Post by kintarooe on 2010-03-27
I am building a script to modify dns zone files and am having difficulties.  I am trying to find/replace certain lines with updated information.  Any help is welcome.

Here is a default zone.

```
$TTL 1200
@	IN	SOA	ns1.where.net.  webmaster.somewhere.com. (
			2008112501 ; serial
			1200 ; refresh
			7200 ; retry
			604800 ; expire
			1200 ; ttl
			)

@	IN	NS	ns1.where.net.
@	IN	NS	ns1.where2.net.

@	IN	MX	1	mail
mail	IN	MX	1	mail

test.com.		IN      A       2.2.2.2
www			IN	CNAME	test.com.

mail	IN	A	1.1.1.1
```

I am trying to use sed to replace the lines after the first mail occurance as each line could be different.

---

### Post by stlsaint on 2010-03-28
You might recieve more direct help in the programming section of the forums.

---

### Post by koenn on 2010-03-28
you might also receive more accurate help if you explain why you want to do this, and what exactly you would want to replace, and with what.

---

### Post by kintarooe on 2010-03-29
> **stlsaint said:**
> You might recieve more direct help in the programming section of the forums.

How do I move the thread to programming?

Also, the script basically does this:

dns.sh <args>

the script is fed some variables, and it then uses those to create/remove/modify zone files.  We will be using this in conjuntion with a web form that builds the command + arguments to eliminate user errors.  This should help with syntax issues and easy administration.

---

### Post by slakkie on 2010-03-30
DNS syntax issues can be checked with the checkzone binary/script.

---

### Post by Elfy on 2010-03-30
> **kintarooe said:**
> How do I move the thread to programming?

Use the report abuse button and ask us to move it.

---

