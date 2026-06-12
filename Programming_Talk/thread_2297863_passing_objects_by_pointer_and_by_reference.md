---
title: "passing objects by pointer and by reference"
date: 2015-10-07
forum: Programming Talk
---

### Post by chuchi on 2015-10-07
Hi there!

Could someone explain to me what is the difference between passing objects by pointer and by reference? Let's see this example:

```


#include <iostream>

using namespace std;

class Test {
public:
    
    int var;
    Test( int v = 0) {
        var = v;
    }
};

void alterByReference(Test &t)
{
    Test t2(2);
    t = t2;//this alters the object
}

void alterByPointer(Test *t)
{
    Test t2(2);
    t = &t2;//this does not alter the object, why?
}

int main() {
    Test t1(1);
    
    alterByReference(t1);
    cout <<"By reference. val = "<< t1.var<< endl;
    
    alterByPointer(&t1);
    cout <<"By pointer. val = "<< t1.var<< endl;//t1.var is still 1, why?
    
    return 0;
}


```

The function 'alterByPointer' does not change the value of the object, but the funcion 'alterByReference' alters the value. Why??

Thanks a lot!

---

### Post by spjackson on 2015-10-07
> **chuchi said:**
> 
Could someone explain to me what is the difference between passing objects by pointer and by reference? Let's see this example:

I don't think I could be so bold as to attempt that. However, this version of alterByPointer would give you the same behaviour as alterByReference.
```

void alterByPointer(Test *t)
{
    Test t2(2);
    *t = t2;
}

```
In your original version, t = &t2 is simply pointer assignment. The local pointer t no longer points to the original object. In alterByReference (and my alternative alterByPointer) it is the class's default copy assignment operator that is called.

---

