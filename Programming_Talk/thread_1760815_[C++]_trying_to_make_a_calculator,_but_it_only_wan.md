---
title: "[C++] trying to make a calculator, but it only wants to add"
date: 2011-05-17
forum: Programming Talk
---

### Post by u-noob-tu on 2011-05-17
so ive been teaching myself C++ for about 2 1/2 months now, mostly through free online tutorials, and a book or two. one example i found was to make a program that multiplies two numbers. i got that to work just fine, but in order to get better i like to add on to the examples i find by combining them. this time, im trying to make a program that adds, subtracts, divides and multiplies two numbers (i dont know how to make it work with more than two at this point). i think im pretty close to getting it to work, but each time i run it, it only adds the numbers, even if i tell it to do otherwise. not getting any errors, so i think im missing a semicolon somewhere. heres the source code: ```
#include <iostream>
#include <string>
using namespace std;
int mult (int x, int y);
int main()
{
    string answer;
    int x;
    int y;
    cout << "Give me two numbers: ";
    cin >> x >> y;
    cin.ignore();
    cout << "Do you want to add, multiply, subtract, or divide?\n";
    cin >> answer;
    cin.ignore();
    if ((answer == "Add"));
    {
        cout << "These two numbers equal "<< x+y <<".\n";
    }
    int mult (int x, int y);
    {
        return x+y;
    }
    if ((answer == "Multiply"));
    {
        cout << "These two numbers equal "<< x*y <<".\n";
    }
    int mult (int x, int y);
    {
        return x*y;
    }
    if ((answer == "Subtract"));
    {
        cout << "These two numbers equal "<< x-y <<".\n";
    }
    int mult (int x, int y);
    {
        return x-y;
    }
    if ((answer == "Divide"));
    {
        cout << "These two numbers equal "<< x/y <<".\n";        
    }
    int mult (int x, int y);
    {
        return x/y;
    }
}
```
again, im just a beginner, and my resources to teach myself are limited. any help would be much appreciated.

---

### Post by potat on 2011-05-17
I'm not sure what mult() does here. It seems like you are declaring a function inside main(), which you shouldn't do. Try this. 

```

#include <iostream>
#include <string>
using namespace std;
int mult (int x, int y);
int main()
{
    string answer;
    int x;
    int y;
    cout << "Give me two numbers: ";
    cin >> x >> y;
    cin.ignore();
    cout << "Do you want to add, multiply, subtract, or divide?\n";
    cin >> answer;
    cin.ignore();
    if ((answer == "Add"));
    {
        cout << "These two numbers equal "<< x+y <<".\n";
    }
    if ((answer == "Multiply"));
    {
        cout << "These two numbers equal "<< x*y <<".\n";
    }
    if ((answer == "Subtract"));
    {
        cout << "These two numbers equal "<< x-y <<".\n";
    }
    if ((answer == "Divide"));
    {
        cout << "These two numbers equal "<< x/y <<".\n";        
    }
}


```

---

### Post by u-noob-tu on 2011-05-17
thanks for the help. still only adds though. ive got a feeling its skipping the last three "if's" due to a missing semicolon or something.

EDIT: i didnt see that you took out the "return x*y" and the others. it works but it gives me all four answers at once now.

---

### Post by simeon87 on 2011-05-17
> **u-noob-tu said:**
> thanks for the help. still only adds though. ive got a feeling its skipping the last three "if's" due to a missing semicolon or something.

Actually, you have too many semicolons. There should not be any semicolons after an if-statement:

```
if ((answer == "Add")); // <-- remove these semicolons
    {
        cout << "These two numbers equal "<< x+y <<".\n";
    }
```

---

### Post by u-noob-tu on 2011-05-17
> **simeon87 said:**
> Actually, you have too many semicolons. There should not be any semicolons after an if-statement:

```
if ((answer == "Add")); // <-- remove these semicolons
    {
        cout << "These two numbers equal "<< x+y <<".\n";
    }
```
HA!!! that did it! sweet! thanks guys. if theres one thing ive learned about programming so far, its that you are guaranteed to screw up and miss something.

---

