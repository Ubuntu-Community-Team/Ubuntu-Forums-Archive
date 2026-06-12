---
title: "g++ error: expected primary-expression before ‘&lt;=’ token"
date: 2014-03-05
forum: Programming Talk
---

### Post by ac7nj on 2014-03-05
I'm getting an error from the compiler that I haven't been able to solve
Learning C++ from a book has been a chalenge so far and I'm stuck

```

/* 
* 241054Z FEB 2014
* Randy Williamson
* Practical C++ Programing O'Reily book
* chapter 6-1 generate letter grades
*/

#include <iostream>

int points;
char grade;

int main ()
{ 

    /* input from user */
    std::cout << "Enter total points " << '\n';
    std::cin >> points;
    
    /* alternation choices */
    
    if ((points >= 0) && (<= 60)){
        grade = 'F';
        std::cout << grade << '\n';
        }
        
    else if ((points >= 61) && (<= 70)){
        grade = 'D';
        std::cout << grade << '\n';
        }
        
    else if ((points >= 71) && (<= 80)){
        grade = 'C';
        std::cout << grade << '\n';
        }
        
    else if ((points >= 81) && (<= 90)){
        grade = 'B';
        std::cout << grade << '\n';
        }
        
    else if ((points >= 91) && (<= 100)){
        grade = 'A';
        std::cout << grade << '\n';
        }
        
    else
        std::cout << "ERROR!" << '\n';

    return(0);

}
 
```

The errors
randy@randy:~/workspace$ g++ -g -Wall -och6-1 ch6-1.cpp
ch6-1.cpp: In function ‘int main()’:
ch6-1.cpp:22:24: error: expected primary-expression before ‘<=’ token
ch6-1.cpp:27:30: error: expected primary-expression before ‘<=’ token
ch6-1.cpp:32:30: error: expected primary-expression before ‘<=’ token
ch6-1.cpp:37:30: error: expected primary-expression before ‘<=’ token
ch6-1.cpp:42:30: error: expected primary-expression before ‘<=’ token

Thank you

---

### Post by steeldriver on 2014-03-05
Try

```

    if ((points >= 0) && ([COLOR=#0000ff]**points **[/COLOR]<= 60)){
        grade = 'F';
        std::cout << grade << '\n';
        }

```

and so on

---

### Post by Vaphell on 2014-03-05
that said you don't have to do double checks in all steps
if you do these tests in increasing order and the test for 0-60 fails then you can skip the check for >60 in the next step. It has to be true because if it wasn't, earlier test for 0-60 would be true and you wouldn't be in this place. Same deal with other tiers.

<0 // error
<=60
<=70 // -60 already excluded
<=80 // -70 already excluded
<=90 // -80 already excluded
<=100 // -90 already excluded
>100 // error

---

### Post by ac7nj on 2014-03-06
thank you

---

