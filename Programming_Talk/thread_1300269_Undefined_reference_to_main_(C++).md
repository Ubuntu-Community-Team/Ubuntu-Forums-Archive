---
title: "Undefined reference to main (C++)"
date: 2009-10-24
forum: Programming Talk
---

### Post by spacesearcher on 2009-10-24
I'm trying to write a program in c++ everything was going fine then Eclipse gives me the error that I have an undefined reference to main. I can't figure out why its breaking. here is the error message and my source:

Error message:
```
Severity and Description	Path	Resource	Location	Creation Time	Id
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S undefined reference to `main'		n-queenserrorchecking	line 115	1256433944392	266

```


nqueens.cpp :
```
#include <cstdlib>
#include <iostream>
#include <stack>
#include "Point.h"
#include <cmath>

using namespace std;
namespace macs262_labs{


int main()
{
	
	
	
	return 0;
}

} // end namespace

```


```

#ifndef POINT_H_
#define POINT_H_

//a point class
#include <cstdlib>

using namespace std;
namespace macs262_labs{
class Point{
    public:
       Point(void);
       Point( int xpoint, int ypoint): x(xpoint), y(ypoint) {}
       
        int getx() const { return x; }
        int gety() const { return y; }
        
        void setx( int xpoint ) { x=xpoint; }
        void sety( int ypoint ) { y=ypoint; }
        
    private:
        int x;
        int y;
};


} // end namespace
#endif /*POINT_H_*/


```


This is the first time I have had this error and I have written more complicated programs. But this one is stumping me. Anyone have any ideas?

---

### Post by dwhitney67 on 2009-10-24
Wow, there is definitely a first for everything.  Why in pray tell do you have the main() function declared/implemented in a namespace?

P.S.  A couple of pointers... 1) do not use the "using namespace" directive in a header file; 2) include your local header file(s) (eg. Point.h) before you include system header file(s).

---

### Post by kavon89 on 2009-10-24
I'd guess it's because you're defining main in a namespace, or you're trying to make two main functions. I'm not very experienced in C++ though.

---

