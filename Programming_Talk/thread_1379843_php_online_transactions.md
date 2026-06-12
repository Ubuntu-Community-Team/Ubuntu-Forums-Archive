---
title: "php online transactions"
date: 2010-01-13
forum: Programming Talk
---

### Post by korvirlol on 2010-01-13
I may need to start supporting this soon, and after doing some fruitless searching (pretty much just finding the documentation on php.net) i havent found a ton of information on what I would need to do to be able to support online financial transactions.

Of course i know about the obvious things like SSL and all that goodness, but i still feel like i am no where near educated enough about this to even consider implementing it.

Can anyone suggest some informational sites about things i van use to get educated about the subject? Of course helpful advice is also greatly appreciated!

thanks in advance.

---

### Post by Hellkeepa on 2010-01-13
HELLo!

I suspect you're talking about database transactions, in other words the ability to roll back a bunch of commands to the database if one of them fails? If so, then you should be looking at the documentation for the database system you're using, not PHP.
Otherwise, I'm afraid you'll have to be a bit more descriptive on what you want to accomplish, and why.

Happy codin'!

---

### Post by korvirlol on 2010-01-13
nope, i meant credit card processing. 

Judging from php.net, the only one offered through PHP is MVCE, but i dont know the other prerequisites i need before i can support something like this. Which is why i was looking for good literature about online credit card transactions.

---

### Post by Hellkeepa on 2010-01-13
HELLo!

Generally the service providers for the solution you decide to pick has an API which makes it quite easy to implement this, all you need in addition is to set the server up to use SSL. Also, make sure that you store personal data about your customers in a safe manner, and in accordance with the local law. Credit card data should never be stored, and is usually a violation of the terms of the transaction solution you pick.

Rolling your own solution from the scratch isn't possible, unless you're working for a bank or some other financial institution which'll give you access to their financial servers.

Happy codin'!

---

