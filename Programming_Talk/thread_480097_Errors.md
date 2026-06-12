---
title: "Errors??????/"
date: 2007-06-21
forum: Programming Talk
---

### Post by cessna_89702 on 2007-06-21
If I compile this using the make command I get the errors which is underneath this. Anyone know whats wrong??




```
#include<iostream>
using namespace std;

int gcf(int a, int b);

int main() {
int a = 0, b = 0;
while(1) {
   cout << ¨enter a number or press 0 to quit¨;
   cin >> a;
   if (a == 0)
   break;
 cout <<¨Enter a 2nd number¨;
  cin >> b;
  cout << ¨GCF = ¨ << gcf(a, b) << endl;
 }
return 0;
}
int gcf(int a, int b) {
 if (a % b == 0)
return b;
else
return gcf(b, a % b);
}
```




```
gcf.cpp:9: error: stray ‘\302’ in program
gcf.cpp:9: error: stray ‘\250’ in program
gcf.cpp:9: error: stray ‘\302’ in program
gcf.cpp:9: error: stray ‘\250’ in program
gcf.cpp:13: error: stray ‘\302’ in program
gcf.cpp:13: error: stray ‘\250’ in program
gcf.cpp:13:19: error: invalid suffix "nd" on integer constant
gcf.cpp:13: error: stray ‘\302’ in program
gcf.cpp:13: error: stray ‘\250’ in program
gcf.cpp:15: error: stray ‘\302’ in program
gcf.cpp:15: error: stray ‘\250’ in program
gcf.cpp:15: error: stray ‘\302’ in program
gcf.cpp:15: error: stray ‘\250’ in program
gcf.cpp: In function ‘int main()’:
gcf.cpp:9: error: ‘enter’ was not declared in this scope
gcf.cpp:9: error: expected `;' before ‘a’
gcf.cpp:13: error: ‘Enter’ was not declared in this scope
gcf.cpp:13: error: expected `;' before ‘a’
gcf.cpp:15: error: ‘GCF’ was not declared in this scope
gcf.cpp:15: error: expected primary-expression before ‘<<’ token
make: *** [gcf] Error 1

```

---

### Post by cessna_89702 on 2007-06-21
nevermind...
I think the problem was those werent quotes because I had my keyboard layout changed lol

---

