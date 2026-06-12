---
title: "Darnit g++"
date: 2009-04-02
forum: Programming Talk
---

### Post by tdrusk on 2009-04-02
I had to do an assignment in my csci class. Everyone in there uses Microsoft Visual Studio. I wrote my program which had
```
class BankAccount 
{ 
    private: 
        int accountNumber; 
        double accountBalance; 
    public:     
        void enterAccountData(int); 
        void computeInterest(int, int); 
        void displayAccount(int); 
        double const static annualInterestRate = .03;         
};
```

It compiled and ran great with g++, but failed to compile in Microsoft Visual Studio on this line
```
double const static annualInterestRate = .03;    
```

I explained to my professor how I use Linux and g++. He told me I should compile at the lab and send it in. He never said that Microsoft Visual Studio was "required", but it is obvious that's what he wants us to use.  After I fixed the code I recieved a 75% for turning in a second attempt. I suppose I should be grateful, but I wish he was more understanding.

FML

---

### Post by dwhitney67 on 2009-04-02
You cannot initialize non-int values within a class.  What compiler allowed you to do that?

Try
```

class BankAccount
{
   ...

   static const double annualInterestRate;
};

double BankAccount::annualInterestRate = 0.03;

...

```

---

### Post by tdrusk on 2009-04-02
> **dwhitney67 said:**
> You cannot initialize non-int values within a class.  What compiler allowed you to do that?

Try
```

class BankAccount
{
   ...

   static const double annualInterestRate;
};

double BankAccount::annualInterestRate = 0.03;

...

```
g++ 4:4.3.1-1ubuntu2 from the Ubuntu repos. 

I did as you suggested and submitted. Still got a 75%.

---

### Post by eye208 on 2009-04-03
Compile with the -pedantic option to avoid these troubles in the future.

---

### Post by dwhitney67 on 2009-04-03
And perhaps with '-Wall -ansi'

---

### Post by tdrusk on 2009-04-03
Okay thanks. So by doing that it will make g++ a more standard compiler?

---

### Post by stevescripts on 2009-04-03
FWIW, g++ is probably *more* standards compliant than the MS compiler ...

Steve

---

