---
title: "Pausing Execution"
date: 2008-05-29
forum: Programming Talk
---

### Post by yaisiel on 2008-05-29
Hi,

How could I pause (or freeze) a console after program execution?
I was trying to use system("PAUSE") (using std namespace), but it doesn't work. 

Thanks for your help,
Yaisiel

---

### Post by WW on 2008-05-29
It's usually a good idea to state what language you are using when you ask a question like this. :)

You mention "std namespace"; are you asking about C++?

---

### Post by amingv on 2008-05-29
Can you be bothered to give more information? (Language you're using, OS you're using (pause is not available in Linux AFAIK) or what are you specifically trying to do)
I assume you're using C++, do you want to do something like:

[PHP]#include <iostream>

int main(){
    std::cout<< "Stuff is good to have...\n";
    sleep(5); //talking about this?
    std::cout<< "...although 5 seconds later you'll lose it.\n";
    std::cin.get(); //or this?
}
[/PHP]

---

