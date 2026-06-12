---
title: "[C++] Segmentation fault (core dumped)"
date: 2016-03-29
forum: Packaging and Compiling Programs
---

### Post by battogtokh on 2016-03-29
I'm new to C++ and I need some help to check this code. It's compiled, but not run (segmentation fault). Please advice me, what should I do?
```

#include <iostream>
#include <fstream>
#include <iomanip>
#include <string>
#include <cstdlib>
#include <cmath>

using namespace std;
int main()
{
    long N = 10000;
    int C = 360;
    string INPUT1, INPUT2;

    ifstream inp1, inp2;
    ofstream out1;

    cout << "\bPlease enter file name ?\n";
    cin >> INPUT1;
    inp1.open( INPUT1.c_str() );
    if ( ! inp1 ) 
    {
        cout << "Can't open the file named file name\n";
        exit(1);
    }
    cout << "\bPlease enter file name* ?\n";
    cin >> INPUT2;
    inp2.open( INPUT2.c_str() );
    if ( ! inp2 ) 
    {
        cout << "Can't open the file named file name*\n";
        exit(1);
    }

    out1.open("diff1");

    int i=0, j=0, k=0,l=0;
    long s=N*C;
    int R=2;
    long double A[s][R], B[N][R];
    long double D;

    while(!inp2.eof() ) 
    {
        inp2>>B[i][0]>>B[i][1];
        i++;
    }

    out1<<k<<endl;
    while(!inp1.eof())
        {
            if(l > i+1)
            {
                l=0;
                k++;
                out1<<k<<endl;
            }
            inp1>>A[j][0]>>A[j][1];
            D = A[j][1]-B[k][1];
            out1<<setprecision(10)<<scientific<<D<<endl;
            j++;
            l++;
        }


    inp1.close();
    inp2.close();

    out1.close();

      return 0;

}

```

---

### Post by spjackson on 2016-03-30
> **battogtokh said:**
> I'm new to C++ and I need some help to check this code. It's compiled, but not run (segmentation fault). Please advice me, what should I do?
```

    long double A[s][R], B[N][R];
```
I am pretty sure that the segmentation fault is because these objects are too big for the stack.

---

### Post by G4143 on 2016-03-31
I'm looking at your arrays here and I can't see why they are two-dimensional.
```

long double A[s][R], B[N][R];

```
Won't it be simpler to have an array of two element structures?

Also.
All uppercase names are generally reserved for constants and not variables. INPUT1  INPUT2

I would try data structures like these.
```

#include <iostream>

const unsigned int ARR_SIZE = 3;

struct twoElems{
    int elemOne;
    int elemTwo;
};

std::ostream& operator <<(std::ostream & out, const struct twoElems & te){
    return out << te.elemOne << " " << te.elemTwo;
}

int main()
{
    struct twoElems elems[ARR_SIZE] = {{1, 2}, {3, 4}, {5, 6}};
    
    for (unsigned int i = 0; i < ARR_SIZE; i++){
        std::cout << elems[i] << std::endl;
    }
      return 0;

}

```

---

