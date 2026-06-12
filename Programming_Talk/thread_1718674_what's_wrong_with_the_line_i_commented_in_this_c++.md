---
title: "what's wrong with the line i commented in this c++ code?"
date: 2011-03-31
forum: Programming Talk
---

### Post by btf18 on 2011-03-31
Hi, the line near the bottom that i commented. Thanks.
 
```

#include <iostream>
using namespace std;
int main()
{
int age;
cout<<"Please enter your age\n";
cin>>age;
cin.ignore();
if ( age < 100 ) {
cout<<"youre pretty young!\n"; }
else if ( age = 100 ) {
cout<<"Youre ollllld\n"; }
else ( age > 100 ) {                            //this line says it needs a ';' before the '{'
cout<<"youre really really old xP\n";
}
cin.get();
}


```

---

### Post by GeneralZod on 2011-03-31
Needs to be "else if", although just "else {" (i.e. without the "( age > 100 )") would probably be better :)

Edit:

Also, "else if ( age = 100 )" should be "else if ( age == 100 )"

---

### Post by btf18 on 2011-03-31
Thanks man, i changed it to else without the brackets, then added the extra =, and it worked proerly :-)

---

