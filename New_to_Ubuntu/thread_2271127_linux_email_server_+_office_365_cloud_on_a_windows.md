---
title: "linux email server + office 365 cloud on a windows domain"
date: 2015-03-27
forum: New to Ubuntu
---

### Post by rmit2 on 2015-03-27
Can i have a domain with office 365 on the cloud ( no on-premises  exchange server) configured and at the same time have open source email  server - Postfix,  ( physical machine) on the domain as well. idea is to minimize  licensing cost. i want  important users to use office 365 on the cloud  and the rest to use an open source email server ( postfix or   any linux based server) whichever is applicable. I would want to protect my emails from  spam by using email security product as well ( . is this setup possible at all and has anyone tried  this .

---

### Post by TheFu on 2015-03-27
Never tried it, but you can tell postfix which addresses to send to whatever back-end email server you like. Basically, I think you need a tiny email gateway with all the users known that does AS/AV then forwards the good emails to either Exchange or the other postfix box.  Only the gateway needs an MX DNS record.

I use an email gateway to direct email for different domains at the domain level. Only a few key accounts have specific forwarding rules to ensure they cannot be used to take over our DNS records or get certs by outsiders who get control of an email address somehow.

---

### Post by SeijiSensei on 2015-03-28
Another option is to use subdomains, so that mail for @office.example.com has a different MX from @local.example.com.

Can Office365 be configured to use a back-end IMAP server?  Then you could have one Linux box with all the accounts, with the accounts for the Office365 users configured to collect their mail from the Linux box.

---

### Post by jacqueline-patricia on 2015-03-29
If I understand correct, you want to host to mail environments for the same SMTP domain. In your case Office 365 and Postfix on the premises. This should be possible. 
Check this: [https://technet.microsoft.com/en-us/library/jj945194%28v=exchg.150%29.aspx](https://technet.microsoft.com/en-us/library/jj945194%28v=exchg.150%29.aspx) and [http://exchangeserverpro.com/how-to-share-an-email-domain-between-two-mail-systems/](http://exchangeserverpro.com/how-to-share-an-email-domain-between-two-mail-systems/)

Is this what you mean?

Jacqueline

---

