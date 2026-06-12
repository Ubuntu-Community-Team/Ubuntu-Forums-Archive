---
title: "[C] weird problems with the if statement"
date: 2008-05-28
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-05-28
I am trying to help a friend who is doing a homework. But I cannot understand why the if doesn't behave correctly. The relevant instruction from the homework translates to:
> if the user enters one of the following +,-,*,/ to indicate operation you must determine what operation the user wants

And my friend uses a simple if to just test it. My problem is when you want to check if it is +,-,*,/ do you use char or int type? I went with char so here is the problem:

```

#include <stdio.h>
#include <stdlib.h>



main()   {
char operation;
printf ("+ \n");
printf ("- \n");
printf ("* \n");
printf ("/ \n");
printf ("choose one of the above operations \n");
scanf ("%d",&operation);
if ( (operation != '+')){
               printf("the operation you chose is invalid");              
               }
```

But even if I input the plus(+) sign the if returns true. So I am stuck.

---

### Post by WW on 2008-05-28
Change the format specification in the scanf function from %d to %c.

---

### Post by imdano on 2008-05-28
edit: nvm

---

### Post by slavik on 2008-05-28
when reading in a character, give ' %c' to scanf (there is a space there, to get rid of a possible LF/CR character), not %d. Although %d should work, too.

```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv) {
  char operation;
  printf ("+ \n");
  printf ("- \n");
  printf ("* \n");
  printf ("/ \n");
  printf ("choose one of the above operations \n");
  scanf ("%c",&operation);
  if (operation != '+') {
    printf("the operation you chose is invalid");              
  }
  return 0;
}

```

---

### Post by mike_g on 2008-05-28
operation = getchar() would be a more appropriate method to get a single character input. scanf does dodgy things if you enter stuff it does not expect. You could then run it in a loop until a valid operation is entered.

---

### Post by SledgeHammer_999 on 2008-05-28
Thanks. As I am used to C++ I wasn't aware of the %c,%d stuff. Is there any link that explains them? Another quick problem is my friend then uses a switch to see which operation is chosen. this switch evaluates the **operation** variable. So for the case is this valid? ---> 
case '+':
do somethind
break;
case '-':
do...
break;
case '*':
do...
break;
case '/':
case
break

---

### Post by slavik on 2008-05-28
> **SledgeHammer_999 said:**
> Thanks. As I am used to C++ I wasn't aware of the %c,%d stuff. Is there any link that explains them? Another quick problem is my friend then uses a switch to see which operation is chosen. this switch evaluates the **operation** variable. So for the case is this valid? ---> 
case '+':
do somethind
break;
case '-':
do...
break;
case '*':
do...
break;
case '/':
case
break
yes, a switch is valid ...

---

### Post by WW on 2008-05-28
The **switch** statement works the same in both C and C++, so if you know the C++ version, you (or your friend) can use it the same way in C. [This link](http://www.cplusplus.com/doc/tutorial/control.html) gives a quick introduction and a couple of examples (scroll down to near the end).

---

### Post by SledgeHammer_999 on 2008-05-28
Ok got it. The problem was elsewhere. thank you.

---

