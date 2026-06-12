---
title: "&quot;conflicting types&quot;"
date: 2013-12-18
forum: Programming Talk
---

### Post by wingnut2626 on 2013-12-18
Here is my code in C:


```
#include <stdio.h>


int intA[] = {1,2,3,4,5,6,7,8,9,1,2,3,4,5,6,7,8,9};
int intB[20];


int *ptrA;
int *ptrB;
_ptrA = intA_;
_ptrB = intB_;


int *source;
int *destination;




int nbr, counter;


void intCopy(int const *source, int *destination);


int main(){


    void intCopy(int const *source, int *destination){


        printf("How many to copy?>");
        scanf("%d",&counter);


        for(nbr = counter; nbr != 0; nbr--){


            *destination++ = *source++;


        }


    intCopy(*ptrA,*ptrB);








    }












    return 0;


}


```

When I attempt to compile i am getting a 'conflicting types for ptrA' and the same message for ptrB....What am I doing wrong?

---

### Post by papibe on 2013-12-18
Hi wingnut2626.
```
ptrA = intA;
ptrB = intB;
```
Those are assignments (and expressions too). They should be inside a function.

For instance:
```

...
int
main()
{
    ptrA = intA;
    ptrB = intB;

    ...
}
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by wingnut2626 on 2013-12-18
Is there a reason that they need to  be inside of the function, or is that "just the way it is"?

---

### Post by wingnut2626 on 2013-12-18
```
#include <stdio.h>


int intA[] = {1,2,3,4,5,6,7,8,9,1,2,3,4,5,6,7,8,9};
int intB[20];


int *ptrA;
int *ptrB;


int nbr, counter;


void intCopy(int const *source, int *destination);


int main(){
    ptrA = intA;
    ptrB = intB;


    void intCopy(int const *source, int *destination){


        printf("How many to copy?>");
        scanf("%d",&counter);


        for(nbr = counter; nbr != 0; nbr--){


            *destination++ = *source++;


        }


        puts(intB);
        getchar();








    }


    intCopy(ptrA,ptrB);








    return 0;


}
```

Thats what i have now, compilation is successful.  However when I run the program, the question "How many..." is asked, and regardless of what the input is, there are no digits displayed.....what am I doing wrong now?

---

### Post by papibe on 2013-12-18
puts() takes an string of characters as an argument.

In order to print an array of ints, you need another approach. Another loop for instance.

Hope it helps.
Regards.

---

### Post by trent.josephsen on 2013-12-18
> **wingnut2626 said:**
> Is there a reason that they need to  be inside of the function, or is that "just the way it is"?

Inside a function, "ptrA = intA" is an assignment statement, i.e. code that is run when the function is called.

Code (i.e. "runnable stuff") can't appear outside a function. You can't do printf("hello, world\n") without putting it in a function. Even if it was syntactically legal, it wouldn't mean anything because control can never reach it. The only things that can appear outside of any function (barring preprocessor hijinks) are declarations or definitions of functions, file-scope ("global") variables and data types.

So outside of a function, "ptrA = intA" can't be an assignment statement. What is it, then? It turns out that C didn't always require you to declare the type of a variable, and would assume "int" if you didn't provide a type. If you've ever seen code that looks like this:
```
main()
{
    printf("This is old code, don't do this\n");
}
```
main() doesn't have an explicit type, but "implicit int" means this is still acceptable in some dialects of C. (Implicit int was removed from the language in C99, if memory serves.)

Under the implicit-int rule, "ptrA = intA;" looks like a variable definition, and it's treated as "int ptrA = intA;". Since you already declared ptrA as type 'int *', the compiler complains about ptrA being declared twice with conflicting types.

---

### Post by wingnut2626 on 2013-12-18
```
#include <stdio.h>


int intA[] = {1,2,3,4,5,6,7,8,9,1,2,3,4,5,6,7,8,9};
int intB[20];
int *ptrA;
int *ptrB;
int nbr, counter, count_number;


void intCopy(int const *source, int *destination);
void printResults(int *integer);


int main(){
    ptrA = intA;
    ptrB = intB;


    void intCopy(int const *source, int *destination){


        printf("How many to copy?>");
        scanf("%d",&counter);
        for(nbr = counter; nbr != 0; nbr--){
            *destination++ = *source++;
            }


        }
    void printResults(int *integer){
        for(count_number = counter; count_number != 0; count_number--){
            printf("%d", *integer++);
        }
      }
    intCopy(ptrA,ptrB);
    printResults(ptrB);


    return 0;
}



```

Here is my "finished" product.  Can you critique it please?  It does what its supposed to do, but i want to have it "clean".

---

### Post by Bachstelze on 2013-12-19
Who ever told you nested functions were okay?

---

### Post by wingnut2626 on 2013-12-19
if im not mistaken they are a part of GNU C aren't they?

---

### Post by Bachstelze on 2013-12-20
Maybe, but even so that doesn't make them okay. :)

---

### Post by wingnut2626 on 2013-12-20
got it

---

