---
title: "C++ programming help"
date: 2010-12-21
forum: Programming Talk
---

### Post by kdizil on 2010-12-21
im trying to write  c++ program the tells the user to input numbers from 8 to 23 and if they type the wrong one it says wrong.
```
#include <iostream>

using namespace std;

int main(){
    int x(8),n;
cout<<"type numbers from 8 to 23"<<endl;
    for(x=8;x<=23;x++){
    cin>>n;
    if (x/=n){
cout<<"wrong!!!"<<endl;}
else {
x++;}
    }

}

```
can someone tell me why it doesnt work please?

---

### Post by dwhitney67 on 2010-12-21
How many numbers do you want the user to enter?  Figure this out because you will require a for-loop for this if N > 1.

Now, as for the inputted numbers that the user enters, validate these using an if-statement to ensure the number is within the range of 8 to 23.  There's no need for a for-loop for this test; only an if-statement.

Another worthwhile test is to examine cin.fail().  Suppose the user enters "abc" instead of a number; well, the >> operation will fail.  Then you will need to flush the cin stream until a newline character is found.  You can do that using cin's ignore() function.

---

### Post by schauerlich on 2010-12-21
Two things: "not equals" is !=, not /=. Second: every time the user enters the correct number, x will be incremented twice.

You should also work on formatting.

---

### Post by kdizil on 2010-12-22
thanks trying to improve my programming

---

### Post by kdizil on 2010-12-22
Im a newb and what exactly do you mean by formating?

---

### Post by worksofcraft on 2010-12-22
> **kdizil said:**
> Im a newb and what exactly do you mean by formating?

I think they mean your indentation...
Although C is free format language it helps readability if you indent lines depending on their block nesting in your program.

Then if you are trying to follow the logic it's easier to see where conditional blocks and functions start and end.

---

### Post by VorpalBunny on 2010-12-22
This is what worksofcraft is talking about:

```

#include <iostream>
using namespace std;

int main()
{       
    int x(8), n;

    cout << "type numbers from 8 to 23" << endl;

    for (x = 8; x <= 23; x++)
    {   
        cin >> n;

        if (x != n)
        {   
            cout << "wrong!!!" << endl;
        }
        else
        {   
            x++;
        }
    }
}

```

For some reason, it seems to take a while for people to realize this actually makes sense. When I was a TA for the CS 101 course, no one used whitespace at all. I didn't understand how people could live with something so *wrong* :P

---

### Post by Arndt on 2010-12-22
Or this style, which is called Kernighan&Ritchie (K&R) style.

```

#include <iostream>
using namespace std;

int main()
{       
    int x(8), n;

    cout << "type numbers from 8 to 23" << endl;

    for (x = 8; x <= 23; x++) {   
        cin >> n;

        if (x != n) {   
            cout << "wrong!!!" << endl;
        } else {   
            x++;
        }
    }
}

```

---

### Post by C0derBear on 2010-12-22
Nice example Bunny.

OP:

The reason for well-formatted code is the same reason that typesetters take the time to layout books and magazines and newspapers with care, if not outright obsessive disorder.

While it doesn't make any different to the computer, it makes all the difference to the human reading the code, and that is very very important.

Choosing a consistent pattern for formatting of your source, including appropriate use of whitespace and - *gasp* - comments - will go a long way to helping you write good code.

Well formatted code helps you find bugs faster, type bugs less, and present your work and ideas to others more clearly.

---

