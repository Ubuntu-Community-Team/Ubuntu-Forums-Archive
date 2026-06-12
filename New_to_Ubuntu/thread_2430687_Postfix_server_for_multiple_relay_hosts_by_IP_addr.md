---
title: "Postfix server for multiple relay hosts by IP address and SASL authentication"
date: 2019-11-06
forum: New to Ubuntu
---

### Post by karthik-techie on 2019-11-06
[COLOR=#242729][FONT=Arial]I have done setup of postfix. Now I want to use 2 sasl accounts to send mails through 2 relay hosts. Those are[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]1) [EMAIL="user1@example.com"]user1@example.com[/EMAIL] - relayhost - sendgrid[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]2) [EMAIL="user2@example.com"]user2@example.com[/EMAIL] - relayhost - local smtp server[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now, I am integrating[/FONT][/COLOR]

[LIST=1]
[*]user1 account in website-1
[*]user2 account in website-2
[/LIST]
[COLOR=#242729][FONT=Arial]when the request came from website-1, mails should go from sendgrid and request came from website2 mails should go from local SMTP server(installed in server). I have done this setup with "transport" configuration(/etc/postfix/transport file). In transport configuration, we are giving domain names. Now, I want give IP address instead of domain names.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How we can route mapping by IP address?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It means, when request came from IP address 'X', mails should go from sendgrid and request came from IP address 'Y' mails should go from local SMTP server(installed in server). Please provide your suggestions to achieve this requirement. Thanks in advance.[/FONT][/COLOR]

---

### Post by Skaperen on 2019-11-06
mail servers work best with domain names.  you can send mail by IP but you need to configure it to recognize the IP address in the email address as one of its own domains.

---

### Post by karthik-techie on 2019-11-06
Thanks for your quick response. I agree with you, mail servers are work best with domain names. 
But as per my requirement, My Website-1 is a website builder. It means we are creating new websites to the customers. So, every customer has his own website with new domain names.
So, I can't set condition(in transport file) on domain names for relaying. If I set condition on IP address, My websites-1's all customer domain mails will go through sendgrid and website-2 mails will go through local SMTP server. Please, I need your suggestions.

---

### Post by SeijiSensei on 2019-11-06
You usually must put IP addresses inside square brackets to use them in an email address, e.g., user@[10.10.10.10].  I use sendmail, not Postfix, but my mailertable that determines where to relay mail also uses this convention.

```

example.com               relay:[10.10.10.10]

```

---

### Post by TheFu on 2019-11-06
Use the transport file for this.

example1.com       to_example1.com:[172.22.22.5]:25
example2.com       to_example2.com:[172.22.22.6]:25

I've never used it per login, but it definitely works for each domain.  IPs and posts are per domain configurable.
Email for example1 is sent to a relay on port 25/tcp at 172.22.22.5.
There is a manpage for the postfix transport file format. 
```
NAME
       transport - Postfix transport table format
```

The manpage says how to configure it with a per-user nexthop.
```
TABLE SEARCH ORDER
       With  lookups  from  indexed files such as DB or DBM, or from networked
       tables such as NIS, LDAP or SQL, patterns are tried  in  the  order  as
       listed below:

       user+extension@domain transport:nexthop
              Deliver mail for user+extension@domain through transport to nex&#8208;
              thop.

       user@domain transport:nexthop
              Deliver mail for user@domain through transport to nexthop.
...

```

Another answer is to use the /etc/aliases which can forward email to a local userid anywhere thru postfix as the MTA.  There's a manpage for the aliases file.

Don't know how helpful this is, sorry.

---

