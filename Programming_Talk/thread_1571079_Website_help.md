---
title: "Website help"
date: 2010-09-09
forum: Programming Talk
---

### Post by cj13579 on 2010-09-09
Hi all,

Before I start with my problem, may I give you a little backfround info...

At work we hire a security firm who every so often scan our routers for security holes etc and provides us with fixes. This isn't a human system but rather one that just emails us a report with links to their site for the fixes. 

Anyways, on it's latest search it has come back, rightly, saying that one of our sites uses plain text HTML pasword fields which are insecure. My problem is, the system isn't clever enough for us to tell it to ignore that site/port and according to the powers that be within my firm the data is sensetive enough for them to want keep the login system but the data is not sensetive enough for them to want to fork out for the HTTPS certificate fees which the Security system is saying is what we will have to do to pass the tests. Also, self-signing isn't really an option.

I can beat the test by just setting the input type to be "text" instead of "password", which the system just sees as a non-intrusicve form but it doesnt look particularly pretty!!

So, I was wondering, is there a way to use Javascript or something to dynamically mask the field with a "-", "*", dot or anything else?

You help as always is much appreciated!

Regards

Chris

---

### Post by Bachstelze on 2010-09-09
Even if you do mask the field, the passwords will travel on the wire in clear text. Hardly better in terms of security.

But if that's really what you want to do, <input type="password" ...>

---

### Post by cj13579 on 2010-09-09
Thanks for the reply!

That however, was what is was set to before. 

I understand that what I am doing is in no way more secure. I am merely trying to get round some the stupid rules they have in place whereby you can set up no exceptions for the scans.

Thanks again.

---

### Post by vikas.sood on 2010-09-09
[http://www.puremango.co.uk/mask/](http://www.puremango.co.uk/mask/)

---

### Post by cj13579 on 2010-09-09
That's great. Thank you.

It works great in all browsers apart from IE! Doh.

If anyone knows a fix for that I would be much obliged. If not, I will go and hassle some others!

Chris

---

