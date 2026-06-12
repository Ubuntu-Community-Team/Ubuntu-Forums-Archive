---
title: "[C++] Newbie, something's wrong with my code"
date: 2009-03-10
forum: Programming Talk
---

### Post by dodle on 2009-03-10
[PHP]
#include <iostream>
#include <string>
using namespace std;


int main()
{
    int age;

    cout << "How old are you?";
    cin >> age;

    if (age < 100)
        cout << "You are younger than 100";
    else if (age == 100)
        cout << "You are 100";
    else (age > 100)
        cout << "You are older than 100";

    return 0;
}[/PHP]Output during compiling:```
g.cpp: In function ‘int main()’:
g.cpp:19: error: expected `;' before ‘cout’

```There is something that I am not seeing.  According to the tutorial I was reading, my code *looks* fine to me.

---

### Post by issih on 2009-03-10
I suspect your problem lies in having a condition after the else statement.

else is a catch all, no condition goes with it, try removing the "(age > 100)" and compiling again.

Hope that helps

P.S. in essence I think it is interpreting (age > 100) as the statement to run in the else block, but you supply no closing ; so the compiler gets confused

---

### Post by dodle on 2009-03-10
Lol, sorry, what a silly mistake.  Good thing I put "Newbie" in the title.  Thanks.

---

### Post by jsmidt on 2009-03-10
Change it to this:

```

#include <iostream>
#include <string>
using namespace std;


int main()
{
    int age;

    cout << "How old are you?";
    cin >> age;

    if (age < 100)
        cout << "You are younger than 100";
    else if (age == 100)
        cout << "You are 100";
    else
        cout << "You are older than 100";

    return 0;
}

```

Don't give else and 'if' clause.

---

