---
title: "Simple C++ Programming Problem"
date: 2007-02-22
forum: Programming Talk
---

### Post by Spinelli on 2007-02-22
I am currently taking an introductory programming class at my university. We are learning C++. At the end of each chapter in the text book their are several "programming projects". They are NOT assigned as homework. I just like figuring them out for fun. At the end of the second chapter I have encountered one that I have absolutely no idea how to solve. I am wondering if anyone has any ideas or hints. Any suggestions would be greatly appreciated.

> Write a program that reads in an integer that is greater than 1,000 and less than 1,000,000. Recall that the number must be entered without a comma. Display the number with a comma inserted where it belongs. (Hint: use the % operator)

```

#include <iostream>

using namespace std;

int main ()
{
    int number;
    cout << "Enter an integer between 1,000 and 1,000,000: ";
    cin >> number;
    if (1000 <= number <= 1000000)
        {
    // I don't know what to put here. Any ideas?
        }
    else
        cout  << "Invalid input";

    return 0;
}
```

---

### Post by LotsOfPhil on 2007-02-22
The % operator is called modulus (or modulo). It's the remainder.

17 % 10 = 7
To understand it, think back to elementary school. What is 17 divided by 10? 1 remainder 7. 

So, say someone enters 96743. What is 96743 % 1000 and how might that be useful to your task?

Also, you might want to make a loop so that someone can enter another value if they enter an invalid input.

---

### Post by Mirrorball on 2007-02-22
Hint: number % 1000. ;)

---

### Post by LotsOfPhil on 2007-02-22
P.S. I don't think that if loop is going to do what you want.

---

### Post by Spinelli on 2007-02-22
Thanks for the hints. I added some code, but it still doesn't work the way it is supposed to. This programming project is from chapter two of my text book. Chapter two covers cin, cout, data types, variable declarations, constant declarations, assignment statements, and arithmetic expressions. This leads me to believe that there is some sort of simple one line cout statement that will solve the problem. Is there a way to do it without if statements, switch statements, or loops?

```

#include <iostream>
using namespace std;

int main () 
{ 
  // BEGIN LOCAL VARIABLE DECLARATION 
  int number; // input: a number between 1000 and 1000000 
  // END LOCAL VARIABLE DECLARATION 
 
  // get user input 
  cout << "Enter and integer between 1,000 and 1,000,000 : "; 
  cin >> number; 
  
  if ((number < 1000000) && (number > 1000)) 
    { 
      if (number % 1000 == 0) 
        { 
          cout << number / 1000 << ",000" << endl; 
        } 
      else 
        { 
          cout << number / 1000 << ',' << number % 1000 << endl; 
        }
    } 
  else 
    { 
      cout << "Invalid input!" << endl; 
    } 
  return 0; 
} 

```

---

### Post by Mirrorball on 2007-02-22
Did it explain what "%03d" means?

---

### Post by Spinelli on 2007-02-23
> **Mirrorball said:**
> Did it explain what "%03d" means?

No I have not learned what "%03d" means. What does it mean? I hope my questions don't seem too stupid.

---

### Post by Lux Perpetua on 2007-02-23
> **Spinelli said:**
> No I have not learned what "%03d" means. What does it mean? I hope my questions don't seem too stupid.It means you want your number printed in decimal (that's the **d**), at least three characters wide (that's the **3**), and padded with zeroes if necessary (that's the **0**). 

...or that's what it would mean if you were using the C function printf, which you're not. Since you're using iostreams, look into the <iomanip> manipulators, especially setw and setfill. 

More info: [http://www.fredosaurus.com/notes-cpp/io/omanipulators.html](http://www.fredosaurus.com/notes-cpp/io/omanipulators.html)

---

