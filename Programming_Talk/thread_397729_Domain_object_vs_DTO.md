---
title: "Domain object vs DTO"
date: 2007-03-31
forum: Programming Talk
---

### Post by blastus on 2007-03-31
Can someone please explain the difference between a Domain object and a DTO? 

I understand a Domain object is one that contains business logic (things like validation etc...) related to the domain in question. A DTO, on the other hand, contains no logic, exposes only what needs to be exposed, and is only used for the transfer of data between a service layer and a presentation layer for example.

I'm just not sure when and why DTOs may be used? What are the advantages of using DTOs? It seems to me that having a Domain Model + a set of DTOs just for transferring data between layers is redundant because the Domain objects can be used for the same thing or am I missing something? :(

---

### Post by Jmccaffrey on 2007-03-31
DTO's avoid duplicate storage of the data in question usually.  A DTO will provide managed access to the Model's DO in the most common applications of this pattern.

---

### Post by smokey edgy on 2007-03-31
Data Transfer Objects can be used to pass groups of related data across network connections (meaning they are serializable). Domain objects are usually fine-grained; there is a one-to-one kind of relationship between your objects and the actual real life entities they are representing (eg Customer, ChequingAccount, SavingsAccount, Loan, MutualFund, CreditCard, etc etc). 

Data Transfer Objects are usually composites of attributes and can represent some sort of a unit of work (eg MoneyTransferDetails containing attributes such as customerId, accountId, transferAmount, etc). As opposed to having your presentation layer call your service layer in a fine-grained fashion (eg call getCustomerId(customerName) then call getAccountIdForCustomer(customerId), etc), you can call a more coarse-grained service method such as getMoneyTransfer() that returns all that data in one object (which can translate into less network traffic and latency since you're doing less calls). 

DTOs are sometimes used in non-distributable applications, which many consider to be redundant and somewhat useless. They can also clutter your domain model (if they aren't there for a practical reason) and make things pretty messy. 

Personally, I don't believe this stuff is black and white; meaning there is a wrong or right way to do it. These patterns have generally evolved over time but there aren't no hard and fast rules to them. I'd say alot of times, folks tend to force their domains to fit into patterns, rather than let the domain evolve and manage the patterns as they develop. This sort of stuff gets abused all the time.

---

