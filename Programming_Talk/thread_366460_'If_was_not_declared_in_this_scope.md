---
title: "'If was not declared in this scope"
date: 2007-02-20
forum: Programming Talk
---

### Post by tofoo on 2007-02-20
Hello, i am new to linux and i am having some trouble making a program on emacs with ubuntu. so far, this is the following code that i have.

#include <iostream>
using namespace std;

int main()
{
  char command;
  int pin;

cout << "Please enter your pin /n";
cin >> pin;

If (ping == 12345)
{
cout << endl
<< "1-Deposit \n"
<< "2 - Withdraw \n";

cin >> command;
}
Else
return -1;
}




And i get errors saying that 'if' was not declared in this scope, as well as 'Else'. Can anyone please help me out and tell me whats wrong?

also, i had to type this code out manually in this window. the code would not let me copy and paste for some reason. anyone know why? thanks in advance.

---

### Post by Lux Perpetua on 2007-02-20
> **tofoo said:**
> Hello, i am new to linux and i am having some trouble making a program on emacs with ubuntu. so far, this is the following code that i have.

#include <iostream>
using namespace std;

int main()
{
  char command;
  int pin;

cout << "Please enter your pin /n";
cin >> pin;

If (ping == 12345)
{
cout << endl
<< "1-Deposit \n"
<< "2 - Withdraw \n";

cin >> command;
}
Else
return -1;
}




And i get errors saying that 'if' was not declared in this scope, as well as 'Else'. Can anyone please help me out and tell me whats wrong?

also, i had to type this code out manually in this window. the code would not let me copy and paste for some reason. anyone know why? thanks in advance.'if' and 'else' need to be lowercase. C++ is case-sensitive. 

Regarding cut-and-paste, it should work if you just highlight your code and then middle-click where you want it pasted. (It should work in Emacs. I do this all the time to paste code.)

---

