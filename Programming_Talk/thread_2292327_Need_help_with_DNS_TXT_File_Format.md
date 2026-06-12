---
title: "Need help with DNS TXT File Format"
date: 2015-08-27
forum: Programming Talk
---

### Post by patrick19 on 2015-08-27
Hey everyone. 

I am trying to enter some TXT records for mailgun on my DNS TXT records. I've been looking up all the ways you can enter this information, but I can't seem to find a solution for my case. 

Typically, you will have a record such as:

```

[FONT=Verdana][SIZE=1][SIZE=2]                 mydomain.com. TXT "v=spf1 -all"
[/SIZE][/SIZE][/FONT]
```[FONT=Verdana][SIZE=1][SIZE=2]

They can vary but this is pretty common. Most DNS providers have an easy form for you to add the the information with 3 fields: Host name; select record type (TXT); and TXT record value.

However my DNS host (domain.com) only has a text area, and there's virtually no documentation on formatting the record. So far, all of my attempts have failed to validate.

Any suggestions?

Thanks
[/SIZE][/SIZE][/FONT]

---

### Post by Habitual on 2015-08-27
Who is your "DNS host" exactly?

---

### Post by SeijiSensei on 2015-08-27
An SPF record is usually tied to a domain rather than a specific hostname. Have you tried simply entering the string appearing after the TXT in your example above?

Also I've always used the tilde in "~all", not the hyphen.

---

### Post by CharlesA on 2015-08-27
> **SeijiSensei said:**
> An SPF record is usually tied to a domain rather than a specific hostname. Have you tried simply entering the string appearing after the TXT in your example above?

Also I've always used the tilde in "~all", not the hyphen.

They should have a SPF type as well as a TXT type at domain.com, but if I remember right the SPF type is depreciated and should be replaced with a TXT entry. I use both, however.

Off topic, but don't even get me started about trying to get a DKIM key set up in their control panel. That was what made my switch to Cloudflare for DNS.

---

### Post by patrick19 on 2015-09-02
Thanks for the replies.

I actually got fed up with their control panel, so I switched nameservers to Route 53. Everything is working well now.

---

