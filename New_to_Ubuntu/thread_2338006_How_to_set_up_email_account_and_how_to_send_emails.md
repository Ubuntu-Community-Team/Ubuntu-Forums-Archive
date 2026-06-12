---
title: "How to set up email account and how to send emails to users on Ubuntu16.04LTS ?"
date: 2016-09-23
forum: New to Ubuntu
---

### Post by dkm171 on 2016-09-23
Dear administrators & forum supporters,

How to set up email account and how to send emails to our users on Ubuntu 16.04LTS ?

I have a domain and email accounts in cpanel (i have a hosting account) for my business 
but i don't know, how to set up email account(s) on my pc Ubuntu 16.04 and how to send emails to our users (more than 5000 users) at the same time  from my pc!

please tell me, i want to know clear solution about this !

Best Regards !
Krishna

---

### Post by QIII on 2016-09-23
Hello!

Please use the default font and color except in cases where it is necessary to draw special attention to some small point in your thread.

Thanks.

---

### Post by SeijiSensei on 2016-09-26
If you were running your own server, I'd tell you to add an entry to /etc/aliases like this:
```
clients:         :include:/home/me/client-mailing-list
```
Then mail sent to the "clients" address would be redistributed to the list of addresses in that file.

However I have no idea how you would do that with cpanel.  You probably need to ask your provider for help.

You could also install a mail client like Mozilla Thunderbird and add the list to your address book.  I don't how well it would do with >5000 entries though.

---

### Post by dkm171 on 2016-09-30
> **SeijiSensei said:**
> If you were running your own server, I'd tell you to add an entry to /etc/aliases like this:
```
clients:         :include:/home/me/client-mailing-list
```
Then mail sent to the "clients" address would be redistributed to the list of addresses in that file.

However I have no idea how you would do that with cpanel.  You probably need to ask your provider for help.

You could also install a mail client like Mozilla Thunderbird and add the list to your address book.  I don't how well it would do with >5000 entries though.


Dear SeijiSensei, in this case i am using "thunderbird" app in my pc (ubuntu 16.04) for email sending 
but, i saw a article on internet "thunderbird" is not a secure app, is it right ?

---

### Post by mastablasta on 2016-09-30
none of the questions has anyhting to do with Ubuntu. 

you have the quesiton regarding thunderbird (which by the way is a secure app btu you can additonally harden it). i know how you would set up individual account. but for 5000 users you should use thunderbird if they have a CLI solution.

another question is regarding cpanel. cpanel is not meant for such high volume of users. at least not from what i've seen, so again while i do know how to set up a few accounts i don't know how you would do it en masse. if you are using a host, i am sure they can do it for you.

---

### Post by SeijiSensei on 2016-10-01
Frankly I think you would be better off using a commercial service like [ConstantContact]("http://constantcontact.com").

---

