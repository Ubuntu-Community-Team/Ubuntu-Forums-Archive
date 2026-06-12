---
title: "[ C++ ] Inheritance &amp; constructors - how do I use them ?"
date: 2010-02-04
forum: Programming Talk
---

### Post by SemiBuz on 2010-02-04
Let's say I've two classes, parent and the child - Bank and Account.
The Bank class needs to have a constructor to set the name of the bank and the Account class, the name of the account holder.

How would I achieve that ?

---

### Post by amauk on 2010-02-04
Unless I've misunderstood what you're asking,
something like this

```
class bank
{
public:
	// constructors
	bank();
	bank(std::string bank_name);

	// destructor
	~bank();

	set_name(std::string bank_name);

private:
	std::string m_bank_name;
};

bank::bank() { }

bank::bank(std::string bank_name)
{
	set_name(bank_name);
}

bank::~bank() { }

bank::set_name(std::string bank_name)
{
	m_bank_name = bank_name;
}
```

---

### Post by CptPicard on 2010-02-04
That is composition, not inheritance -- *an account is not a bank*.

---

### Post by radeon21 on 2010-02-04
Are you sure that you want the Account class to inherit from the Bank class?  The relationship is better described with "a Bank *has an* Account" (ie: the Accounts are members of the Bank class) than "an Account *is a* Bank" (an Account inherits from a Bank).

In general, with inheritance, a child is a more specific version of the parent.  An example of this relationship would be Bank (parent) and National Bank (child).  Here National Bank is a type of bank.  In your case, I doubt you want to say that an Account is a type of Bank.

Do you have any code that would give us a little more information about what you're trying to do?

---

### Post by SemiBuz on 2010-02-04
```
#include <iostream>
#include <string>

using namespace std;

class Bank
{
    string bankName;
    public:
        Bank(string e_bankName);
        string getBankName();
};

Bank::Bank(string e_bankName)
{
    this->bankName = e_bankName;
}

string Bank::getBankName()
{
    return this->bankName;
}

class Account : public Bank
{
    string accountHolder_fname, accountHolder_lname;
    double balance;
    public:
        Account(string e_accountHolder_fname, string e_accountHolder_lname, double e_accountBalance);
};

Account::Account(string e_accountHolder_fname, string e_accountHolder_lname, double e_accountBalance)
{
    this->accountHolder_fname = e_accountHolder_fname;
    this->accountHolder_lname = e_accountHolder_lname;
    this->balance = e_accountBalance;
}

int main(int argc, char *argv[])
{
    Account account("John", "Wilder", 100.00);

    return 0;
}

```If I want to use [COLOR=SeaGreen]account->getBankName()[/COLOR], it'll come up with an error because the Bank class constructor haven't yet been called.
The question is, how do I call it and from where ?

---

### Post by MadCow108 on 2010-02-04
first: as mentioned, you have a design problem.
Inheritance is "Is-A" relationship, an account is NOT a bank
have account link with a bank object (preferably over a smart pointer) or use an aggregate/composite structure

nevertheless you also have a coding error:
bank is missing a default constructor which is needed to use it like that.
either add a constructor with no arguments or call your defined on constructor like this:
```

Account::Account(string e_accountHolder_fname, string e_accountHolder_lname, double e_accountBalance) 
  : Bank::Bank("somebank"), accountHolder_fname(e_accountHolder_fname)
{
// fname already initialized above as an example, can be done with beneath stuff to
 this->accountHolder_lname = e_accountHolder_lname;
 this->balance = e_accountBalance;
}

```

the : behind the constructor defines an initializer list where you can initialize variables without temporaries (good for expensive objects and necessary for constant stuff) and call specific constructors of parent classes like in this example

---

### Post by amauk on 2010-02-04
First off, the way you've structured the classes isn't quite right

As others have said, Account shouldn't be extending Bank
(an account is not a special form of Bank)

You've got 3 actors in the code above
Customer
Bank
Account
Each actor should have it's own class

A customer has one or more accounts
so Account objects should be stored in a vector member variable of the Customer class

A bank has many customers
so customers should be stored in a vector member variable of the Bank class

I'd suggest using pointers, rather than real objects (as you're always going to be dealing with a subset of information - most likely returned from an SQL query?)

This way you can:
- Send the query off to the database
- Get back the subset of info
- Create the objects and populate with info (bank name, customer name, etc.)
- Populate each object's vector of pointers with the other related objects

---

### Post by SemiBuz on 2010-02-04
Thank you guys for the feedback / suggestions - will think about a  couple of things and get back to you tomorrow :)

> **amauk said:**
> 
I'd suggest using pointers, rather than real objects (as you're always going to be dealing with a subset of information - most likely returned from an SQL query?)


Not really - it's just for myself .. still learning ( as a hobby ).

---

### Post by amauk on 2010-02-04
well, mock up a database (the info has to be stord somewhere) :)

Anyway, inheritance should be used to specify specialist forms of something

Eg.
if you had different tiers of customer

class Customer
{
// any variables / methods that relate to all customers goes here
};

class GoldCustomer : public Customer
{
// special form of customer
// anything that relates to the gold customers goes here
};

class SilverCustomer : public Customer
{
// special form of customer
// anything that relates to the silver customers goes here
};

---

### Post by dwhitney67 on 2010-02-04
> **SemiBuz said:**
> Thank you guys for the feedback / suggestions - will think about a  couple of things and get back to you tomorrow :)

If you want the account to know to which bank it pertains to, what you could do is add a relationship within the account object that holds a reference to the bank object.  Sometimes this is referred to as 'registration' of a parent object.

For example:
```

class Bank
{
   ...
};

class Account
{
public:
   enum AcctType { SAVINGS, DRAFT, CD, CREDIT, ETC };

   Account(const unsigned int acctNum, const AcctType acctType, const Bank& bank);

   ...

private:
   unsigned int acctNum;
   AcctType     acctType;
   const Bank&  bank;
};

...

Account::Account(const unsigned int acctNum, const AcctType type, const Bank& bank)
   : acctNum(acctNum),
     acctType(acctType),
     bank(bank)
{
}

```
You should consider implementing a class that returns the next available account number.  Above I defined the account number as an unsigned int, but feel free to have it represented as a string if you wish.

The comment given earlier about defining a Customer class is good.  A Customer can have more than one account, and obviously a Bank has can have more than one Customer.

I would *not* recommend using an STL vector to store the Customer's accounts, but instead I would recommend an STL map.  The key would be the account number, and the value the Account object itself.

Similarly for the Customers; put them in an STL map, with the customer ID as the key, the Customer object as the value.  Yep, customers are not known by name anymore; just a number.  :-)

The rationale for using the STL map is that searches would occur more rapidly.  With a vector being basically glorified array, one would have to potentially search all records before finding the one of interest.

---

### Post by VertexPusher on 2010-02-05
Bank and Account don't have a parent/child relationship, but they may still share some common properties and associated code that you want to implement only once. This can be solved using multiple inheritance.

The name property may be a bad example to demonstrate the technique, but consider something like this: You have a class "Shop" and a class "Customer". Although a shop has many customers, and customers may buy at several shops, there is no parent/child relationship between them. A customer is not a special type of shop, nor vice versa. But both shops and customers have common properties, e.g. phone numbers.

Now imagine you have a class "Telephone" that you want to use to call shops or customers. The telephone doesn't care about the differences between shops and customers; all it needs is a phone number from either to establish a connection.

Now instead of defining separate call() methods for customers and shops (which is possible, but not elegant), you can define a class "Callable" that includes at least

- a property "phoneNumer"
- a method "setPhoneNumber"
- a method "getPhoneNumber"

Now you can implement the Telephone class with a single call() method that accepts a parameter of type Callable. To make this work with both customers and shops, make the Shop and Customer classes inherit from Callable. Now your program has zero redundancy. Since C++ allows multiple inheritance, you can do the same thing for other properties as well: postal addresses, email addresses, bank accounts ... anything that is shared "horizontally" between classes without a parent/child relationship.

---

### Post by CptPicard on 2010-02-05
One needs to add to the above, though, that there is also a strain in OOP design thought that tries to move away from sharing functionality/data in an inheritance hierarchy altogether and to prefer to "program to interfaces" which in turn form inheritance hierarchies and just specify the outward appearance of some contract, not any of its behavioural properties. The latter can easily lead to the [fragile base class problem]("http://en.wikipedia.org/wiki/Fragile_base_class").

By extension, multiple inheritance of functionality is multiply troublesome. Implementing many interfaces (inheriting from virtual base classes, in C++ terms) is, of course, a much more reasonable strategy.

---

