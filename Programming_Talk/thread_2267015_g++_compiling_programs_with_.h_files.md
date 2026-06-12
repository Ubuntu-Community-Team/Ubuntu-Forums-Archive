---
title: "g++ compiling programs with .h files"
date: 2015-02-26
forum: Programming Talk
---

### Post by Matthew_Cole on 2015-02-26
Hi! I'm trying to comple a .cpp file:

```
#include"Savings.h"
#include<iostream>
#include<iomanip>

using namespace std;
using namespace Cole;

int main()
{

    //create our savingsAccout objects
    SavingsAccount savings1, savings2;
    
    //bool var used to validate interest
    bool valInterest =  true;

    //used to temporarly stor such things as balances and interest rates
    double tempDouble;

    //greeting for user
    cout << "Hello! This program demonstrates the SavingsAccount class!\nIt will allow you to enter the initial values of two savings accouts\n";
    cout << "and allow you to choose a common interest rate for the two\n";

    //get initial savings accout balances
    cout << "Please input the inital budge for the first savings accout: ";
    cin >> tempDouble;
    savings1.setBal(tempDouble);
    
    cout << "Please input the inital budget for the second savings accout: ";
    cin >> tempDouble;
    savings2.setBal(tempDouble);

    //set inital interest rate
    cout << "Please enter a percent as the interest rate (Example: 50 = 50% .5 = 0.5%): ";
    cin >> tempDouble;

    valInterest = SavingsAccount::setInterestRate(tempDouble);

    //validate data
    while (valInterest == false)
    {
        cout << "Invalid entry, please enter a percent as the interest rate (Example: 50 = 50% .5 = 0.5%): ";
        cin >> tempDouble;
        
        valInterest = SavingsAccount::setInterestRate(tempDouble);
    
    }

    //we want our output to look like dollars and cents
    cout << setprecision(2) << fixed;
    cout << "After one month, the balance of the first accout will be $" << savings1.calcMonthlyInterest() << endl;
    cout << "After one month, the balance of the second accout will be $" << savings2.calcMonthlyInterest() << endl;

    //allow for a new percentage to be inputted
    cout << "Please enter a new percent as the interest rate (Example: 50 = 50% .5 = 0.5%): ";
    cin >> tempDouble;

    //this will validate the interest rate
    valInterest = SavingsAccount::setInterestRate(tempDouble);


    while (valInterest == false)
    {
        cout << "Invalid entry, please enter a percent as the interest rate between 0 and 50 percent: ";
        cin >> tempDouble;
        
        valInterest = SavingsAccount::setInterestRate(tempDouble);
    
    }
    

    //once again, read out the total ammount of both interest and principle
    cout << "After another month, the balance of the first accout will be $" << savings1.calcMonthlyInterest() << endl;
    cout << "After another month, the balance of the second accout will be $" << savings2.calcMonthlyInterest() << endl;

    cout << "Thanks for using!\n";

    return 0;
}
```

upon using the command line:
```
g++ file.cpp -o out.o
```

I get the following errors:

```

/tmp/ccg2fhXA.o: In function `main':
file.cpp:(.text+0xb5): undefined reference to `Cole::SavingsAccount::setBal(double)'
file.cpp:(.text+0xf7): undefined reference to `Cole::SavingsAccount::setBal(double)'
file.cpp:(.text+0x135): undefined reference to `Cole::SavingsAccount::setInterestRate(double)'
file.cpp:(.text+0x178): undefined reference to `Cole::SavingsAccount::setInterestRate(double)'
file.cpp:(.text+0x1ca): undefined reference to `Cole::SavingsAccount::calcMonthlyInterest()'
file.cpp:(.text+0x214): undefined reference to `Cole::SavingsAccount::calcMonthlyInterest()'
file.cpp:(.text+0x28d): undefined reference to `Cole::SavingsAccount::setInterestRate(double)'
file.cpp:(.text+0x2d0): undefined reference to `Cole::SavingsAccount::setInterestRate(double)'
file.cpp:(.text+0x2ed): undefined reference to `Cole::SavingsAccount::calcMonthlyInterest()'
file.cpp:(.text+0x337): undefined reference to `Cole::SavingsAccount::calcMonthlyInterest()'
collect2: error: ld returned 1 exit status
```

The .h file and the .cpp file for the SavingsAccount class are both found in the same directory as file.cpp . I have been searching for a solution online and I cant seem to find one. Any help would be greatly appriciated. Thanks!

---

### Post by spjackson on 2015-02-26
Welcome to the forums.

Assuming your other source file is Savings.cpp then:
```

g++ file.cpp Savings.cpp -o out.o

```
However, it would be somewhat strange to name the executable file out.o

---

