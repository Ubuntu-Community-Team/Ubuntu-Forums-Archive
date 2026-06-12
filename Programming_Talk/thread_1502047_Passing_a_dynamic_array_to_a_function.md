---
title: "Passing a dynamic array to a function"
date: 2010-06-05
forum: Programming Talk
---

### Post by esmeco on 2010-06-05
Hello!
I'm having some problems with dynamic arrays passed by reference.
I have an add_employee() function  which receives a pointer to a dynamic array of Employee structures.
The purpose of this function is to add employees to an array, everytime this function is callled and reallocate the size of the array to accomodate new employees.
The problem is I'm given an "Unhandled Exception" each time the function is called for the second time(to add a second employee to the array).The first time it works alright and the array is filled with the information passed on the call to gets();
Here's the Employee function:
 
  ```

int add_employee(Employee **employee,int n_employees)
{
    
    
    n_employees++;

    *employee=(Employee*) realloc(*employee,n_employees* sizeof(Employee));
    
 
    if(*employee== NULL)
    {
        fprintf(stderr, "Error alocating memory!");
        exit(1);
    }
    

    printf("Introduce employee name:\n");
    fflush(stdin);
    gets(employee[n_employees-1]->name);
    employee[n_employees-1]->id=n_employees;
    
    
    return n_employees;
}

```
 Here it is the main function:
 
  ```

void main()
{
        int n_employees=0;
    Employee *emp=NULL;

    .........
        
    emp=(Employee *)malloc(sizeof(Employee));

        if(emp==NULL)
        {
            fprintf(stderr,"Error alocating memory!"); 
            exit (1); 
        }
            

   
    do{
       ...
  
            case 2:         
                do
                {
                    ...
                    switch(opsub)
                    {
                        case 1:
                    n_employees=add_employee(&emp,n_employees);
                                                break;
                                         ...
                                        }
                                } while(opsub!=5);
                            
           }while(op!=5);

```
And the Employee structure in Employee.h:

```

typedef struct employee
{
    char name[100];
    int id;

}Employee;


int add_employee(Employee **employee,int n_employees);

```If I use this code directly in main it works alright,but in this function it doesn't.
What could I be doing wrong?

---

### Post by Milliways on 2010-06-05
You have too many levels of indirection


```

int add_employee(Employee ***employee**,int n_employees)
{
    
    
    n_employees++;

    **employee**=(Employee*) realloc(**employee**,n_employees* sizeof(Employee));
    
 
    if(employee== NULL)
    {
        fprintf(stderr, "Error alocating memory!");
        exit(1);
    }
    

    printf("Introduce employee name:\n");
    fflush(stdin);
    gets(employee[n_employees-1]**.name**);
    employee[n_employees-1]**.id=n_employees**;
    
    
    return n_employees;
}

```


```

void main()
{
    int n_employees=0;
    Employee *emp=NULL;

    .........
        

  n_employees=add_employee(**emp**,n_employees);
 
```

There are other problems

Why typedef struct employee ?
rather than typedef struct

This is confusing at least as you use employee as a variable.
There is no point making your code harder to read.

gets is not recommended.

The code is a bit clumsy, but I assume you are learning.
The above will at least make it work.

---

### Post by esmeco on 2010-06-05
That too isn't working for me...It gives an "Unhandled Exception" at line 
gets(employee[n_employees-1].name);

---

### Post by Milliways on 2010-06-05
Are you sure you included all the changes.
I have edited my post to show changes in bold.
You will also need to edit the header file to amtch.

---

### Post by Some Penguin on 2010-06-05
Why are you calling fflush on stdin?

---

### Post by esmeco on 2010-06-05
Yes,I'm calling fflush on stdin...Now,I don't know what's happening but the program is exiting after I choose the option on the menu to add a new employee...Something's wrong with the program or Visual Studio...

---

### Post by esmeco on 2010-06-05
The pointer employee is now pointing to NULL and that is causing the program to exit...And I don't know why as it was pointing somewhere just a few minutes ago...

---

### Post by Some Penguin on 2010-06-05
I didn't ask you whether, I asked *why*.  Flushing an input stream is fairly odd.

Another thing to notice is that the following code is odd because you're treating Employee as an array of pointers to employees, and not a pointer to an array of structures.


    printf("Introduce employee name:\n");
    fflush(stdin);
    gets(employee[n_employees-1]->name);
    employee[n_employees-1]->id=n_employees;

---

### Post by esmeco on 2010-06-05
I used fflush because after the printf("Introduce employee name:\n"); it doesn't let me introduce anything!How can I solve that without using fflush?

Tested it again and it consistently breaks when trying to add the 3rd employee and exits with a message on Visual studio that says: "Windows has triggered a breakpoint...This may be due to a corruption of the heap..."

Maybe it has something to do with the pointers...The strange thing is,this breakpoint only occurs because I added the code to a function...If I use the exact same code in main it works perfectly,but as I wanted to have a function to add employees I was hoping it woulr work too...

---

### Post by MadCow108 on 2010-06-05
flushing of input streams is undefined.
Don't do it.

Don't use gets. You have no means of detecting buffer overflows with gets
use fgets instead

are you sure you incorporated all of millways changes including in main?
it should work.
edit: no it won't check dwhitneys post following mine.

---

### Post by dwhitney67 on 2010-06-05
> **Milliways said:**
> Are you sure you included all the changes.
I have edited my post to show changes in bold.
You will also need to edit the header file to amtch.

Milliways, your code suggestion offered to esmeco is a bit off, and that is probably explains why esmeco is getting the seg fault.

In your code, the employee pointer is a *local* variable that points to whatever is passed into the function, and initially this is null.  After the realloc(), the employee pointer within the function is fine, however it's reference address is not returned back to the main() function because, as I stated a moment ago, it is a local variable.

To fix this, esmeco would need to pass the address of the Employee list to the function, thus assuring that he obtains the new address once the realloc() takes place.

In simpler words:
```

typedef struct Employee
{
   char name[80];
   int  id;
} Employee;


int addEmployee(**Employee**** emp, int numEmployees)
{
   ++numEmployees;

   ***emp** = realloc(***emp**, numEmployees * sizeof(Employee));

   if (*emp == 0)
   {
      perror("Failed to allocate memory ");
      return -1;
   }

   printf("Enter employee name: ");
   **fgets**((***emp**)[numEmployees - 1].name, sizeof((***emp**)[numEmployees - 1].name), stdin);

   // replace newline character, if it is present, with a null char.
   char* nl = strchr((***emp**)[numEmployees - 1].name, '\n');
   if (nl) *nl = '\0';

   (***emp**)[numEmployees - 1].id = numEmployees;

   return numEmployees;
}


int main(void)
{
   int       numEmployees = 0;
   Employee* employees = 0;

   for (int i = 0; i < 3; ++i)
   {
      numEmployees = addEmployee(**&employees**, numEmployees);
   }

   //...

   free(employees);
   numEmployees = 0;

   return 0;
}

```

---

### Post by esmeco on 2010-06-05
The code works fine except for the part that if I don't use fflush(stdin) the input is skipped...
I tried fgets with the same result!


I'm trying to understand a bit more about pointers so I'd like youu to check if I'm following through: The difference between Milliways' code and your code is that one is passed a copy of the pointer and the other is passed the address of the pointer,so the changes on the copy will only have effect while add_employee is executing and the changes in the other will persist?


Why is the **(*emp)** needed in the code below?What does it do in terms of access?

```

(***emp**)[numEmployees - 1].id= numEmployees;

```I was wondering, is that function the best way to add an employee to a structure or having instead the same function like this:

```

Employee addEmployee(int numEmployees)
{

   Employee emp;

   printf("Enter employee name: ");
   **fgets**(**emp**.name, sizeof(**emp**.name), stdin);

   **emp**.id = numEmployees;

   return emp;
}


```And main like this:

```

int main(void)
{
   int       numEmployees = 0;
   Employee* employees = 0;

   for (int i = 0; i < 3; ++i)
   {
      numEmployees++;
      **emp**loyees = realloc(**employees**, numEmployees * sizeof(Employee));
      employees[i] = addEmployee(numEmployees);
   }

   //...

   free(employees);
   numEmployees = 0;

   return 0;
}

```

---

### Post by Some Penguin on 2010-06-05
I don't think 'best' could possibly be used to describe any algorithm which reallocs the same for every single insert.

And you need to read up on pointers, if you don't understand the difference between a pointer to an array versus an array of pointers.  Think about how data is stored in memory.

---

### Post by dwhitney67 on 2010-06-05
> **esmeco said:**
> 
I tried fgets with the same result!

What result was that?  Run your code through a debugger to examine the contents of the "name" array to see what is in it after typing your entry.  I believe you stated that you are running under Windows; I'm not sure what they place at the end of the buffer (is it a newline or newline/carriage return combo?).

> **esmeco said:**
> 
I'm trying to understand a bit more about pointers so I'd like youu to check if I'm following through: The difference between Milliways' code and your code is that one is passed a copy of the pointer and the other is passed the address of the pointer,so the changes on the copy will only have effect while add_employee is executing and the changes in the other will persist?

Yes, you are correct.

> **esmeco said:**
> 
Why is the **(*emp)** needed in the code below?What does it do in terms of access?

```

(***emp**)[numEmployees - 1].id= numEmployees;

```

The asterisk (star) dereferences the pointer so that we can have access to the location where the pointer is pointing to; without the dereference, you would access the address of the pointer itself, which is not where the data is located at.  In other words, the "emp" is pointing to a location that contains the address of where the data is located at.

> **esmeco said:**
> 
I was wondering, is that function the best way to add an employee to a structure or having instead the same function like this:

```

Employee addEmployee(int numEmployees)
{

   Employee emp;

   printf("Enter employee name: ");
   **fgets**(**emp**.name, sizeof(**emp**.name), stdin);

   **emp**.id = numEmployees;

   return emp;
}

```

For the simple structure you have, I cannot think of any reason why the code above would be considered bad, but nevertheless a copy is being made for the return value and this takes up CPU time.  For large or perhaps complex structures, this approach may not be suitable.

> **esmeco said:**
> 
And main like this:
```

int main(void)
{
   int       numEmployees = 0;
   Employee* employees = 0;

   for (int i = 0; i < 3; ++i)
   {
      numEmployees++;
      **emp**loyees = realloc(**employees**, numEmployees * sizeof(Employee));
      employees[i] = addEmployee(numEmployees);
   }

   //...

   free(employees);
   numEmployees = 0;

   return 0;
}

```
The code above, I do not care for; keep the main() function "clean" of tasks.  For a small project, what you have above is not a big deal, but the practical approach is to place operations that are called repeatedly within a separate function.

Personally, since it seem you are doing C programming, what I would do is define you interface functions (ie. add_employee(), print_employee_roster(), etc) in a header file that the main module can include.  Within the implementation module for the employee stuff, I would declare the employees object as a global, yet static, variable.  Then the functions can use it as needed.  The main module should _never_ have direct access to the employees object.


Employee.h:
```

#ifndef EMPLOYEE_H
#define EMPLOYEE_H

void add_employee();
int  num_employees();
void print_employee_roster();

// etc

#endif

```

Employee.c:
```

#include "Employee.h"

typedef struct Employee
{
   char name[80];
   int  id;
} Employee;

static Employee* employees = 0;
static int       num_of_employees = 0;

void add_employee()
{
   //...
}

int num_employees()
{
   return num_of_employees;
}

void print_employee_roster()
{
   //...
}

```

Main.c:
```

#include "Employee.h"

int main(void)
{
   enum Action { ADD, REMOVE, PRINT, NUM, ETC, QUIT };

   Action action = QUIT;

   do
   {
      // Display a menu prompting the user which action they wish to perform.
      // (I'll leave this as an exercise).
      //...

      switch (action)
      {
         case ADD:   add_employee(); break;
         case PRINT: print_employee_roster(); break;

         //...
      }
   } while (action != QUIT);

   return 0;
}

```

---

### Post by esmeco on 2010-06-05
The problem is it skips typing my entry if I don't use fflush(stdin). I'm using Windows.

---

### Post by esmeco on 2010-06-05
Based on the link [http://c-faq.com/stdio/gets_flush2.html](http://c-faq.com/stdio/gets_flush2.html) I've discovered what the problem is.

Since I have some calls to scanf to read input it reads also the '\n' character when I press enter to send the input,which in turn,when gets is called,since it reads a new line,skips whatever I wanted to type.

---

### Post by nvteighen on 2010-06-05
> **esmeco said:**
> Based on the link [http://c-faq.com/stdio/gets_flush2.html](http://c-faq.com/stdio/gets_flush2.html) I've discovered what the problem is.

Since I have some calls to scanf to read input it reads also the '\n' character when I press enter to send the input,which in turn,when gets is called,since it reads a new line,skips whatever I wanted to type.

Behaivor of fflush(stdin) is undefined. It usually "works", i.e. it erases the contents still available at stdin that you haven't read because you haven't read the whole line up to the '\n'. But, the correct way to do it is actually using a "trash bin" variable, like this:

```

#include <stdio.h>

int main(void)
{
    char name[10];
    char surname[10];
    char trash[256]; /* Just to "flush" stdin. 256 seems a reasonable value. */

    printf("Enter your name:");
    fgets(name, sizeof(name), stdin);

    /* "flushing". Commenting the line below will make the code behaive
     * incorrectly when more than 10 characters are typed in. */
    fgets(trash, sizeof(trash), stdin);

    printf("Enter surname:");
    fgets(surname, sizeof(surname), stdin);
    /* "Flushing" not needed as we're exiting anyway. */

    return 0;
}

```

Of course, that code is just a quick unstructured example... I could/should have written a function that automatically "flushes" stuff when asking for input. Or maybe even created one single function that handles prompting for an input with "flushing" support :p

---

### Post by soltanis on 2010-06-05
Why would you flush the input? Obviously if the user is typing names beyond the bounds of your variables, you need to consider making those variables bigger, or alternatively yelling at the user if they decide to type more.

"flushing" i.e. obliterating data from the input stream is only going to break the program when you try to interact with it using pipes, i.e.

```

program1 | program2
# or,
program2 < answers-in-a-file

```

---

