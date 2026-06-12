---
title: "hex &amp; dec question"
date: 2011-03-12
forum: Programming Talk
---

### Post by Segaman on 2011-03-12
hey there)
```

//#include <QtCore/QCoreApplication>
#include <iostream>
#include <cstdio>

using namespace std;

int main()
{
    //QCoreApplication a(argc, argv);
    cout<<"put the data in plz \n"<<endl;
    //char s [6];
    int t [6];
    for (int k=0;k<6;++k){
    scanf("%d", &t[k]);
}
    cout<<"before: "<<dec<<t<<"\n"<<endl;
    for (int i=0;i<6;++i){
        for (int j=0;j<6-j+1;++j){
                if (t[i]>t[i+1]){
                int c = t[i+1];
                t[i+1]=t[i];
                t[i]=c;
        }
            }
        cout<<"after:  "<<dec<<t[i]<<"\n"<<endl;
    }

    return 0;
}

```

And it gives me...
```

put the data in plz

1
5
23
8
45
90
before: 0xbfe4f688

after:  1

after:  5

after:  8

after:  23

after:  45

after:  90

```

Why "before: "  reuslts in hex? in cout I wrote "dec" so why does it shows in hex..?

Another little problem is with IDE QT Creator...
I actually compile my programs manually in terminal cause in QT it seems to be compiled successful and work in "Application console" tab,but I cant work with it..I mean..for example,when I compile code written before,it shows me "put the data in plz" which I can only delete with "backspace" or "delete" key. Enabling "Show in terminal" doesnt help..Terminal is launching but there is empty...
Do you have any solution folks?

---

### Post by johnl on 2011-03-12
Because t is an **int***.  If you want to print it in decimal, cast it to an **intptr_t** (or uintptr_t), which is an integer type large enough to hold a pointer address.

```

cout << dec << static_cast<intptr_t>(t) << endl;

```

Otherwise, if you meant **t[0]** or **t[n]**, you are missing an array subscript.

---

