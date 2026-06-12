---
title: "undefined reference static linker class problem"
date: 2007-08-23
forum: Programming Talk
---

### Post by monkeyking on 2007-08-23
Hi,
I guess I have a simple problem,
but I've been unable to solve it.

I't boils down to the following.

I've got a class header with static methods and static variables.
I've got a implementation of the class.

But I can't link it all together, these are the files.

header: 
```

class relateHMM{
private:
  static int a,b,c;
public:
  int ultraMain();
  static  double like_optim(double* var);
};

```
implementation
```

#include <iostream>
using namespace std;
#include "relateHMM.hh"

int relateHMM::ultraMain(){
  a=1;
  b=2;
  c=3;
}
double relateHMM::like_optim(double* var){
  cout <<a<<b<<c<<endl;
}

```
And the runfile
```

#include <iostream>
#include "relateHMM.hh"

int main(){
  static relateHMM myObject;
  myObject.ultraMain();
  myObject.like_optim(NULL);
}

```

Im creating the o file with
```

g++ relateHMM.cpp -c -g

```
I'm trying to put it all together with

```

g++ runRelate.cpp relateHMM.o -g

```

And I get

```

relateHMM.o: In function `relateHMM::ultraMain()':
/skrald/relateHMM.cpp:10: undefined reference to `relateHMM::a'
/skrald/relateHMM.cpp:11: undefined reference to `relateHMM::b'
/skrald/relateHMM.cpp:12: undefined reference to `relateHMM::c'
relateHMM.o: In function `relateHMM::like_optim(double*)':
/relateHMM.cpp:16: undefined reference to `relateHMM::c'
/relateHMM.cpp:16: undefined reference to `relateHMM::b'
/relateHMM.cpp:16: undefined reference to `relateHMM::a'
collect2: ld returned 1 exit status

```

It might seem strange that I do the var's and method static,
but it is somewhat needed since I'me extern'ing to a c function,
and that requires a static method.

thanks in advance

---

### Post by monkeyking on 2007-08-23
Ok, I resolved it myself sorry for bothering you.

I changed the implemention so it looks like

```

#include <iostream>
using namespace std;
#include "relateHMM.hh"

int relateHMM::a;
int relateHMM::b;
int relateHMM::c;

int relateHMM::ultraMain(){
  a=1;
  b=2;
  c=3;
}
double relateHMM::like_optim(double* var){
  cout <<a<<b<<c<<endl;
}


```

It works and runs, but I'm still not really quite sure what's happing,
but I guess it must be that the static vars needs a file to bind.
or something like that.

---

### Post by aquavitae on 2007-08-24
I think the problem is that you've declared a, b and c, but you haven't implemented them (which you then corrected).  Not certain about that but that's what it looks like.  As for what's happening... a, b and c are static, i.e. one shared copy of each.  When you set them in ultraMain it will change the for every instance of your class.  In fact, for the implementation you've given you could also make ultraMain static.

You say you need to make them static because you want pointers to them?  This is possible with non-static functions too as I found out recently - see [http://ubuntuforums.org/showthread.php?t=527901]("http://ubuntuforums.org/showthread.php?t=527901").  I'm not sure how a c compiler would handle this, but if you just mean you're sending them to a c style function within a c++ project it won't matter.

Does this help?

---

### Post by monkeyking on 2009-01-23
> **aquavitae said:**
> 
You say you need to make them static because you want pointers to them?  This is possible with non-static functions too as I found out recently - see [http://ubuntuforums.org/showthread.php?t=527901]("http://ubuntuforums.org/showthread.php?t=527901").  I'm not sure how a c compiler would handle this, but if you just mean you're sending them to a c style function within a c++ project it won't matter.

Does this help?

I had a similar problem again, with these function pointers.
So I just looked into this old post.
a funtion like
[PHP]int fun(double,double)[/PHP]
the type for a function pointer when fun is free is
[PHP]int (*)(double,double)[/PHP]
whereas as to a member function it would look like
[PHP]int (object::*)(double,double)[/PHP]
If the member function is static however, the type would decay to the free type.
I had no idea about this difference however, untill today.

---

