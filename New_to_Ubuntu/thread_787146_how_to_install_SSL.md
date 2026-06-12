---
title: "how to install SSL"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by GoCool on 2008-05-08
How do I install SSL in ubuntu?

---

### Post by Monicker on 2008-05-08
What are you trying to do in regards to ssl?  Are you trying to manually compile an application with ssl support?

If you are compiling something then you most likely need to install the libssl-dev package in order to get ssl support for it. 

I have a feeling you may be talking about something else altogether though.

---

### Post by GoCool on 2008-05-08
> **Monicker said:**
> I have a feeling you may be talking about something else altogether though.
LOL...definitely nothing fancy. I am configuring my scanner, and it is giving me a little too many configurable options. When I put it's ipaddress (ip of the scanner) in my browser, it does take me to a configuration page but gives the following warning

> SSL is not set-up. Please set up SSL after admin logins to secure safety of the information.

And when ever I do any changes it pops up an error

> Socket Connect Error

But the changes are stay put.

---

### Post by Monicker on 2008-05-08
Your browswer will already have ssl support.  You can verify this yourself by going to any web page which uses ssl.  Try [https://www.paypal.com](https://www.paypal.com) , for example.  If you can view that page then the problem is not ssl in your browser.


It sounds like it needs to be enabled on the scanner side.  What model scanner is this?

---

### Post by GoCool on 2008-05-08
> **Monicker said:**
> Your browswer will already have ssl support.  You can verify this yourself by going to any web page which uses ssl.  Try [https://www.paypal.com](https://www.paypal.com) , for example.  If you can view that page then the problem is not ssl in your browser.


It sounds like it needs to be enabled on the scanner side.  What model scanner is this?

Thank you Monicker. I am using a KonicaMinolta BizHub C250, its a printer cum scanner.
Let me see if there are any options in the configuration page.

---

