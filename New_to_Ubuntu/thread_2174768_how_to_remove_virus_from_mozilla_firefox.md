---
title: "how to remove virus from mozilla firefox"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by emiliano_1975 on 2013-09-16
Hello to everybody.

I'm using ubuntu 12.04 on my laptop. My browser, "mozilla firefox for ubuntu canonical - 1.0", doesn't work correctly. I think it has infected by virus. When I open whatever link or page a popup appear. Many alert messages open continuously. And so on...

Can anybody give me a suggestion how to remove the virus? 

Thanks.

---

### Post by mastablasta on 2013-09-16
what kind od alert message? what does it say?

---

### Post by carl4926 on 2013-09-16
One thing to try
Is rename the hidden folder .mozilla to .oldmozilla

---

### Post by emiliano_1975 on 2013-09-16
The message I receive when I try to open a page says:

Security Warning

Although this page is encrypted, the information you have entered is to be sent over an unencrypted connection and could easily be read by a third party.
Are you sure you want to continue sending this information?

---

### Post by emiliano_1975 on 2013-09-16
I've renamed the hidden folder .mozilla to .oldmozilla and all problems are disappeared. 

Thank you very much carl4926 and mastablasta

---

### Post by FiremanEd on 2013-09-16
Hello emilano,

The message in Mozilla (Firefox) that you are getting 

> Security Warning

Although this page is encrypted, the information you have entered is to be sent over an unencrypted connection and could easily be read by a third party.
Are you sure you want to continue sending this information? 
is not a virus, but rather a feature in which the Mozilla (Firefox) developers have implemented into the browser.  To put it simply, I believe that the poopup means that the login form submits to a javascript. The javascript does some setting of form variables and such depending on the page you're logging in from, then submits the login form. It turns out that Firefox, because it doesn't know exactly what the javascript is going to do on the client side, has to assume that the javascript is submitting the form data to an unencrypted page.

It appears that this message cannot be turned off after I searched for solutions in the various mozilla & firefox forums.  Think of the message as a reminder that you need to be alert to the dangers of websites that may be questionable.

---

### Post by buzzingrobot on 2013-09-16
The warning should only appear in the specific circumstances described in the message.  Suspect some forms data was somehow left inapproriately cached, triggering the warning anytime a page was opened.

---

### Post by philinux on 2013-09-16
> **buzzingrobot said:**
> The warning should only appear in the specific circumstances described in the message.  Suspect some forms data was somehow left inapproriately cached, triggering the warning anytime a page was opened.

+1. Probably clearing the cache would have sorted it.

---

