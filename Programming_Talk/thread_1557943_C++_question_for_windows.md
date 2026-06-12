---
title: "C++ question for windows"
date: 2010-08-21
forum: Programming Talk
---

### Post by Orbaneqtrx5 on 2010-08-21
I just started learing C++ on my own and use Ubuntu (GCC) to compile and run.  I compiled the following program using GCC and works fine, but when I tried running it on Windows using Dev++ or VC++ as soon as i input my name and press enter the prompt will exit. I don't know what is the difference from linux to windows maybe someone can help me out... Thanks beforehand :
#include <iostream>
#include <string>
using namespace std;
int main ()
{
    cout << "Please enter your name :";
string name;
cin >> name;
const string greeting = "Hello" + name + "!";
const string spaces (greeting.size(), ' ');
const string second = "* " + spaces + " *";
const string first (second.size(), '*');
cout << endl;
cout << first << endl;
cout << second << endl;
cout << "* " + greeting + " *" << endl;
cout << second << endl;
cout << first << endl;
return 0;
}

---

### Post by MadCow108 on 2010-08-21
windows prompts opened by a program close when the program running in it exits.
you can keep it open by expecting some input on the end.
```

char ch;
std::cin.get(ch);

```
it will then only exit when you press return

or I think you can also open a prompt first (run->cmd) and start the program there. That way it should stay open too (just as in linux terminal).

---

### Post by Orbaneqtrx5 on 2010-08-21
Thanks very much madcow108. By running it from the prompt and using the code supplied by yourself it worked.... thanks again

---

