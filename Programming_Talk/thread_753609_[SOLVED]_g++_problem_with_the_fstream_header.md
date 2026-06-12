---
title: "[SOLVED] g++ problem with the fstream header"
date: 2008-04-12
forum: Programming Talk
---

### Post by NeverEndingBattle on 2008-04-12
I just started using g++ and started to write a few very simple programs to test the compiler before I got into something too complex and run into a wall. I tried to simply write to a text file, but every time I would use #include <fstream> it would give me a huge slew of errors and not compile. But I changed it to #include <fstream.h> and it compiled fine but told me to consider using #include <fstream> instead. Am I missing something?


Update: Just a little bit after posting this I made a different code, that looks like this

#include <iostream>
#include <string>

int main()
{
char input[16];
cin.getline(input, 16);
cout << input;
}

but now it is saying cout and cin are not defined, and will not work until I put the .h at the end of iostream.

---

### Post by WW on 2008-04-12
You need to use the std namespace. Try this:
[php]
#include <iostream>
#include <string>

using namespace std;

int main()
{
char input[16];
cin.getline(input, 16);
cout << input;
}
[/php]

---

### Post by NeverEndingBattle on 2008-04-12
Ah. I was using it before as law, but I stopped just recently assuming I wouldn't need it at the moment. Thanks.

---

