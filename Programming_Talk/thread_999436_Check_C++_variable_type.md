---
title: "Check C++ variable type"
date: 2008-12-01
forum: Programming Talk
---

### Post by fatmarik on 2008-12-01
So I am currently learning C++ and decided to make a program that tests my skills I have learned so far. Now in my code I want to check if the value that the user enters is a double, if it is not a double I will put a if loop and ask them to reenter it. The problem I have is how do I go about checking what type of variable the user enters, ex- if a user enters a char or string, I can output an error message. Here is my code:

```
//cubes a user entered number
#include <iostream>
using namespace std;

double cube(double n); //function prototype

int main()
{
        cout << "Enter the number you want to cube: "; //ask user to input number
        double user;
        cin >> user;  //user entering the number

        cout << "The cube of " << user << " is " << cube(user) << "." << endl; //displaying the cubed number

        return 0;
}

double cube (double n) //function that cubes the number
{
        return n*n*n; // cubing the number and returning it
}
```

---

### Post by Mr.Macdonald on 2008-12-01
I won't write any code but

1.234566 % 1 == .234566
1%1 == 0

while (num%1 == 0) {
     prompt for a double
}

this works for floats too, why do you need to make sure it is a double (decimal number?), if you assign a value to a double then it is a double

---

### Post by dribeas on 2008-12-02
> **fatmarik said:**
> 
```
double user;
        cin >> user;  //user entering the number

```

You should check the result of the 'cin >> user' operation and/or the state of the stream after trying to read. If the data in the stream cannot be converted into a stream (it is a character) then the operation will fail (this can be checked either converting the stream to a bool [implicitly in an if suffices] or directly querying the stream:

```

// option 1
if ( !(cin >> user) ) {

// option 2
cin >> user;
if ( cin.fail() ) {

```

After checking that the read failed you should clear the error bits in the stream (.clear()) and clear the offending data out of the buffer (if the operation failed then the data is not removed from the stream).

---

### Post by mdurham on 2008-12-02
You can't tell if a number entered (typed on a keyboard) is a double or not, the concept doesn't exist. It's only a double, float or int if you make it so in the program.
-1,  1,  1.1,  1.111111111 could all be doubles if you want them to be.
Cheers, Mike

---

### Post by StOoZ on 2008-12-02
you can always use C++ RTTI ability :
> int i;

// ...

   typeid(i) == typeid(int)    // True

   typeid(8) == typeid(int)    // True

// ...



use 'typeid' as shown above.

---

### Post by mdurham on 2008-12-02
> **StOoZ said:**
> you can always use C++ RTTI ability :



use 'typeid' as shown above.

How does that check what the user has entered"?

---

