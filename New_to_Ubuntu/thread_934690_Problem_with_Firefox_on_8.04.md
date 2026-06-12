---
title: "Problem with Firefox on 8.04"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by L Campbell on 2008-09-30
I have 8.04 running on a PC and have noticed what seems to be a problem with Firefox.  

When trying to log on to pay a credit card bill online, the credit card website would not log me in.  A couple of hours later, I logged in and paid the bill using MS Explorer.  What accounts for the difference?

TIA.

---

### Post by karlr42 on 2008-09-30
Some websites refuse connections from machines running Linux, maybe your bank does it.

---

### Post by appier on 2008-10-01
Although I have not personally encountered it, I have also heard of some banks refusing connections to Firefox.  Frequently, the server can be convinced to connect to Firefox by spoofing the user agent string.  This can be done by about:config then enter general.useragent.override and set the value.

Or, if you would like to be able to switch back and forth easily with a GUI, there is an extension called the "User Agent Switcher" which may be found at [https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

---

### Post by Tatty on 2008-10-01
It sounds like your cookie settings are not storing your cookies.  Have a look to see what your firefox preferences are.

---

### Post by L Campbell on 2008-10-01
> **Tatty said:**
> It sounds like your cookie settings are not storing your cookies.  Have a look to see what your firefox preferences are.

Thanks.

I went to the Preferences > Privacy page and everything is checked except 'always clear my private data when I close Firefox' and the 'keep until' is set to when 'they expire'.

I guess it must be something else causing the problem.

---

### Post by TopEnder on 2008-10-01
Lewis,

Had a similar problem with my Credit Union, it was solved by setting the Cookies to 'Always accept', you can find it here under:  Edit/ Preferences/ Pricacy - under Cookies check the first one "Always accept'  Hope this helps you, TopEnder

---

