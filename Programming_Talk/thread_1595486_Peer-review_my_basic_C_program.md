---
title: "Peer-review my basic C program"
date: 2010-10-13
forum: Programming Talk
---

### Post by smdawson on 2010-10-13
Hello all. I am almost done with this but I am getting a few errors with my pointers. This is my first time using pointers so I am still solidifying the concepts. Anyways, any help or suggestions (related to the errors or not) would be great. Thanks in advance.

```
//Shawn M. Dawson
//
//Program 4; COT3011
//
//October 18, 2010
//
//This program is a revision of program3 with most sections of code put into functions.
//The program is only required to handle 4 basic errors.(1)Nonexistatnt account ID when 
//performing operations, (2)Duplicate account ID when adding accounts, (3)Over-withdrawing
//from an account, and (4)Trying to make more than the maximum, 10 accounts.

#include <stdio.h>
#define ACCOUNTS "Accounts"
#define NUMBER "Number"
#define ID "ID"
#define BALANCE "Balance"
#define SIZE 10


//Prototype the functions used.
//
void displayMenu();
int userInput();
int findIndex();
void printError();
void showAccounts();
void showTotal();
void addAccount();
void makeDeposit();
void makeWithdraw();

//The main prints the menu, allows the user to choose an operation,
//and then repeat any operations until they exit the program.
//
int main(void)
{
  int menu_choice = 0;
  int position = 0;
  int id[10], balance[10];
   
  while (!(menu_choice == -1))
 {
  displayMenu();
  menu_choice = userInput();

  switch (menu_choice)
  {
    case 1:
    {
      addAccount(&id, &balance, &position);
    } break;
    case 2:
    {
      makeDeposit(id, &balance, position);
    } break;
    case 3:
    {
      makeWithdraw(id, &balance, position);
    } break;
    case 4:
    {
      showAccounts(id, balance, position);
    } break;
    case 5:
    {
      showTotal(balance, position);
    } break;
    case 6:
      menu_choice = -1;
    default: break;
  }
 }
  return 0;
}

//This function displays the menu.
//
void displayMenu(void)
{     
  printf("\n\n              Menu             \n");
  printf("--------------------------------\n");
  printf("1. Add an account\n");
  printf("2. Make a deposit\n");
  printf("3. Make a withdraw\n");
  printf("4. Display all accounts\n");
  printf("5. Display total of all accounts\n");
  printf("6. Quit menu\n");
  printf("\nChoose an option: ");
}

//This function reads a double and returns a int because all dollar  
//amounts are supposed to be rounded to the nearest dollar.
//
int userInput(void)
{
  double choice = 0;
  scanf("%lf", &choice);
  return (int)choice;
}

//This function checks the index array for a duplicate number (ID). 
//If there is a duplicate in the array the duplicate is returned. If there is no
//duplicate then -1 is returned.
//
int findIndex(int num_check, int index[])
{
  int duped = -1;
  int i = 0;
  while (i < SIZE && duped == -1)
  {
   duped = (index[i] == num_check) ? index[i] : -1;
   i++;
  } 
  return duped;
}

//This function prints the error message that is associated
//with the number thrown by the error.
//
void printError(int err_num)
{
  switch (err_num)
  {
    case 1: printf("Error! Account ID does not exist"); break;
    case 2: printf("Error! Can not duplicate account ID"); break;
    case 3: printf("Error! Can not over-withdraw from account"); break;
    case 4: printf("Error! Maximum number of accounts is 10"); break;
  }
}

//This function prints all of the account IDs and balances 
//currently contained in their respective arrays.
//
void showAccounts(int id[], int balance[], int position)
{ 
  int i = 0;
  int a = 1;
  printf("\n%20s\n", ACCOUNTS);
  printf("--------------------------------------------\n");
  printf("%10s %5s %13s\n", NUMBER, ID, BALANCE);
  for(i = 0; i < position; i++)
  {
    printf("%10i %5i %13i\n", a, id[i], (int)balance[i]);
    a++;
  } 
}

//This function prints the total dollar amount of all
//of the accounts in their respective arrays.
// 
void showTotal(int balance[], int position)
{
  double total = 0.0;
  int i = 0;
  for(i = 0; i < position; i++)
  {
    total += balance[i];
  }
  printf("Total of all accounts is: %10i$\n", (int)total);
}

//This function adds a new account to the index if 
//there is no duplicate.
//
void addAccount(int *id[], int *balance[], int *position)
{
  int newid = 0, amount = 0, place = 0; 
  place = position;
  printf("Enter the account ID: ");
  newid = userInput();
  printf("Enter the starting balance: ");
  amount = userInput();
  if (findIndex(newid, id) != -1)
    printError(2);
  else
    if (place < SIZE)
    {
      *id[place] = newid;
      *balance[place] = amount;
      *position++;
    }
    else
      printError(4);
}

//This function deposits an amount of money if
//the account ID exists. Error message displays on an exception.
//      
void makeDeposit(int id[], int *balance[], int position)
{
  int oldid = 0, deposit = 0, dupe = 0;
  printf("Enter the account ID to deposit to: ");
  oldid = userInput();
  printf("Enter the amount to deposit: ");
  deposit = userInput();
  dupe = (findIndex(oldid, id) == -1) ? findIndex(oldid, id): -1; 
  if (dupe == -1)  
    printError(1);
  else 
    *balance[dupe] += deposit;
}

//This function withdraws money from the account ID if it exists
//and also if the user does not attempt to over-withdraw. Error message
//displays on an exception.
//
void makeWithdraw(int id[], int *balance[], int position[])
{
  int oldid = 0, withdraw = 0, dupe = 0;
  printf("Enter the account ID to withdraw from: ");
  oldid = userInput();
  printf("Enter the amount to withdraw: ");
  withdraw = userInput();
  dupe = (findIndex(oldid, id) == -1) ? findIndex(oldid, id): -1;
  if (dupe == -1)
    printError(1);
  else
  {
    if (balance[dupe] - withdraw < 0)
      printError(3);
    else 
      *balance[dupe] -= withdraw;
  }
}     
  
```

---

### Post by Zugzwang on 2010-10-13
Hi, 

there are some (probably minor) problems with your program. Try compiling it with the "-Wall" or "-pedantic" options using gcc - it will tell you something about your program:

```

me@my-computer:/tmp$ gcc test.c -Wall
test.c: In function &#8216;addAccount&#8217;:
test.c:168: warning: assignment makes integer from pointer without a cast
test.c:173: warning: passing argument 2 of &#8216;findIndex&#8217; from incompatible pointer type
test.c:105: note: expected &#8216;int *&#8217; but argument is of type &#8216;int **&#8217;
test.c:180: warning: value computed is not used

```

You should definitely correct at least the first three warnings by looking at the code again and analysing what could be the problem.

---

### Post by smdawson on 2010-10-13
I am in the process of fixing those errors, I am just not completely sure what those fixes are...I'm rereading information on the correct use of pointers before I attempt to tackle the problem because I don't fully understand the errors.

---

### Post by nvteighen on 2010-10-13
It looks quite good, but it has some issues:

1) The prototypes are inconsistent with the function's declared signature. For a prototype to be useful (i.e. to allow the compiler check the types of the data you pass), you have to not only specify the return value, but also the argument list.

```

/* In prototypes there's no need to name the arguments, only types */
int myGreatFunction(const char *, struct MyGreatStruct, int);

/* Blah... */

int myGreatFunction(const char *string, struct MyGreatStruct handler, int n)
{
    /* ... */
}

```

2) Avoid the **type name[]** syntax. It's misleading, as it shows a pointer as it were an array: either you use **type *name** or **type name[size]**, but the second forces you to pass an array of size known at compile-time. IMO, as you're using fixed sized arrays, maybe the second would be the most strict thing to do.

3) I'm not sure why you're using so much pointers... There's a lot of confusion with them and it leads to a segfault as soon as one tries to set up an account. To pass an array, it's enough with a simple pointer... double pointers are a very specific thing, unless you go for 2D matrices or something that has to modify the array's address... Another issue is that you make **position** arguments to be pointers, where that may be needed only in addAccount. Moreover, you don't even use them in makeWithdraw nor makeDeposit... I'd call this a bad interface design: you barely use return values, where they could be perfect for returning the new position or something to avoid using pointers as "return places".

4) There are some logic mistakes... Look carefully at my changes regarding findIndex, both implementation and usage. Basically, after solving all your pointer-related issues, what you got was a program that was unable to find any account because no matter what findIndex returned, you made duped to be -1 when using the ?: operator (remember: test ? then : else...) you were doing **dupe = (findIndex(oldid, id) == -1) ? findIndex(oldid, id) : -1;**. Think about it. Also, the place in addAccount where you incremented the "position" was actually incrementing the pointer, not the value.

5) Anyway, it's a great idea to use two "correlate" arrays to do this in a language where no hashes are available. Good job!

Ah, changed all comments to C style... but that's secondary :P
```

/* Shawn M. Dawson
 *
 * Program 4; COT3011
 *
 * October 18, 2010
 *
 * This program is a revision of program 3 with most sections of code put into
 * functions.  The program is only required to handle 4 basic errors. (1)
 * Nonexistant account ID when performing operations, (2) Duplicate account ID
 * when adding accounts, (3) Over-withdrawing from an account, and (4) Trying to
 * make more than the maximum, 10 accounts.
 */

#include <stdio.h>
#define ACCOUNTS "Accounts"
#define NUMBER "Number"
#define ID "ID"
#define BALANCE "Balance"
#define SIZE 10

/* Prototypes */
void displayMenu(void);
int userInput(void);
int findIndex(int, int *);
void printError(int);
void showAccounts(int *, int *, int);
void showTotal(int *, int);
void addAccount(int *, int *, int *);
void makeDeposit(int *, int *);
void makeWithdraw(int *, int *);

/* The main prints the menu, allows the user to choose an operation, and then
 * repeat any operations until they exit the program. */
int main(void)
{
    int menu_choice = 0;
    int position = 0;
    int id[10], balance[10];
   
    while (!(menu_choice == -1))
    {
        displayMenu();
        menu_choice = userInput();

        switch (menu_choice)
        {
        case 1:
        {
            addAccount(id, balance, &position);
        } break;
        case 2:
        {
            makeDeposit(id, balance);
        } break;
        case 3:
        {
            makeWithdraw(id, balance);
        } break;
        case 4:
        {
            showAccounts(id, balance, position);
        } break;
        case 5:
        {
            showTotal(balance, position);
        } break;
        case 6:
            menu_choice = -1;
        default: break;
        }
    }
    return 0;
}

/* This function displays the menu. */
void displayMenu(void)
{     
    printf("\n\n              Menu             \n");
    printf("--------------------------------\n");
    printf("1. Add an account\n");
    printf("2. Make a deposit\n");
    printf("3. Make a withdraw\n");
    printf("4. Display all accounts\n");
    printf("5. Display total of all accounts\n");
    printf("6. Quit menu\n");
    printf("\nChoose an option: ");
}

/* This function reads a double and returns a int because all dollar amounts are
 * supposed to be rounded to the nearest dollar. */
int userInput(void)
{
    double choice = 0;
    scanf("%lf", &choice);
    return (int)choice;
}

/* This function checks the index array for a duplicate number (ID). If there is
 * a duplicate in the array the duplicate is returned. If there is no duplicate
 * then -1 is returned. */
int findIndex(int num_check, int *index)
{
    int duped = -1;
    int i = 0;
    while (i < SIZE && duped == -1)
    {
        if(index[i] == num_check)
        {
            duped = i;
            break;
        }
        else
            i++;
    } 
    return duped;
}

/* This function prints the error message that is associated with the number
 * thrown by the error. */
void printError(int err_num)
{
    switch (err_num)
    {
    case 1: printf("Error! Account ID does not exist"); break;
    case 2: printf("Error! Can not duplicate account ID"); break;
    case 3: printf("Error! Can not over-withdraw from account"); break;
    case 4: printf("Error! Maximum number of accounts is 10"); break;
    }
}

/* This function prints all of the account IDs and balances currently contained
 * in their respective arrays. */
void showAccounts(int *id, int *balance, int position)
{ 
    int i = 0;
    int a = 1;
    printf("\n%20s\n", ACCOUNTS);
    printf("--------------------------------------------\n");
    printf("%10s %5s %13s\n", NUMBER, ID, BALANCE);
    for(i = 0; i < position; i++)
    {
        printf("%10i %5i %13i\n", a, id[i], (int)balance[i]);
        a++;
    } 
}

/* This function prints the total dollar amount of all of the accounts in their
 * respective arrays. */
void showTotal(int *balance, int position)
{
    double total = 0.0;
    int i = 0;
    for(i = 0; i < position; i++)
    {
        total += balance[i];
    }
    printf("Total of all accounts is: %10i$\n", (int)total);
}

/* This function adds a new account to the index if there is no duplicate. */
void addAccount(int *id, int *balance, int *position)
{
    int newid = 0, amount = 0, place = 0; 
    place = *position;
    printf("Enter the account ID: ");
    newid = userInput();
    printf("Enter the starting balance: ");
    amount = userInput();
    if (findIndex(newid, id) != -1)
        printError(2);
    else
        if (place < SIZE)
        {
            id[place] = newid;
            balance[place] = amount;
            (*position)++;
        }
        else
            printError(4);
}

/* This function deposits an amount of money if the account ID exists. Error
 * message displays on an exception. */      
void makeDeposit(int *id, int *balance)
{
    int oldid = 0, deposit = 0, dupe = 0;
    printf("Enter the account ID to deposit to: ");
    oldid = userInput();
    printf("Enter the amount to deposit: ");
    deposit = userInput();
    dupe = findIndex(oldid, id); 
    if (dupe == -1)  
        printError(1);
    else 
        balance[dupe] += deposit;
}

/* This function withdraws money from the account ID if it exists and also if
 * the user does not attempt to over-withdraw. Error message displays on an
 * exception. */
void makeWithdraw(int *id, int *balance)
{
    int oldid = 0, withdraw = 0, dupe = 0;
    printf("Enter the account ID to withdraw from: ");
    oldid = userInput();
    printf("Enter the amount to withdraw: ");
    withdraw = userInput();
    dupe = findIndex(oldid, id);
    if (dupe == -1)
        printError(1);
    else
    {
        if (balance[dupe] - withdraw < 0)
            printError(3);
        else 
            balance[dupe] -= withdraw;
    }
}

```

---

### Post by xnerdx on 2010-10-13
I program more in C++ than C but I can still understand what is going on with your program. As previously mentioned, your protos should also include an argument list as well as the type and name of the function.
I recommend you don't use float/double to store money, instead use an integer value representing pennies and convert it to money by taking it and doing (float)totalInPennies/100 (Therefore converting it to dollar amounts with the least amount of consistency lost.
I'm not sure exactly why you're taking in a long float version of the user input and then converting it to int, I would just take in an integer value. I would imagine that you chose long float for a specific reason, I just can't determine why.
I don't exactly understand the goal with the findIndex function but I recommend trying it more like this:
```

int findIndex(int num_check, int &index)
{
   for(int i = 0; i < SIZE; i++) //Can you use for in C?
   {
      if(index[i] == num_check)
         return 1;   //True
   }
   return 0;   //False, exited for loop before num_check was found
}

```
For your functions where you're passing balance/id and position, just pass a reference to balance[position]. I.E. int foo(int& balance) Call it with, foo(balance[position]);
The above example may not be what your after, it seems like your using position like an index... Using it to determine how many accounts already exist? I'm not exactly sure. What I do know is I wouldn't pass your arguemtns by pointer. Declare your functions with paramaters such as (int& foo) and pass them using (foo). This is called passing-by-reference, maybe you should do a little research on it. I know I was trying to pass by pointer before int foo(int *id); foo(&id); It is hard to work with, prone to failure, and just not common. I suggest you do a little research on passing by reference.

---

### Post by smdawson on 2010-10-13
@nvteighen - Thank you very much for your post! It was extremely helpful.

> **nvteighen said:**
> It looks quite good, but it has some issues:

1) The prototypes are inconsistent with the function's declared signature. For a prototype to be useful (i.e. to allow the compiler check the types of the data you pass), you have to not only specify the return value, but also the argument list.]
  
I didn't realize that the arguments also needed to be listed in the prototype, but from now on I will know the right way.

> **nvteighen said:**
> 2) Avoid the **type name[]** syntax. It's misleading, as it shows a  pointer as it were an array: either you use **type *name** or **type  name[size]**, but the second forces you to pass an array of size  known at compile-time. IMO, as you're using fixed sized arrays, maybe  the second would be the most strict thing to do.

Thanks for the pointers (pun!) on the syntax. It does seem like a good  idea to pass the array with the size since it already has a predetermined limit. 


> **nvteighen said:**
> 3) I'm not sure why you're using so much pointers... 

I am not sure either. I think I am confused about how to correctly pass pointers and use them in functions either by reference (where I need the value changed at the address) or by value (where I just need to use the value in some arbitrary way). I think returning some values in my functions, like the position in the addAccount() would be a good idea. However, I would like to understand how I can use the pointers by reference in the function to change the value at the address...

> **nvteighen said:**
> 4) There are some logic mistakes... 

I see now that my if statement in makeDeposit() and makeWithdraw() was returning -1 regardless of whether the duplicate was found or not. I'll make some adjustments there.

> **nvteighen said:**
> Ah, changed all comments to C style... but that's secondary :razz:

>_<  Oops. I'm making a mental note to use C style commenting in C programs. (duh)

---

### Post by xnerdx on 2010-10-13
When passing values by reference (int& foo) you are passing to the function the address of a variable that is declared elsewhere. When passing by reference you are able to modify a variable that is "technically" out of the initial scope of the function that is using it. Normally when you pass an argument to a function (int foo) a copy of the value passed is made. The function that the value was passed to is only allowed to operate on it's own, local, copy of the variable. Any modifications to the variable are ignored outside of the function. So if you have a function with a variable int total and you want a different function to modify it, you must pass it by reference. The following is an example (comments explaining current values):
```

//Proto
void addTwo(int&);
int addTwoReturn(int);
int main()
{
   int total = 0;   //total = 0
   addTwo(total);   //total = 2
   total = addTwoReturn(total);   //Total = 4
   return 0;
}
   
int addTwoReturn(int total)
{
   //A copy of the value of total has been made, now any modifications to the variable are local only
   total +=2;   //Total in this function has a DIFFERENT value than that of total in main()
   return total;   //We return the new version of total and set it equal to total in main()
}
void addTwo(int& total)
{
   total += 2;   //We are modifying total directly, the current value of total here is actually the current value of total in main()
}

```
I hope that code isn't confusing... I'm not 100% awake today! The moral of the story is that passing by reference allows you to directly modify variables instead of copying them.

---

### Post by smdawson on 2010-10-13
Ok, so I understand that by passing the value as int& total you are changing the value of 'total' at the address which modifies it for the whole program, not just the function containing it.

So the only kind of pointer you can have is one that points to the address? Can you not have a pointer that only points to the value?

---

### Post by VernonA on 2010-10-13
For a beginner, this is very good code, so don't worry too much if it doesn't quite work as expected. You are wise to get it peer-reviewed - it is a compulsory part of software development at the company where I work, since it is so valuable.
[LIST=1]
[*]One part of programming is to get the overall design clear before you leap into the bits and bytes. One important thing to get sorted is how you are going to store your data, so, for example, you were advised to store money in cents, so you can use an integer for it. Likewise you should read up about structures, since an obvious improvement would be to store the accounts in one array rather than two.
[*]A second part of the design is to come up with the main functions you are going to need (ie createAccount, deleteAccount, updateAccount, etc) You have done this very well. Once you got coding you soon realised you would need some helper functions like findAccount, printAllAccounts and so on. As you put these together, try to make them as useful as possible. For example, it is obvious when adding a new account that it can't have the same ID as an existing one. Therefore you could provide a boolean doesAccountAlreadyExist function. However you spotted it would be more useful to go with the findAccount route and instead of returning a boolean return the actual index of the account, or -1 if it doesn't exist. Combining a couple of the samples we arrive at:
```
// This function searches the index array for the given account ID. 
// If it finds a match it returns the element number, otherwise it
// returns -1.
int findIndex(int num_check, int idIndex[])
{
   for (int i=0; i < SIZE; i++)
   {
      if (idIndex[i] == num_check) return i;   
   }
   return -1;   // No match found
}
```
On most projects you will find that there is a header file containing some #defined error codes, so I would actually return E_NOTFOUND rather than -1. Then you don't even need the comment on the last line!

[*]As to your pointer problems, I find it useful to remember that a pointer is just a variable which contains the address of another variable rather than actual data. If you keep this in mind you will be able to untangle your problems. Note that pointers are a major cause of bugs in code, so (a) don't use them unless you have to, (b) avoid creating pointers to pointers to pointers to ... as that can cause your brain to explode. In C, function arguments are always passed by value. In other words, without pointers a function could never modify anything except its local variables (and globals, but good programs rarely use these!). However if the caller passes in the address of one of his locals, the called function can change that variable. Thus the only time you need ever use a pointer is when you need a called function to modify a local var in the caller's function.
In your program, you often need to pass an array, and an element number to a function. You want the called function to update the array (so you must pass a pointer to it). You don't want to change the element number, though, so you just want to pass its value. Thus you need:
```
   doAccountThing( int *accountInfo, int index );

```The * says that the value being passed in the first arg is the address of a variable (in this case the account array), whilst the second is an integer value. The called function cannot affect index, but it certainly can write into the array now it knows where it is! One point that may have confused you is that the C compiler knows it cannot pass an array into a function, and that you will need to pass a pointer to it. Therefore, for simplicity it will let you use the name of the array on its own as if it was a real pointer. Thus you are allowed to write (and indeed should write) "index" when you really mean "&index[0]".
[*]One final observation is that if you are going to pass the address of an array, and the element in it, why not just pass the address of the actual element. Thus instead of writing:
```
    update( &myArray[0], elementNum );
    ....
    int  update( int *anArray, int ix )
    {
        anArray[ix] = 99;  // say
    }
```
why not just write:
```
    update( &myArray[elementNum] );
    ....
    int  update( int *anElement )
    {
        *anElement = 99;  // say
    }
```
I hope this makes some of your pointer troubles clearer!
[/LIST]

---

### Post by dwhitney67 on 2010-10-13
> **smdawson said:**
>   
I didn't realize that the arguments also needed to be listed in the prototype, but from now on I will know the right way.

Parameter names are *not* required for the function prototype, but they do assist in the reading (and implied documentation) for the function.  For example, ask yourself which of the following example prototypes is clearer to comprehend?
```

void calculateInterest(double, double, int);

OR

void calculateInterest(double principle, double interestRate, int numOfMonths);

```

> **smdawson said:**
> 
>_<  Oops. I'm making a mental note to use C style commenting in C programs. (duh)

There was nothing wrong with the comment-style you chose in the OP.  I understood them, and so does the GCC compiler when you specify that the C99 (or GNU99) standard should be followed.  These options are specified as -std=c99, or -std=gnu99, respectively.

---

### Post by dwhitney67 on 2010-10-13
> **xnerdx said:**
> When passing values by reference (int& foo) you are passing...

You are delving into C++ concepts; the OP is writing code in C.  Please do not confuse the two languages.

---

### Post by xnerdx on 2010-10-13
> **smdawson said:**
> Ok, so I understand that by passing the value as int& total you are changing the value of 'total' at the address which modifies it for the whole program, not just the function containing it.

So the only kind of pointer you can have is one that points to the address? Can you not have a pointer that only points to the value?

Pointers are built to point to the address of variables only. So when you declare a variable as a pointer, you want to set it equal to an address:
```

   int foo = 1;
   int *ptr;
   ptr = &foo;

```
That is the normal way of handling pointers. To modify the value of the pointer you must "de-reference" the pointer using the * operator. Therefore, if you were to run:
```

   *ptr = 3;

```
You are "de-referencing" the pointer, which reveals the actual contents of the variable (the values), then you can assign a value to the object pointed to by ptr; in this case you set foo to 3. In C syntax, to ensure that this is correct run this:
```

   printf("Ptr = %d, Foo = %d", *ptr, foo);

```
 When passing by reference you do not have to dereference the variable within the function you passed it to and you don't have to pass the variable as &foo. Here is an example:
```

void func(int&);
int main()
{
   int foo = 3;
   printf("%d ",foo);   //Prints 3
   func(foo);   //Note that I don't put &foo
   printf("%d",foo);   //Prints 10

void func(int& var)
{
   var = 10;
}

```

Hope that helps ^.^

---

### Post by xnerdx on 2010-10-13
> **dwhitney67 said:**
> You are delving into C++ concepts; the OP is writing code in C.  Please do not confuse the two languages.

I thought pass-by-reference was a C standard? Are you allowed to pass pointers like he is doing in C? I don't know a whole lot about C... I'm pretty good with C++ though.

---

### Post by smdawson on 2010-10-13
> **VernonA said:**
> For a beginner, this is very good code...
:) Thanks! I'm just happy I'm on the right track.


@dwhitney67 & @VernonA - Thank you both for the explanations and advice, they cleared up some of the foggier areas for me. I've got my code working just fine now, but I'm still applying some of those suggestions to try and make it better. I'll post it again once I feel pretty good about it.


@xnerdx - I am a bit confused about what you are posting. The code that you posted does not compile on my C compiler..so (though it may be right) I am a little disinclined to consider it correct.

---

### Post by spjackson on 2010-10-13
> **xnerdx said:**
> I thought pass-by-reference was a C standard? Are you allowed to pass pointers like he is doing in C? I don't know a whole lot about C... I'm pretty good with C++ though.
No. C is always pass by value; even a pointer is passed by value. The following is not valid in any C standard, nor ever has been.
```

$ cat ref.c 
void foo(int & x);
$ gcc -Wall -pedantic -std=c99 -c ref.c
ref.c:2: error: expected ‘;’, ‘,’ or ‘)’ before ‘&’ token

```

---

### Post by spjackson on 2010-10-13
> **smdawson said:**
> 
@xnerdx - I am a bit confused about what you are posting. The code that you posted does not compile on my C compiler..so (though it may be right) I am a little disinclined to consider it correct.
It's C++ syntax, not C syntax.

---

### Post by worksofcraft on 2010-10-13
> **xnerdx said:**
> I thought pass-by-reference was a C standard? Are you allowed to pass pointers like he is doing in C? I don't know a whole lot about C... I'm pretty good with C++ though.

Many languages like Java and I think even ancient Fortran implicitly pass parameters by reference and they do not support the concept of pointers.

C OTOH makes you code your references **explicitly** by passing the memory address of your actual parameter (a.k.a a pointer) and then requiring you to dereference that pointer in your function.
This is roughly what the compiler generates "under the hood" for those other languages.

Thus keeping *pass by reference* out of the C syntax it gains didactic value IMO :)

---

### Post by smdawson on 2010-10-13
So the syntax that xnerdx is using is C++, not C?

---

### Post by worksofcraft on 2010-10-13
> **smdawson said:**
> So the syntax that xnerdx is using is C++, not C?

Correct.
C++ supports both pass by reference and pass by value and this can be very confusing for people who haven't got the two concepts clear.

p.s. I personally hope that the standards committees **do not** add it to new C standard as it would really confuse the issue. In fact I personally think the C language standard should be frozen and not continue to develop in a diverging path from C++, but that's just my opinion.

---

### Post by xnerdx on 2010-10-14
> **smdawson said:**
> So the syntax that xnerdx is using is C++, not C?

That's correct. I want to sincerely apologize for the discrepancy! I am not very affiliated with the C although I do know some of it. I figured the example worked because I used Visual Studios to compile it (However VC is a C++ compiler so it supported the code example I posted). Not to offend, I just don't like base-line C all too much. I prefer C++ in most cases, however, C can be a very useful tool while programming in C++ as it can sometimes accomplish tasks without as much code and/or overhead from the compiler, allowing for faster programs. But at the same time the base C language requires several hacks to do things that C++ can do, and there are still many flaws and holes in original C code. I have studied both languages so I'm affiliated with C, but I am proficient with C++ (Sorta :P). Again, sorry about that ^.^

If you ever do move on to C++ you'll see what I mean when I say that C allows for shorter code. Take the following example (These code snippets do the same thing except one is C and the other is C++):
```

int i = 4;
int t = 9;
//C++
cout << "I = " << i << " ";
cout << "T = " << t << endl;

//C Version
printf("I = %d T = %d \n", i, t);

```
Some prefer the C++ version because it is slightly easier to read whereas others prefer the C version because it's shorter and (if I'm not mistaken) faster when compiled/executed.
Anyways, I'll stop rambling! Good luck with your programming!

---

### Post by smdawson on 2010-10-14
> **xnerdx said:**
> I want to sincerely apologize for the discrepancy!

It's not a problem. I have the syntax all straightened out.

> **xnerdx said:**
> I just don't like base-line C all too much

Not that I am a super-programmer, but I happen to think C is pretty nice. I like the "closeness" to the hardware, so to speak. I understand that C++ has all sorts of neato functions and add-ons, but I don't like the code doing things for me that I don't know how to do myself. So far, I am enjoying C very much.


Here is the final draft of my code. I may have not implemented all the suggestions (for the sake of not confusing myself. However, I will use them for future projects,) and my code is working the way it is supposed to and meets all the criteria set for it. Thanks again for the peer-review everyone. I will definitely do this again next time I need some advice.

```
//Shawn M. Dawson
//
//Program 4; COT3011
//
//October 18, 2010
//
//This program is a revision of program3 (a simple money managing software that holds 10 
//accounts, allows for withdraws and deposits, displays the total of all accounts, and 
//displays all account IDs and their balances) with most sections of code put into functions.
//The program is only required to handle 5 basic errors.(1)Nonexistatnt account ID when 
//performing operations, (2)Duplicate account ID when adding accounts, (3)Over-withdrawing
//from an account, (4)Trying to make more than the maximum, 10 accounts, and (5)Attempting
//to enter a negative number as an ID, deposit, or withdraw.

#include <stdio.h>
#define ACCOUNTS "Accounts"
#define NUMBER "Number"
#define ID "ID"
#define BALANCE "Balance"
#define SIZE 10


//Prototype the functions used.
//
void displayMenu(void);
int userInput(void);
int findIndex(int num_check, int *id);
void printError(int err_num);
void showAccounts(int *id, int *balance, int position);
void showTotal(int *balance, int position);
void addAccount(int *id, int *balance, int *position);
void makeDeposit(int *id, int *balance, int position);
void makeWithdraw(int *id, int *balance, int position);

//The main prints the menu, allows the user to choose an operation,
//and then repeat any operations until they exit the program.
//
int main(void)
{
  int menu_choice = 0;
  int position = 0;
  int id[SIZE], balance[SIZE];
   
  while (!(menu_choice == -1))
 {
  displayMenu();
  menu_choice = userInput();

  switch (menu_choice)
  {
    case 1:
    {
      addAccount(id, balance, &position);
    } break;
    case 3:
    {
      makeDeposit(id, balance, position);
    } break;
    case 4:
    {
      makeWithdraw(id, balance, position);
    } break;
    case 2:
    {
      showAccounts(id, balance, position);
    } break;
    case 5:
    {
      showTotal(balance, position);
    } break;
    case 6:
      menu_choice = -1;
    default: break;
  }
 }
  return 0;
}

//This function displays the menu.
//
void displayMenu(void)
{     
  printf("\n\n              Menu             \n");
  printf("--------------------------------\n");
  printf("1. Add an account\n");
  printf("2. Display all accounts\n");
  printf("3. Make a deposit\n");
  printf("4. Make a withdraw\n");
  printf("5. Display total of all accounts\n");
  printf("6. Quit menu\n");
  printf("\nChoose an option: ");
}

//This function reads a double and returns a int because all dollar  
//amounts are supposed to be rounded to the nearest dollar.
//
int userInput(void)
{
  double choice = 0;
  scanf("%lf", &choice);
  return (int)choice;
}

//This function checks the index array for a duplicate number (ID). 
//If there is a duplicate in the array the duplicate is returned. If there is no
//duplicate then -1 is returned.
//
int findIndex(int num_check, int *id)
{
  int duped = -1;
  int i = 0;
  while (i < SIZE && duped == -1)
  {
   duped = (id[i] == num_check) ? i : -1;
   if (duped != i)
   i++;
   else;
  } 
  return duped;
}

//This function prints the error message that is associated
//with the number thrown by the error.
//
void printError(int err_num)
{
  switch (err_num)
  {
    case 1: printf("Error! Account ID does not exist"); break;
    case 2: printf("Error! Can not duplicate account ID"); break;
    case 3: printf("Error! Can not over-withdraw from account"); break;
    case 4: printf("Error! Maximum number of accounts is 10"); break;
    case 5: printf("Error! Negative values are not allowed"); break;
  }
}

//This function prints all of the account IDs and balances 
//currently contained in their respective arrays.
//
void showAccounts(int *id, int *balance, int position)
{ 
  int i = 0;
  int a = 1;
  printf("\n%20s\n", ACCOUNTS);
  printf("--------------------------------------------\n");
  printf("%10s %8s %12s\n", NUMBER, ID, BALANCE);
  for(i = 0; i < position; i++)
  {
    printf("%8i %9i %10i\n", a, id[i], (int)balance[i]);
    a++;
  } 
}

//This function prints the total dollar amount of all
//of the accounts in their respective arrays.
// 
void showTotal(int *balance, int position)
{
  double total = 0.0;
  int i = 0;
  for(i = 0; i < position; i++)
  {
    total += balance[i];
  }
  printf("Total of all accounts is: %10i$\n", (int)total);
}

//This function adds a new account to the index if 
//there is no duplicate.
//
void addAccount(int *id, int *balance, int *position)
{
  int newid = 0, amount = 0, place = 0; 
  place = *position;
  printf("Enter the account ID: ");
  newid = userInput();
  printf("Enter the starting balance: ");
  amount = userInput();
  if (findIndex(newid, id) != -1)
    printError(2);
  else if (amount < 0 || newid < 1)
    printError(5);
  else
    if (place < SIZE)
    {
      id[place] = newid;
      balance[place] = amount;
      (*position)++;
    }
    else
      printError(4);
}

//This function deposits an amount of money if
//the account ID exists. Error message displays on an exception.
//      
void makeDeposit(int *id, int *balance, int position)
{
  int oldid = 0, deposit = 0, dupe = 0;
  printf("Enter the account ID to deposit to: ");
  oldid = userInput();
  printf("Enter the amount to deposit: ");
  deposit = userInput();
  dupe = (findIndex(oldid, id) != -1) ? findIndex(oldid, id): -1; 
  if (dupe == -1)  
    printError(1);
  else if (deposit < 0)
    printError(5);
  else 
    balance[dupe] += deposit;
}

//This function withdraws money from the account ID if it exists
//and also if the user does not attempt to over-withdraw. Error message
//displays on an exception.
//
void makeWithdraw(int *id, int *balance, int position)
{
  int oldid = 0, withdraw = 0, dupe = 0;
  printf("Enter the account ID to withdraw from: ");
  oldid = userInput();
  printf("Enter the amount to withdraw: ");
  withdraw = userInput();
  dupe = (findIndex(oldid, id) != -1) ? findIndex(oldid, id): -1;
  if (dupe == -1)
    printError(1);
  else if (withdraw < 0)
    printError(5);
  else
  {
    if (balance[dupe] - withdraw < 0)
      printError(3);
    else 
      balance[dupe] -= withdraw;
  }
}     
 
```

---

