---
title: "Newbie C problem with delete"
date: 2010-11-21
forum: Programming Talk
---

### Post by bcz on 2010-11-21
Teaching myself C++ (g++), and can't see my obvious mistake.

Code compiles fine, but dumps core when run.

Running Ubuntu 9.04, but copied code to netbook on 10.4 LTS; same problem


```
#include <iostream>
using namespace std;

class Cstatic{
public: static int cnt;
        int x,y;
        Cstatic(){cnt++;}
        ~Cstatic(){cnt--;}
};

int Cstatic::cnt=0;

int main(){
        Cstatic *a3=new Cstatic[3];
        cout<<"at.cnt:\t" <<a3->cnt <<endl;
        cout<<"at.cnt:\t" <<a3[2].cnt <<endl;
        delete a3;
        return 0;}  
```

---

### Post by worksofcraft on 2010-11-21
try this:
[php]
#include <iostream>
using namespace std;

class Cstatic{
public: static int cnt;
        int x,y;
        Cstatic(){cnt++;}
        ~Cstatic(){cnt--;}
};

int Cstatic::cnt=0;

int main(){
        Cstatic *a3=new Cstatic[3];
        cout<<"at.cnt:\t" <<a3->cnt <<endl;
        cout<<"at.cnt:\t" <<a3[2].cnt <<endl;
        delete [] a3;
        return 0;}
[/php]

---

### Post by bcz on 2010-11-22
Thanks

Simple really.  Nice if compiler flagged an error.

Getting the feeling that the cc is a better compiler than g++

Solution within an hour...   MS does not come near

Rgds BillC

---

