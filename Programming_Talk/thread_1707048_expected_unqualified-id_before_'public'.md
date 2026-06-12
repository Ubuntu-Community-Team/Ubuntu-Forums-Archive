---
title: "expected unqualified-id before 'public'"
date: 2011-03-14
forum: Programming Talk
---

### Post by Segaman on 2011-03-14
```

//bubble.h

#ifndef BUBBLE_H
#define BUBBLE_H

//#include <iostream>
//#include <cstdio>

public class bubble{

public:
    bubble();

}
#endif // BUBBLE_H

``````

//bubble.cpp

#include "bubble.h"
#include <iostream>
#include <cstdio>

using namespace std;

void bubble(){
cout<<"put the data in plz \n"<<endl;
int t [5];
for (int k=0;k<5;++k){
scanf("%d", &t[k]);
cout<<"before: "<<dec<<static_cast<intptr_t>(t[k])<<"\n"<<endl;
}
for (int i=0;i<5;++i){
    for (int j=0;j<5-i+2;++j){
            if (t[i]>t[i+1]){
            int c = t[i+1];
            t[i+1]=t[i];
            t[i]=c;
    }
        }
    cout<<"after:  "<<dec<<static_cast<intptr_t>(t[i])<<"\n"<<endl;
}
}
}

``````

//main.cpp

#include "bubble.h"
//#include <iostream>

int main()
{
    cout<<"hello user,I wanna play the game with ya\n 1. bubble\n ";
    int u=0;
    scanf("%d",&u);
    switch(u){
    case 1:
        bubble();
    }

    return 0;
}

```So..As you can see,I have a simple program which provides a user to insert few digits and program will sort it. In main,I`m writing program`s interface. Bubble sort is in another module...
During comilation, it makes an error named ```
expected unqualified-id before 'public'
```if I use access specifier for methods (wheter in *.cpp or *.h file)
and makes another error ```
new types may not be defined in a return type
``` if I don`t.

whats the problem?
please help...

---

### Post by Arndt on 2011-03-14
> **Segaman said:**
> ```

//bubble.h

#ifndef BUBBLE_H
#define BUBBLE_H

//#include <iostream>
//#include <cstdio>

public class bubble{

public:
    bubble();

}
#endif // BUBBLE_H

``````

//bubble.cpp

#include "bubble.h"
#include <iostream>
#include <cstdio>

using namespace std;

void bubble(){
cout<<"put the data in plz \n"<<endl;
int t [5];
for (int k=0;k<5;++k){
scanf("%d", &t[k]);
cout<<"before: "<<dec<<static_cast<intptr_t>(t[k])<<"\n"<<endl;
}
for (int i=0;i<5;++i){
    for (int j=0;j<5-i+2;++j){
            if (t[i]>t[i+1]){
            int c = t[i+1];
            t[i+1]=t[i];
            t[i]=c;
    }
        }
    cout<<"after:  "<<dec<<static_cast<intptr_t>(t[i])<<"\n"<<endl;
}
}
}

``````

//main.cpp

#include "bubble.h"
//#include <iostream>

int main()
{
    cout<<"hello user,I wanna play the game with ya\n 1. bubble\n ";
    int u=0;
    scanf("%d",&u);
    switch(u){
    case 1:
        bubble();
    }

    return 0;
}

```So..As you can see,I have a simple program which provides a user to insert few digits and program will sort it. In main,I`m writing program`s interface. Bubble sort is in another module...
During comilation, it makes an error named ```
expected unqualified-id before 'public'
```if I use access specifier for methods (wheter in *.cpp or *.h file)
and makes another error ```
new types may not be defined in a return type
``` if I don`t.

whats the problem?
please help...

Maybe the compiler gives a file name and a line number, too?

---

### Post by Segaman on 2011-03-14
yes,sorry..
```
expected unqualified-id before 'public'  bubble.h 7
```
this line gives an error in both cases

---

### Post by cgroza on 2011-03-14
Missing semicolon at the end of class declaration.
For the bubble cpp file:
Declaration definition should be like this.
```

bubble::bubble{//code here}
```aka:```


return type CLASS::METHOD(PARAMETERS){FUNCTION BODY}
```

And remove that public word before the class keyword in you .h file. It is not necessary and syntactically incorrect.

---

### Post by Segaman on 2011-03-15
fixed,but got new error
```
 undefined refference to 'bubble::bubble'  main.cpp 13 
```

intresting that my code has been successfuly compiled in WinXP

---

### Post by Arndt on 2011-03-15
> **Segaman said:**
> fixed,but got new error
```
 undefined refference to 'bubble::bubble'  main.cpp 13 
```

intresting that my code has been successfuly compiled in WinXP

I think that the original problem was the word "public" before the class definition. I don't know what it does in WinXP, but g++ doesn't like it.

Apart from that, you don't actually use the class, just the function bubble. I suppose you will start using the class later.

A note about error messages: it seems you copied it by hand, since there's a spelling error in it (I can't help it - I notice such things). It doesn't matter this time, but it's mostly a good idea to copy such messages exactly as they are, with copy/paste, so nothing important gets lost. Sometimes tiny details are important.

---

### Post by Segaman on 2011-03-15
damn...its such a strange feeling when you know how to do smth but cant make it work...

---

### Post by SledgeHammer_999 on 2011-03-15
1. In 'bubble.cpp' you don't implement your class constructor. (well you try but you're doing it totally wrong)

2. In 'main.cpp' you try to use the class constructor directly and you dont create a local instance of the class. I am refering to the usage of 'bubble()' <---- this is your constructor, you don't call it directly.

Take a look in this tutorial page to have some enlightment: [http://www.cplusplus.com/doc/tutorial/classes/](http://www.cplusplus.com/doc/tutorial/classes/)

---

### Post by Segaman on 2011-03-15
UPDATE:
```

//bubble.h

#ifndef BUBBLE_H
#define BUBBLE_H

#include <iostream>
#include <cstdio>

class sort{

public:
    void bubble();
    sort();
    ~sort();

};

#endif // BUBBLE_H

``````

//bubble.cpp

#include "bubble.h"

using namespace std;


//sort::sort();
//sort::~sort();

void bubble(){
    cout<<"put the data in plz \n"<<endl;
    int t [5]={0,0,0,0,0};
    for (int k=0;k<5;++k){
        scanf("%d", &t[k]);
        //cout<<"before: "<<dec<<static_cast<intptr_t>(t[k])<<"\n"<<endl;
        printf("%d\n",t[k]);
    }
    int i=0;
    for (int j=0;j<5-i+1;++j){
        for (i=0;i<4;++i){
            if (t[i]>t[i+1]){
                int c = t[i+1];
                t[i+1]=t[i];
                t[i]=c;
            }
        }
        for (int l=0;l<5;++l){
            printf(" \n");
            printf("%d\n",t[j]);
        }
        //cout<<"after:  "<<dec<<static_cast<intptr_t>(t[i])<<"\n"<<endl;
    }
    int o=0;
    scanf("%d",&o);
}

``````

//main.cpp

#include "bubble.h"
//#include <iostream>

using namespace std;

int main()
{
    cout<<"hello user,I wanna play the game with ya\n 1. bubble\n ";
    int u=0;
    scanf("%d",&u);
    switch(u){
    case 1:
        sort *s = new sort();
        s->bubble();
    }

    return 0;
}

```
Yet again,I`m geting these errors:
```
 undefined refference to sort::sort() in main.cpp 13
  undefined refference to sort::bubble() in main.cpp 14
  collect2:ld returned 1 exit status

```

---

### Post by Arndt on 2011-03-15
> **Segaman said:**
> UPDATE:
```

//bubble.h

#ifndef BUBBLE_H
#define BUBBLE_H

#include <iostream>
#include <cstdio>

class sort{

public:
    void bubble();
    sort();
    ~sort();

};

#endif // BUBBLE_H

``````

//bubble.cpp

#include "bubble.h"

using namespace std;


//sort::sort();
//sort::~sort();

void bubble(){
    cout<<"put the data in plz \n"<<endl;
    int t [5]={0,0,0,0,0};
    for (int k=0;k<5;++k){
        scanf("%d", &t[k]);
        //cout<<"before: "<<dec<<static_cast<intptr_t>(t[k])<<"\n"<<endl;
        printf("%d\n",t[k]);
    }
    int i=0;
    for (int j=0;j<5-i+1;++j){
        for (i=0;i<4;++i){
            if (t[i]>t[i+1]){
                int c = t[i+1];
                t[i+1]=t[i];
                t[i]=c;
            }
        }
        for (int l=0;l<5;++l){
            printf(" \n");
            printf("%d\n",t[j]);
        }
        //cout<<"after:  "<<dec<<static_cast<intptr_t>(t[i])<<"\n"<<endl;
    }
    int o=0;
    scanf("%d",&o);
}

``````

//main.cpp

#include "bubble.h"
//#include <iostream>

using namespace std;

int main()
{
    cout<<"hello user,I wanna play the game with ya\n 1. bubble\n ";
    int u=0;
    scanf("%d",&u);
    switch(u){
    case 1:
        sort *s = new sort();
        s->bubble();
    }

    return 0;
}

```
Yet again,I`m geting these errors:
```
 undefined refference to sort::sort() in main.cpp 13
  undefined refference to sort::bubble() in main.cpp 14
  collect2:ld returned 1 exit status

```

You have defined a plain function 'bubble', but not sort::bubble. How do you expect the compiler to know that you want 'bubble' to be called when you do s->bubble()?

Nor have you defined the constructor for 'sort', that is, sort::sort. You can do it inline with just {} if you don't need it to do anything.

---

### Post by Segaman on 2011-03-15
changed ```
 void bubble(){...
``` to ```
 void sort::bubble(){...
```
and its working! finally! huuge thanks for everyone!
guys last question,about IDE QT Creator.  I asked it couple of times but still have no answer..
why,its I have console application, when I press "Run" , I cannot work in IDE`s console? Enabling ```
Projects->Launch settings->show in terminal
``` just shows me empty terminal when compile...
Due to that,I`m forced to "Build" project,then open terminal and run executable file there..Its so uncomfortable..
Anyway,my project is finally working!  thaaanks! :popcorn:

---

### Post by cgroza on 2011-03-15
And also, you don't put return types in front of your constructor.
Never mind, I got confused from the first code sample.

---

