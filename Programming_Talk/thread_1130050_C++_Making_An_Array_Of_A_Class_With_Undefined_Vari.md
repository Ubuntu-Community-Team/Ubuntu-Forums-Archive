---
title: "C++ Making An Array Of A Class With Undefined Variables"
date: 2009-04-19
forum: Programming Talk
---

### Post by tdrusk on 2009-04-19
So I have
```

class BankAccount
{
private:
     int accountNumber;
     int x;
};
BankAccount array[10];
BankAccount::BankAccount(int acct, int a = 10)
{
     accountNumber = acct;
     x = a;
}
BankAccount::enterAccount()
{
     for(a = 0; a < arrayAmount; a++)
      {  
              cin >> array[a].accountNumber;
       }
}

```So basically I can't make an array with undeclared identifiers. 
I can declare the array as 
```
BankAccount *array[10]
```but then I get the error on the line
```
cin >> array[a].accountNumber;
```that says
```
        type is 'BankAccount *'
        did you intend to use '->' instead?
```This is an excellent hint from the compiler, but I am not sure where I should use ->
any tips?

btw it is against the rules to change 
```
BankAccount::BankAccount(int acct, int a = 10)
```
to
```
BankAccount::BankAccount(int acct=0, int a = 10)
```

---

### Post by kjohansen on 2009-04-19
Try the -> in

cin >> array[a].accountNumber;

as in 

cin >> array[a]->accountNumber;

---

### Post by tdrusk on 2009-04-19
as did i

---

### Post by tdrusk on 2009-04-19
Thanks for your help

---

### Post by dwhitney67 on 2009-04-19
Don't use an array; use an STL vector.  And avoid global variables.

Your BankAccount method(s) should not be aware of the array/vector.  They should only be aware of the account number and whatever 'x' is.

---

