---
title: "Postfix send from example.com but from server of mail.example.com"
date: 2019-11-09
forum: New to Ubuntu
---

### Post by posfixintellect on 2019-11-09
I have setup a postfix server that works pretty much flawlessly with spf records and such for mail.mydomain.com and I can send mails from it without being flagged as spam but only if I send with [EMAIL="example@mail.mydomain.com"]example@mail.mydomain.com[/EMAIL] but if I send it with [EMAIL="example@mydomain.com"]example@mydomain.com[/EMAIL] without the subdomain, it's flagged as spam or untrusted. Obviously because I set up the whole process for the subdomain and the A record is only pointed from mail.mydomain.com.

Now the question is really, I don't want the A record from mydomain.com to be changed as it is hosting something else, but I still would like to send mails using mydomain.com instead of the subdomain prefix also. Is it possible to somehow do it without being flagged as spam? And without pointing A record to the postfix server?

---

### Post by SeijiSensei on 2019-11-09
Is there an SPF record for mydomain.com?

Without more details it's hard to know what else to suggest. Can you give us an example of a message that is marked as spam?  If you reveal the full headers for the message on the receiving end, does it include a header that indicates why it was identified as spam?  

You might also add an A record for mydomain.com like this:

```

@    IN    SOA mydomain.com root.mydomain.com. (
         stuff
         )
  
       IN     NS  ns.mydomain.com,
       IN     NS  ns2.mydomain,com.

       IN     MX   0 mail.mydomain.com.

       IN     TXT  "v=spf1 a:mail.mydomain.com ~all"

       IN     A    10.10.10.10

mail   IN     A  10.10.10.10
       IN     TXT "v=spf1 a:mail.mydomain.com ~all"

etc.

```

Adding DKIM signing is also a good idea. You can install the opendkim package from the repositories and add the appropriate support in Postfix.

---

### Post by posfixintellect on 2019-11-09
Thanks for the reply. I didn't know you could set the spf for the host if it wasn't the same domain, it's working great now!

---

