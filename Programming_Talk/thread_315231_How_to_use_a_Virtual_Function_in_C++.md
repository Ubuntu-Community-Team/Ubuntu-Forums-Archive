---
title: "How to use a Virtual Function in C++"
date: 2006-12-08
forum: Programming Talk
---

### Post by thenetduck on 2006-12-08
Hi, 
 I am building a simulation of a bank and have program kind of built like this. 

 Base Class --- Account
 Derived Classes --- Loan, Checking, Savings


 The Derived Classes inherit the Account class. I want to call a function from the Loan, Checking, or Savings class kind of like this.

```

 Account accounts[3];
 accounts[0] = Checking();
 accounts[0].getTransactionHistory();

```

I am trying to use virtual functions in my derived classes, but it calls the getTransactionHistory() from my Account Class. Account is semi Abstract so it does me no good. Does anyone know how to work through this? Or how to use virtual functions correctly? Thanks,
 The Net Duck

---

### Post by duff on 2006-12-08
Only works for pointers. So try:```
Account *accounts[3];
 accounts[0] = new Checking();
 accounts[0]->getTransactionHistory();
```

---

