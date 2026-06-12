---
title: "[SOLVED] hotmail patch works but what are the bad side effects?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by lincoln32 on 2008-11-22
saw this on another board and it worked on one of my computers but before I change all of mine I wanted more info on negative side affects.?

open firefox and in the url bar type "about:config"
without the quotes of course...

Agree to the disclaimer and you will see a page of configuration options. ONLY edit the following:

general.useragent.vendor CHANGE the value of this to - Windows

general.useragent.vendorComment CHANGE the value of this to - Windows NT 6.0

general.useragent.vendorSub Change the value of this to - rv:1.9b5

---

### Post by jimmy the saint on 2008-11-22
Looks to me like you are simply telling ff to pretend to be a microsoft product.  Shouldn't really be that big of a deal.

I will say this though.  Doesn't make you a little uncomfortable leaving your data and personal communications in the hands of a company that would arbitrarily set limitations on how you can access that information?  If all you have to do is misrepresent your user agent (which browser you are using) that means there are not technical limitations, only ones set for their own sake.  I would certainly get my emails off of their servers and start a gmail account or find another provider.  

When you give control of your data to someone else, you better be able to have full confidence in them.  I can't say that disallowing access based on your browser choice is trustworthy move.

---

### Post by nhasian on 2008-11-22
actually you only need to change one thing.

Change the *general.useragent.vendor* variable from *Ubuntu* to *Firefox*.

Every time ubuntu updates firefox it seems to reset the general.useragent.vendor back to Ubuntu.  Hotmail doesnt like that, so just switch it back to Firefox and your all set.

---

### Post by CLomax on 2008-11-22
> **jimmy the saint said:**
> Looks to me like you are simply telling ff to pretend to be a microsoft product.  Shouldn't really be that big of a deal.

I will say this though.  Doesn't make you a little uncomfortable leaving your data and personal communications in the hands of a company that would arbitrarily set li...

+1. Left hotmail because of it.

---

### Post by Idefix82 on 2008-11-22
I simply can't believe how many people stick with a company that goes out of its way to introduce arbitrary incompatibilities with these peoples' system.
I am normally used to companies trying to please me as their customer as hard as they can and such behaviour as this youngest outrageous act by Microsoft would be rather decisive for me, especially seeing that there are much better alternatives.

---

### Post by lincoln32 on 2008-11-22
Like alot of other people on here I started with hotmail 10 years ago and liked it and still do for the most part and hate to email all my contacts and think that they will change their contact lists. The reason I went to hotmail was so that I would never have to change again. I may have to but
not till I have to. plus most of my online places have that as a contact
address it could take weeks to change. but still better than going back to vista even though I paid dearly for it and office and get more support here
and not near the bugs and more speed to boot, maybe I should start to change!!!

---

### Post by 3rdalbum on 2008-11-22
You could use Flock; it always identifies itself as Firefox rather than as Ubuntu. Plus it's a great browser.

---

### Post by lincoln32 on 2008-11-26
I guess that ms feels threatened. I hoped that hotmail was a stand alone division of ms and would still want us to view their ads

---

