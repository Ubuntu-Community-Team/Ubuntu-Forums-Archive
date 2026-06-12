---
title: "Need help with c++ string array handling with function"
date: 2012-12-19
forum: Programming Talk
---

### Post by mahibd on 2012-12-19
Hello Experts,
I need a little help from you??
```

#include<iostream>
#include<string.h>
using namespace std;

string *playerName()
{
    string player[2];
    cout<<"\nWelcome to BlackJack Lite!.\n**************************\n";
    cout<<"Enter The Name of Player1 :\n ";
    getline (cin, player[0]);
    cout<<"Enter The Name of Player2 :\n ";
    getline (cin, player[1]);
    return player;
}

int main()
{
    int dealer=0, result[2]={0,0};
    string *player=playerName();
    cout <<"player 1 is: "<<player[0]<<"player2 is: "<<player[1];
    return 0;
}

Warning : address of local variable 'player' returned

```

I don't understand why this code is not working :confused:

---

### Post by jbrefort on 2012-12-21
Your strings just exist during the playerName() function execution. Their address is not anymore valid when the function returns.
You should use something like:
string *player = new string[2];

---

### Post by lisati on 2012-12-23
*Thread moved to **Programming Talk**.*

---

### Post by dwhitney67 on 2012-12-23
It's rare that one needs to allocate an STL container.

Consider the following:
```

#include <string>
#include <iostream>

using namespace std;

string getStrInput(const char* prompt)
{
    string str;

    cout << prompt << ": ";
    getline(cin, str);

    return str;
}

int main()
{
    cout << "\nWelcome to BlackJack Lite!.\n**************************\n";
    string player1 = getStrInput("Enter the name of player1");
    string player2 = getStrInput("Enter the name of player2");
    //...
}

```

P.S.  If you require an array of "something", declare an STL vector.

---

