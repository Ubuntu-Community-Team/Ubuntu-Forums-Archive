---
title: "Developing web, want to disable sendmail..."
date: 2005-11-15
forum: Programming Talk
---

### Post by dudinatrix on 2005-11-15
I'm developing an ecommerce site on my local Ubuntu system with some data carried over from our live setup (customers/orders/etc.)  --  Problem is, when I do some testing during development, Ubuntu sends out emails (ie, "Your order has been shipped") and I want to avoid this to prevent actual customers from receiving anything.

How can I disable sendmail, and turn it back on later?

---

### Post by nagual on 2005-11-15
You should just be able to sudo /etc/init.d/sendmail stop

---

