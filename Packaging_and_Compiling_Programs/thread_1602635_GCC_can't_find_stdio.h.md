---
title: "GCC can't find stdio.h?"
date: 2010-10-21
forum: Packaging and Compiling Programs
---

### Post by treeshaper on 2010-10-21
So, the code is  as follows:  

#include <stdio.h>
  int main(void) 
{
 prinft("This should work.\n");
 return 0; 
}
 but for some reason I get error "undefined reference to  `prinft'"  I have installed build-essential and all that crap, but for  some reason it just doesn't seem to work.

---

### Post by MadCow108 on 2010-10-21
because its printf not prinft
always compile with -Wall and you should get an "implicit declaration" warning.

if it would not find stdio.h you would get an file not round error in the first stage of creating an executable/library: the preprocessing.
undefined reference is actually an error in the last stage, the linking (which comes after compiling).
It means it can't find an implementation of the function in an library (which is obvious due to the typo)

---

