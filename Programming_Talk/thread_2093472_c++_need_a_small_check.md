---
title: "c++ need a small check"
date: 2012-12-10
forum: Programming Talk
---

### Post by Nagantman on 2012-12-10
Sorry if this is in the wrong area. I am new to c++ programming and after writing this code, g++ won't compile it. I don't understand what is wrong I have looked it over a number of times. 
```
#include <iostream>
#include <string>
using namespace std;
int main ()
{
string username;
string password;
cout << "Enter your username: " << "\n";
getline( cin, username, '\n' );
cout << "Enter your password: " << "\n";
getline( cin, password, '\n\' );
if ( username == "Christopher" && password == "Weeman" )
{
cout << "Access allowed" << "\n";
}
else
{
cout << "Bad username or password. Denied access!" << "\n";
return 0;
}
}
```

---

### Post by 1clue on 2012-12-10
You have an extra \.

getline( cin, password, '\n\' );
should be 
getline( cin, password, '\n' );

---

### Post by 1clue on 2012-12-10
```
$ g++ hello.c++ 
hello.c++:11:25: warning: missing terminating ' character
hello.c++:11: error: missing terminating ' character
hello.c++: In function ‘int main()’:
hello.c++:12: error: expected primary-expression before ‘if’
hello.c++:21: error: expected `;' before ‘}’ token

```

So basically the compiler output is telling you that on line 11, column 25, that's where the start of the problem is.  That's the first quote on the problem token.

Always take the first error, the others may be (and in this case they ARE) caused by the first.

---

### Post by Nagantman on 2012-12-10
Ah alright, thank you very much friend. Greatly appreciated.

---

### Post by 1clue on 2012-12-10
No problem.  And if I may be so bold, if that app is an example of your real-world passwords then you need to tighten that up your you WILL get owned.

Ask me how I know.

---

### Post by Nagantman on 2012-12-10
It's not an example of one of my real passwords at all.

---

### Post by Elfy on 2012-12-11
*Thread moved to **Programming Talk**.*

---

### Post by 1clue on 2012-12-11
Good.

I'm the network nazi at work, and last names as passwords really get my undies in a bunch.  :)

---

