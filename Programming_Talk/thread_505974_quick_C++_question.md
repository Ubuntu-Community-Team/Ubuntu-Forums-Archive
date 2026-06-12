---
title: "quick C++ question"
date: 2007-07-21
forum: Programming Talk
---

### Post by sdmike on 2007-07-21
I was curious to know why when I enter a number of hours more than 169 does my program just doesn't end and give the statement?

```
#include <iostream>

float hours; // how many hours the employee worked for that week
float wages; // the employees hourly wage
float paycheck; //employees weekly pay
float overtime; //time and half 
int impossible; // impossible number of hours to work in a week

int main()
{
impossible = 168;

std::cout << "Enter how many hours you worked: ";
std::cin >> hours;
std::cout << "Enter your hourly wage here: ";
std::cin >> wages;

if (hours > impossible)
{
std::cout << "It is impossible to work that long in seven days.\n";
paycheck == 0;
}
else if (hours < 40)
{
paycheck = hours * wages;
std::cout << "You have earned $"<< paycheck << " for this week.\n";
}
else (hours > 40);
{
overtime = (hours - 40) / 2;
paycheck = (hours + overtime) * wages;
std::cout << "You have earned $"<< paycheck << " for this week.\n";
}
return (0);
}
```

```
Enter how many hours you worked: 190
Enter your hourly wage here: 8
It is impossible to work that long in seven days.
You have earned $2120 for this week.
```

---

### Post by endersshadow on 2007-07-21
```
else (hours > 40);
```

This line is missing an "if" and has an extra ;

It should look like this:

```
else if (hours > 40)
```

---

### Post by sdmike on 2007-07-21
It worked!

Thank You.

---

### Post by Wybiral on 2007-07-21
Remember that in C and C++ everything is a statement.

For instance, this program will actually compile:

```

int main()
{
    1;
    {2;}
    4 != 8;
    16 + 32;
    64 < 128;
    return 0;
}

```

You may get a warning telling you that the statements don't do anything, but it compiles none-the-less... And does absolutely nothing but return 0.

---

