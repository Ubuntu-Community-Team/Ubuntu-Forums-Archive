---
title: "How do You Add Visitor Counts in Javascript?"
date: 2009-04-08
forum: Programming Talk
---

### Post by Penguin Guy on 2009-04-08
I would like to know how to add a visitor count and view count in Javascript with:

[LIST]
[*]Option to set it to only appear for certain IP addresses (mine).
[*]How many IP's have viewed it
[*]How many times it has been viewed
[/LIST]

Thanks.

---

### Post by 505 on 2009-04-08
To do it in javascript is actually quite difficult. Because javascript is executed client-side, you face the problem of storing the results server-side. To do it you would need javascript that calls a special page with certain arguments. That page can then write the results to a textfile/database on the server. However, for this you need a server-side script language for that page. If you do that, you might as well build the whole counter in that script language.

---

### Post by Zugzwang on 2009-04-08
> **Penguin Guy said:**
> I would like to know how to add a visitor count and view count in Javascript with:

...


You will not be able to do what you want without some support on the server side (e.g. using PHP, Perl, whatever), as JavaScript typically runs on the client side (you may run it on the server side, but this is a rather uncommon use, so you would have mentioned that in your post, I guess) only and is unable to distribute information back to the (web) server or to other clients except by requesting pages from the server, for which you would have to write a server-side script again.

What you might do however is something which does not require sending stuff back to the server, like for example a counter that counts how often *you* have visited the site yourself....until the browser cookies are cleared.

---

### Post by Penguin Guy on 2009-04-09
Ok, well thanks for the help guys.

---

