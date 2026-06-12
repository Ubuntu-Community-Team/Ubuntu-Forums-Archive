---
title: "[C++] Confused by OOP constructors."
date: 2009-07-25
forum: Programming Talk
---

### Post by credobyte on 2009-07-25
While trying to learn OOP, I've found one thing confusing me - constructors ! Below are two examples of C++ constructors ( both examples are taken from the internet, so .. don't say I'm trying to invent something new ), but only one of them is valid ( I can't seem to compile B example ).

Is A the one and only "correct" way of using constructors ( instead of B, which I suspect was just a bad example ) ?

A:
```
class Account {
    public:
        int balance;
    
    Account() // class constructor
    {
        balance = 0;
    }
};

```B:
```
class Account {
    public:
        int balance;
        
    Account::Account()
    {
        balance = 0;
    }
};
```

---

### Post by dwhitney67 on 2009-07-25
In example B, the constructor is defined as if it where implemented outside of the class declaration.  In other words, this would compile:
```

class Account
{
public:
   int balance;

   Account();  // this is only a declaration.
};  // end of class declaration

// implementation of the Account constructor; it is prefaced with the
// Account class name and the scope operator "::".
Account::Account()
{
   balance = 0;
}

```

---

### Post by credobyte on 2009-07-25
Thnx, got the idea :)

---

### Post by issih on 2009-07-25
The Account:: bit is used to inform the compiler that the method being defined belongs to the Account class. Clearly this is unnecessary within the class definition itself.

Within the class definition you can define method stubs, and static fields, which are not defined/initialise within the class itself. nothing within the class itself should be prefaced with the Account:: bit.

When you then define the method/initialise the field outside of the class definition you use the Account:: bit to tell the compiler exactly what bit of code you are defining.

In addition to this you would use the Account:: qualifier if you made a subclass with virtual methods, and wanted to explicitly call an overridden superclass method.

Hope that helps

---

### Post by dribeas on 2009-07-27
The second snippet is incorrect. It used to compile with g++ 3.x compilers, but you the extra qualifying Account:: use, while inside the class scope, is incorrect.

That qualifier is required while outside of the class scope to refer to members or attributes that are defined inside of the class.

---

### Post by Sockerdrickan on 2009-07-27
Both constructors suck. Use the following

[php]
class Account {
    public:
        int balance;
    
    Account(): balance() {}
};[/php]

---

### Post by credobyte on 2009-07-27
> **Tux0r said:**
> Both constructors suck. Use the following

[php]
class Account {
    public:
        int balance;
    
    Account(): balance() {}
};[/php]

balance() - I don't have such a function :-k

---

### Post by dribeas on 2009-07-27
> **credobyte said:**
> balance() - I don't have such a function :-k

That is not actually a function. The code between the colon (:) and the open curly brace ({) in the constructor is called initialization list, and is a set of comma separated calls to constructors (your base constructors / attribute constructors). In that scope, the call 'balance()' is a call to the default constructor of the attribute 'balance'. For basic (primitive) types, that is actually value-initialization that ends up meaning set to 0. A more explicit way of writing it (that also allows you to define other values) would be:

```

class Account {
public:
   int balance;
   Account() : balance(0) {}
};

```

---

### Post by credobyte on 2009-07-27
> **dribeas said:**
> That is not actually a function. The code between the colon (:) and the open curly brace ({) in the constructor is called initialization list, and is a set of comma separated calls to constructors (your base constructors / attribute constructors). In that scope, the call 'balance()' is a call to the default constructor of the attribute 'balance'. For basic (primitive) types, that is actually value-initialization that ends up meaning set to 0. A more explicit way of writing it (that also allows you to define other values) would be:

```

class Account {
public:
   int balance;
   Account() : balance(0) {}
};

```

Thank you for an explanation :) If all previous examples ( except the one in my previous post ) suck, how do I "construct" something that does have something more than just a variable initialization ?

---

### Post by Sockerdrickan on 2009-07-27
> **credobyte said:**
> Thank you for an explanation :) If all previous examples ( except the one in my previous post ) suck, how do I "construct" something that does have something more than just a variable initialization ?
Code goes in the ctor definition:
[php]class Account {
    public:
        int balance;
        std::string foo;
    
    Account(): balance(),foo("Hi!") {
        //Code here
    }
};[/php]Is that what you meant?

---

