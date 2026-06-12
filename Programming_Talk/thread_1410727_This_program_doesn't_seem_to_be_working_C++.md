---
title: "This program doesn't seem to be working C++"
date: 2010-02-19
forum: Programming Talk
---

### Post by NielsBhor on 2010-02-19
I am trying to read in data from a file. It's an assignment. I'm not asking for someone to do it. I did the programming part and can't seem to figure out why the file is not reading in the QTY, COST, and Name correctly. Please help me debug this code. I appreciate it.

```
/*VendingMachine.cpp */
#include "VendingMachine.h"

VendingMachine::VendingMachine()
{
    Q=0;
    N=0;
    D=0;
    P=0;
    QTY[50]=NULL;
    snack_name[MAXLEN]=NULL;
    cost[25]=NULL;
    totalm=0.0;
    
}

void VendingMachine::getFile()
{
    ifstream infile("vminput.txt");

    infile >> Q >> D >> N >> P;
    int i=0;

    for(i=0;i<P;i++)
    {
        infile >> snack_name[i] >> QTY[i] >> cost[i];
        
    }

}

void VendingMachine::displayMSG()
{
    char command=' ';
    float Dimes=0,Nickels=0,Quarters=0;

    while(1)
    {
        cout << "Enter a command: ";
        cin >> command;

        switch (command){
            case 'I':    VendingMachine::displayinv();
                        break;
            case 'Q':    Q=Q+1;
                        totalm=Q*0.25+totalm;
                        cout << "Balance = $"<< totalm << endl;
                        break;
            case 'N':    N=N+1;
                        totalm=N*.05+totalm;
                        cout << "Balance = $"<< totalm << endl;
                        break;
            case 'D':    D=D+1;
                        totalm=totalm+D*0.1;
                        cout << "Balance = $"<< totalm << endl;
                        break;
            case 'B':    VendingMachine::buyitem();
                        break;
            case 'R':    VendingMachine::returnmoney();
                        break;
            
        }
    }
}

void VendingMachine::displayinv()
{
    int i=0;
    cout << "Item # Name              Quantity   Price" <<endl;
    
    for (i=0;i<P;i++)
    {
        cout << "     "<<  i << " " << snack_name[i] << "                     " << QTY[i] << "          " << cost[i] << endl;
    }

    VendingMachine::displayMSG();
}

void VendingMachine::buyitem()
{
    int command2=0;
    int temp=0;
    cout << "Enter the item#: ";
    cin >> command2;

    if(totalm > cost[command2])
    {
        totalm = totalm - cost[command2];
        cout << "Purchased " << snack_name[command2] << "; change = $" << totalm << endl;
    }

    if(totalm < cost[command2])
    {
        cout << "Item #" << command2 << " is unavailable. Enter another command" << endl;
    }

    VendingMachine::displayMSG();

}

void VendingMachine::returnmoney()
{
}
``````
/*VendingMachine.h */
#include <iostream>
#include <iomanip>
#include <fstream>

#define MAXLEN 15

using namespace std;

class VendingMachine
{
public:
    VendingMachine(); //default constructor
    void getFile(); //get data file vminput.txt
    void displayMSG(); //display messages and commands
    void displayinv();
    void buyitem();
    void returnmoney();

    int 
        Q,
        D,
        N,
        P,
        QTY[50];
    
    char snack_name[MAXLEN];

    float 
        cost[25],
        totalm;
};
```Finally the main file
```
#include "VendingMachine.h"

void main()
{
    VendingMachine VM;

    VM.getFile();
    VM.displayMSG();
    
}
```This assignment isn't completed as you noticed the class member function is missing. I purposefully did not fill those in to test sections of the code. Eventually, I will fill those in myself.

Here is the vminput.txt file. Any help would be very appreciated.

> 
10
10
10
5
Snickers
10
$0.75
Chips
5
$1.25
Skittles
1
$0.50
Doritos
6
$1.50
Pretzels
2
$1.00


After you compiled, hit 'I' at the command prompt. You'll see what I mean.

---

### Post by dwhitney67 on 2010-02-19
Help for homework assignments is not to be given, but just to get you on your way, I immediately saw some poor choices and errors in your coding.

The first... when defining a string, do not use a char array; use the STL string.

Second, and only if you ignore my first advice above, when initializing a member data array, do not use the assignment operator.  Use memcpy() or the std namespace's method fill().
```

char array[50];

memcpy(array, 0, sizeof(array));

// or

std::fill(array, array + 50, 0);

```

Lastly, and this is the most important issue, is that you inputting of data for the snack name, quantity of the snack, and the snack's cost.  This will not work:
```

infile >> snack_name[i] >> QTY[i] >> cost[i]; 

```
Look how you have declared each of the above.  The QTY part is ok, if you assume that your machine will only have 50 items in it.  But I would not bet on it with the variable 'P' possibly being a larger number.

But the other issue is that the 'snack_name' and the 'cost' are declared as a char-array; not an *array* of char-array objects.  Thus you are reading a character at a time, not the desired string.


Re-factor your code; look at the STL string and the STL vector.  Avoid using fixed-sized arrays for variable data.  Also, consider treating the cost of a product as a float, not a string; this will require you to update your input file to remove each occurrence of the dollar-sign symbol.

---

### Post by Zugzwang on 2010-02-19
Have you tried checking if "inFile.fail()" is set after you read the file? If this is the case, some of the input could not be parsed. Try to find out at which point in the file the problem lies.

---

### Post by NielsBhor on 2010-02-19
Thank you dwhitney.

I fixed it. You're write about the char array reading one character at a time instead of a string.

Well, I made the effort of doing the code. Without help from experienced people, I can sit on the seat all month or year and still could not find out the problem I have.

---

### Post by Zugzwang on 2010-02-19
> **NielsBhor said:**
> Well, I made the effort of doing the code. Without help from experienced people, I can sit on the seat all month or year and still could not find out the problem I have.

This is what debuggers are good for. You can execute your program step-by-step and see when it starts to deviate from the expected behaviour. This usually helps a lot, especially when beginning to program.

---

### Post by dwhitney67 on 2010-02-19
> **NielsBhor said:**
> Thank you dwhitney.

I fixed it. You're write about the char array reading one character at a time instead of a string.

Well, I made the effort of doing the code. Without help from experienced people, I can sit on the seat all month or year and still could not find out the problem I have.

Let me know when you are done with the assignment; I'll show you how I would've done it.

Btw, depending on how modern a vending machine is, most use a product-code to identify the product, not the name of the snack.  For instance, if you want a Snickers bar, then you would select A1 or something like that.

If the goal of your professor is to get you to develop a vending machine application where given an initial inventory, you could process sales, give change, etc., you probably will want to consider re-factoring your code for such.

Since you are learning OOP (and presumably OOD at the same time), I would not couple the VendingMachine class with the product (snack) information.  These are separate entities.  The former contains products.  Consider this:
```

struct Product
{
   // product attributes (eg. name, quantity, cost)
};

class VendingMachine
{
public:
   ...

private:
   int quarters;
   int dimes;
   int nickels;

   // define map which has unique keys, where the key is the
   // product code.  The map has values representing the product
   // associated with the product code.
   //
   std::map<std::string, Product> products;
};

```

---

