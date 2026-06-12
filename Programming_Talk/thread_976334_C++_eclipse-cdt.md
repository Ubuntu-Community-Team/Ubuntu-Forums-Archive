---
title: "C++| eclipse-cdt"
date: 2008-11-09
forum: Programming Talk
---

### Post by Rany Albeg on 2008-11-09
Hi,

I downloaded the package eclipse-cdt so i can write c++ on eclipse.

when im trying to run a simple project like

#include <iostream>
int main()
{
   std::cout<<"a test program.";
   return 0;
}

it says "an error occurred during "Launching""..

need some help with that.
thanks.

---

### Post by PC-XT on 2008-11-21
Does a blank main like```
int main(){}
```work? Also, do you need something in the parenthesis in main()? I have a compiler that requires 2 parameters, string array and int, and another that has optional ones. These parameters are used to pass program switches and other arguments. I've heard of some compilers that will still compile with them omitted, but will have loading errors.

---

### Post by ckomurlu on 2008-11-22
Hi,
   Could you, please, give some details such as, which eclipse version do you use? What kind of project did you created for this code? Do you use gcc? Did you try to compile this code on terminal and is it compiled?

regards

---

