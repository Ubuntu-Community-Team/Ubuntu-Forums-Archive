---
title: "‘div’ and 'mod 'was not declared in this scope"
date: 2011-08-20
forum: Programming Talk
---

### Post by isaacjun16 on 2011-08-20
So I'm new in c++, in school they are teaching us this language using Borland C++ 5.02 (which is very old) I tried to apply everything they teach me in CodeBlocks 8.02 which I think is a more nicer program, the problem is when I tried to run a basic program like the follow it gives me some error with some missing libraries, I tried to google it but I had no luck, please help with this problem, thanks in advance... :D

Code

```

#include <iostream>
#include <cmath>
using namespace std;
int main ()
{
int a,b,c,d;
cout<<"First number: "<<endl;
cin>>a;
cout<<"Second number: "<<endl;
cin>>b;
c=div(a,2);
d=mod(a,2);
cout<<c;
cout<<d;
return 0;
}

```

Errors 
```

error: ‘div’ was not declared in this scope|
error: ‘mod’ was not declared in this scope|
||=== Build finished: 2 errors, 0 warnings ===|

```

---

### Post by Queue29 on 2011-08-20
div is in <cstdlib> 

I dunno about mod, I would just use the % operator.

---

### Post by isaacjun16 on 2011-08-20
Thanks, the operator % is more simple, and it works, but now when I add the lib <cstdlib> I get a different error:

```

error: cannot convert &#8216;div_t&#8217; to &#8216;int&#8217; in assignment|

```

```

#include <iostream>
#include <cmath>
#include <cstdlib>
using namespace std;
int main ()
{
    int a,b,c,d;
    cout<<"First number: "<<endl;
    cin>>a;
    cout<<"Second number: "<<endl;
    cin>>b;
    c=div(a,2);
    d=a%2;
    cout<<c<<endl;
    cout<<d;
    return 0;
}

```

---

### Post by terry_a_g on 2011-08-20
[FONT=monospace]Forget that div() nonsense and use / for integer division.

c = a/2;
d = a%2;

If you insist upon using div(), you should know that it returns a struct that contains the quotient and the remainder.  More info at [http://www.cplusplus.com/reference/clibrary/cstdlib/div/](http://www.cplusplus.com/reference/clibrary/cstdlib/div/)
[/FONT]

---

