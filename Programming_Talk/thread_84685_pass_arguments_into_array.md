---
title: "pass arguments into array"
date: 2005-10-31
forum: Programming Talk
---

### Post by Heretic09 on 2005-10-31
Does any one know how to change a passed argument into an array?

If the user types in foo 123456

it would get passed into an array, then the output would split up the individual numbers eg

cout << array[0] would output 1

cout << array[1] would output 2 etc

any ideas?

---

### Post by GoldBuggie on 2005-10-31
just use a char array. Let's say
char str[256];
cin>>str;
cout << str[0] .. etc

remembet that everythihng is char so if you want to use it as numbers convert it using
int x = atoi(str[0]);

You could also use the string class in c++ instead of char*.
#include <string.h>
string str;
...

---

### Post by raublekick on 2005-10-31
out of curiosity, are you writing a basic shell program?

---

### Post by thumper on 2005-10-31
how about just treating it like a std::string?

---

### Post by Heretic09 on 2005-10-31
raublekick: nah its actually a keygen i'm working on

Thanks for the quick reply. I'll try that, any ideas for groupings?

Basically i'll be passing the arguments to main via: 

int main(int argc, char *argv[])

so if the user puts in: foo 123456

cout << variable[0]; should output 12

cout << variable[1]; should output 34 etc

thanks again.

---

