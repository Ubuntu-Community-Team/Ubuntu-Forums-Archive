---
title: "looking Python Gods advice / help"
date: 2008-04-15
forum: Programming Talk
---

### Post by Mynsc on 2008-04-15
Ok I am following the tutorial on [http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/) and I am on the section for OOPs. I am at the Inheritance section. I enter all the BankAccount class and follow exactly what the tutorial says to do. However when i get to testing it with.
>>> a = BankAccount(500) 

I get the message:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 3, in __init__
NameError: global name 'intialAmount' is not defined

Has anyone done this tutorial before, if so what am I missing?
Thank you
   mynsc

---

### Post by LaRoza on 2008-04-15
intialAmount?

Is that supposed to be initialAmount?

---

### Post by Mynsc on 2008-04-15
/bangsheadoffdesk

Ok thanks, ya it was a spelling mistake that i for some reason just wasnt seeing.
thanks

---

### Post by LaRoza on 2008-04-15
> **Mynsc said:**
> /bangsheadoffdesk

Ok thanks, ya it was a spelling mistake that i for some reason just wasnt seeing.
thanks

I didn't even look at the link, just saw the typo in the error message. 

Errors: They are your friend.

---

### Post by pmasiar on 2008-04-15
Main annoyance with compter programs is that CPU executes exactly what code says, not what we think it should say. :-)

---

