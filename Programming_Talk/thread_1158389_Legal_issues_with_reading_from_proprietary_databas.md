---
title: "Legal issues with reading from proprietary database"
date: 2009-05-13
forum: Programming Talk
---

### Post by Bufke on 2009-05-13
Hi

I'm trying to figure this out but I have no idea.  My company uses a proprietary Foxpro program that stores data in Xbase format on our server.  The vendor already refused to let us connect directly to the database.  However all our data is in plain sight.  I can even cat the .DBF files.  It's all our data inside, we entered it ourself through the foxpro interface that is part of the program.  So is it legal to just use the data?  Maybe someone has had a similar experience.

---

### Post by Ferrat on 2009-05-13
Sounds really weird that they would restrict access for you to your own data, if it's so unsecure why even use it? there are better options out there

---

### Post by wmcbrine on 2009-05-13
I would say the vendor's stance is illegitimate. But IANAL.

---

### Post by perryrt on 2009-05-13
Depends on how you wrote the contract. After all, Google supposedly "owns" the rights to works that they scanned from public sources, so it's not impossible to think that a company says "we did something to it, so now it's ours!"

Doesn't mean you might not win in court.... but YMMV...and it could be expensive.

---

### Post by samjh on 2009-05-13
> **Bufke said:**
> Hi

I'm trying to figure this out but I have no idea.  My company uses a proprietary Foxpro program that stores data in Xbase format on our server.  The vendor already refused to let us connect directly to the database.  However all our data is in plain sight.  I can even cat the .DBF files.  It's all our data inside, we entered it ourself through the foxpro interface that is part of the program.  So is it legal to just use the data?  Maybe someone has had a similar experience.

A web forum is not the right place to ask for legal advice. ;)  Consult your company's lawyer.

Having said that, an ISV who refuses you access to data residing in your own database is... unusual.  How did this refusal come about?  Just curious.

---

### Post by Bufke on 2009-05-14
Thanks for the replies.  The goal is to move away from it ;)  but for now we need it and we need to move data from it.  I'm pretty sure the vendor means they refuse to let me access it, they want us to pay them to modify the program so it sends through xml or something like that.  We are a very small company and would rather not.  Plus I want control of our data, not to have to call up someone and pay because a user decides they want this new feature.

---

### Post by Dngrsone on 2009-05-14
Realistically, what are they going to do if you strip your data out of the database to move it over to another format?

They going to sue you for accessing their 'proprietary' database?  How could they prove you did so?  For all they know, you reentered the data from hardcopy.

Just open the database, write a little macro or script to copy your data to another format or whatever.  Do not publish the methods/macros/script you used in any format, and you should be fine.

---

