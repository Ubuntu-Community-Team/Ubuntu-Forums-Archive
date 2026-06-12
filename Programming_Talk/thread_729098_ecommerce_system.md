---
title: "ecommerce system"
date: 2008-03-19
forum: Programming Talk
---

### Post by lapubell on 2008-03-19
I am working with a guy on building a site with a really simple payment process.  I don't know how to implement a payment process that isn't rediculous overkill.  We don't needs carts, inventory, or anything like that, just a simple recurring payment.

It is basically a member site that lets you calculate your golf handicap.  Here is what we need:

Signup page : member info
Payment Info : SSL? or other system to handle the monies
*if payment goes through* -> log user in and bill them again next year
*if payment does not go through* -> error message of some kind that won't create the new user

everything I have seen online is way too big of a system for this.  We are looking for slim, easy and lightweight.  We want it to be on our site with our branding and not bouncing the user to some 3rd party site (maybe ok with an iframe, dependning on how it looks) but also don't want to deal with storing the credt card info ourselves.

Any ideas?

---

### Post by stevescripts on 2008-03-19
The last time I looked  into doing something similar - I found no simple, secure, inexpensive way to set up accepting credit cards via the internet.

In my *other* line of business, we recently had to start accepting credit cards,
to satisfy our best customer.  (not via the internet, but by phone).

Unfortunately, it is a PITA and relatively expensive.

Hope someone else comes forward with a good solution.

Sorry to be negative, just sharing my unfortunate experience.

Steve

---

### Post by thomasaaron on 2008-03-19
You might look at OS Commerce. If you know PHP, you could probably make it do what you want it to.

---

### Post by pmasiar on 2008-03-19
Satchmo is ecommerce site based on Django (in Python). Usually cleaner code than average PHP :-)

---

### Post by lnostdal on 2008-03-19
wait, regardless whether oscommerce or zen cart is actually what you're (the OP) after you (or anyone else reading this) should consider zen cart instead of oscommerce

oscommerce and zen cart are basically equal but zen cart has cleaned up much of the mess done in oscommerce with regards to lack of separation of html/css and code etc.

---

### Post by supirman on 2008-03-19
You need a merchant account and code to interface with the payment gateway.  The most popular to use is authorize.net

For an example with authorize.net, see [http://www.merchant-account-services.org/article/authorize-net-php-integration](http://www.merchant-account-services.org/article/authorize-net-php-integration)

That was from a quick google search.  I'm sure you can find many others, and there are likely many projects doing such things already.

---

