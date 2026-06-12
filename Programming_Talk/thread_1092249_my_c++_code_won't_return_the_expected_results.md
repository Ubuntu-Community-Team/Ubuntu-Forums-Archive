---
title: "my c++ code won't return the expected results"
date: 2009-03-10
forum: Programming Talk
---

### Post by bigfas on 2009-03-10
please help,

I'm runing ubuntu 8.10, I write my programs using g++ (sudo apt-get install g++) and emacs ( sudo apt-get install emacs)
I've been doing c++ programming for the last 3 months and I never had any problem, since recently every program I write doesn't return the expected result, not even simple ones like 

#include <iostream>
using namespace std;

int main()
{
int a, b ;
int result = a + b ;
 cout <<"Enter a: "<<endl;
cin >> a;
 cout <<"Enter b: "<<endl;
cin >> b;
 cout <<"The result is: "<< result <<endl;
return 0;
}


here's the result

[http://img9.imageshack.us/my.php?image=wtfoyi.jpg](http://img9.imageshack.us/my.php?image=wtfoyi.jpg)

I really don't know what's the problem. :( I've even formated my hard drive and reinstalled ubuntu but the problem remains.

---

### Post by simeon87 on 2009-03-10
Try this:

```

#include <iostream>
using namespace std;

int main()
{
int a, b ;
cout <<"Enter a: "<<endl;
cin >> a;
cout <<"Enter b: "<<endl;
cin >> b;
int result = a + b ;
cout <<"The result is: "<< result <<endl;
return 0;
}

```

When you do an assignment, it happens at that moment in time with the current values of a and b. So when you write result = a + b, you have to do it at a moment when you know the values of a and b. This is after you've received the input from the user. When you do it before a and/or b have received a value, the results are undefined, you're summing random memory now which results in these weird values.

---

### Post by BugenhagenXIII on 2009-03-10
EDIT: simeon87 beat me to it.

You're using a and b before you assign values to them.  Try this
```

#include <iostream>
using namespace std;

int main()
{
  int a, b, result;
  cout <<"Enter a: "<<endl;
  cin >> a;
  cout <<"Enter b: "<<endl;
  cin >> b;
  result = a + b;
  cout <<"The result is: "<< result <<endl;
  return 0;
}

```

---

### Post by issih on 2009-03-10
Your solution is above. Note that an expression only happens momentarily, so the statement

```
result = a+b;
```

takes the value currently stored in a and the value currently stored in b and adds them. it is not like a spreadsheet, and will not update the value in result if the values of a and b change at a later point in time, you must explicitly tell the program to recalculate the result if a or b changes.

Your strange answer is appearing because you don't initialise your variables a and b. Consequently the value of those variables after you create them is simply whatever the integer represention of the byte structure that was already present in the memory that the system assigns you to store those variable. The values in a and b after initialisation are therefore somewhat random, and when you add them together you get a random result.

if you initialise your variables like this 

```

int a = 1;
int b = 2;
```

your answer using the rest of your code would always be 3, quite regardless of the entered numbers, because you only calculate the value in result from the value in a and b just after initialisation.

N.B. it is always good programming practice to explicitly initialise your variables, in order to avoid this kind of confusion

Hope that helps

---

### Post by abhilashm86 on 2009-03-10
[PHP]#include <iostream>
using namespace std;

int main()
{
        int a, b;
        int result=0;
        cout <<"Enter a: "<<endl;
        cin >> a;
        cout <<"Enter b: "<<endl;
        cin >> b;
        result = a + b;
        cout <<"The result is: "<< result <<endl;
}
[/PHP]

actually you had declared result before taking user inputs.
So compiler takes junk values and adds up and stores it in result variable,
hence its not system error, its programmer error.

---

### Post by Bodsda on 2009-03-10
I wont bother telling you the same as everyone else, but i just thought i'd mention something that would make your code easier to read.

Instead of placing each statement on a new line try placing the cin on the same line as the cout that it is being used with. For example

[PHP]
#include <iostream>
using namespace std;

int a, b;

cout << "\nEnter a: "; cin >> a;
cout << "\nEnter b: "; cin >> b;
cout << "\nResult of a + b is: " << a+b << endl;
[/PHP]

Notice on the third cout statement, by doing the addition of the variables there we exclude the need for the result variable you were using and it minimizes the amount of code needed to write.

Thanks

Bodsda

---

### Post by bigfas on 2009-03-10
is incredible how I got confused and get all the "c++ ABC " wrong, is just that lately I've worked a lot with functional programming languages and in some wired way I forgot that c++ is an imperative programming language, I guess from now on I will try to learn only one language programming and then moving to the next .

---

### Post by nvteighen on 2009-03-10
> **bigfas said:**
> is incredible how i got confused and get all the "c++ abc " wrong, is just that lately i've worked a lot with functional programming languages and in some wired way i forgot that c++ is an imperative programming language, i guess from now on i will try to learn only one language programming and then moving to the next .

Great! :D

Though, I don't see the "functional" in your original code... that result = a + b would probably also fail in a functional language, unless you do:

```

; In Scheme
(define (result a b)
  (+ a b))

```

---

### Post by Bodsda on 2009-03-10
> **bigfas said:**
> is incredible how I got confused and get all the "c++ ABC " wrong, is just that lately I've worked a lot with functional programming languages and in some wired way I forgot that c++ is an imperative programming language, I guess from now on I will try to learn only one language programming and then moving to the next .

Ive just done it recently as well. About 4 months ago I stopped learning python and began learning C++, but the other day i needed to show someone how to do a little python scripting (they were just curious) and I found myself forgetting the simplest of things such as raw_input() and upper(), I even almost forgot about the indenting and tried using curly braces :) anyway i decided to learn one language at a time aswell. Although i do delve back into python every week or so to keep things fresh in the mind :)

---

### Post by shababhsiddique on 2009-05-11
> **Bodsda said:**
> Ive just done it recently as well. About 4 months ago I stopped learning python and began learning C++, but the other day i needed to show someone how to do a little python scripting (they were just curious) and I found myself forgetting the simplest of things such as raw_input() and upper(), I even almost forgot about the indenting and tried using curly braces :) anyway i decided to learn one language at a time aswell. Although i do delve back into python every week or so to keep things fresh in the mind :)

you are absolutely right, its all about practice..

---

### Post by Ackowa on 2009-05-12
> **nvteighen said:**
> Great! :D

Though, I don't see the "functional" in your original code... that result = a + b would probably also fail in a functional language, unless you do:

```

; In Scheme
(define (result a b)
  (+ a b))

```

It will work in a functional language since result = a + b doesn't save the value of a + b but rather the statement, so it isn't evalutated until you use result, which in his case would be in the cout statement

---

