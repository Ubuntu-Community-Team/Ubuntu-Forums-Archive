---
title: "Validation in C"
date: 2008-06-25
forum: Programming Talk
---

### Post by moogle1979 on 2008-06-25
I try to validate a user response to weed out characters by repeating the loop and use only integers

I either get no validation or it validates but repeats everything and misses the if's I set up for the integers I am looking for

Here is what I have so far:

```

int main()  //starts program
{
    //Declare Variables
    float taxdelmar, taxencinitas, taxlajolla;//declaring tax variables
    float fCost, fCheck;//calculation operator
    int  iChoice;  //variable for store choice
    int  iValid, iStore, iResponse, iCont, iCon, iName; //variable for validity check
    char cRepeat, cCheck, cStore;  //variable for program repeat
    
    
    //Variable Defined
    fCost = 0;  //defined for subtotal
    fCheck = 0;  //defined for validity check
    cRepeat = '\0';  //defined for program repeat
    iValid = 2;   //defined validity for store chosen
    iResponse = 0;
    iChoice = 0;  //defined choice for store
    iStore = 2;   //defined for subtotal validity
    iCont = 1;
    iCon = 0;
    iName = 0;
    cStore = '\0';
    
    //Tax rates defined
    taxdelmar=.0725;  //tax rate for Del mar  7.25%
    taxencinitas=.0750;  //tax rate for Encinitas 7.50%
    taxlajolla=.07750;  //tax rate for La Jolla 7.75%
            
   STORES:
     
     //User Requirements
     printf("\n\tWelcome to Kudler Fine Foods\n\n\tWe hope you enjoyed your shopping experience.\n");  //Welcome message
     printf("\n\t1. Del Mar\n");
     printf("\n\t2. Encinitas\n");
     printf("\n\t3. La Jolla\n");
     printf("\n Please choose your Location (1,2, or 3): ");
     scanf ("%d", cStore);
     iChoice = isdigit(cStore);
       if(iChoice ==1)	
       {
       printf("\n Welcome Del Mar Associate.\n");
       printf(" Please enter your sub-total: $");
       scanf("\n%f", &fCost);//sale sub-total
       printf(" --------------------------------\n");
       printf(" Your total tax is $%.2f\n", fCost * .0725);//in-line calculation
       printf(" The total amount owed is $%.2f\n", fCost * (1+.0725));//in-line calculation
       goto REPEAT;
       }
       else if(iChoice ==2)	
       {
       printf("\n Welcome Encinitas associate.\n");
       printf(" Please enter your sub-total: $");
       scanf("%f", &fCost);//sale sub-total
       printf(" --------------------------------\n");
       printf(" Your total tax is $%.2f\n", fCost * .075);//in-line calculation
       printf(" The total amount owed is $%.2f\n", fCost * (1+.075));//in-line calculation
       goto REPEAT;
       }
       else if(iChoice ==3) 
       {	
       printf("\n Welcome La Jolla associate.\n");
       printf(" Please enter your sub-total: $");
       scanf("%f", &fCost);//sale sub-total
       printf(" --------------------------------\n"); 
       printf(" Your total tax is $%.2f\n", fCost * .0775);//in-line calculation
       printf(" The total amount owed is $%.2f\n", fCost * (1+.0775));//in-line calculation
       goto REPEAT;
       }  
       else
       {
       fflush(stdin);
       goto STORES;
       }
       REPEAT:
    getchar();//keeps application viewable on screen
    // end selection
    return 0;
}

```

---

### Post by dwhitney67 on 2008-06-25
I have not seen such bad code since the days where BASIC was en vogue.

What's with the goto statements?  There are other tools available to repeat code (e.g. while- or for-loops).

With modern C compilers it is possible to declare and initialize a variable in one statement.  For instance:
[PHP]int value = 0;[/PHP]

Pay attention to your scanf() function (the first one where you get cStore)... you forgot to provide the address of the variable where you want the data stored.  Also, why are you reading a digit as a character?

Anyhow, I hope you are not referencing a C programming book written 20 years ago.  Here's how I would have written the program.  If you have any questions, feel free to ask them!

To compile the code:
```
gcc -Wall -pedantic -std=c99 store.c -o store
```
[PHP]#include <stdio.h>   //for printf(), scanf()
#include <string.h>  //for strcpy()


int main()  //starts program
{
  int   storeID = 0;
  char  storeLocation[50] = {0};
  float taxRate = 0.0;
  float subTotal = 0.0;

  //Tax rates defined
  const float taxDelMar    = 0.0725;   //tax rate for Del Mar 7.25%
  const float taxEncinitas = 0.0750;   //tax rate for Encinitas 7.50%
  const float taxLaJolla   = 0.07750;  //tax rate for La Jolla 7.75%

  do
  {
    //User Requirements
    printf("\n\tWelcome to Kudler Fine Foods\n\n\t"
           "We hope you enjoyed your shopping experience.\n");  //Welcome message

    printf("\n\t1. Del Mar\n");
    printf("\n\t2. Encinitas\n");
    printf("\n\t3. La Jolla\n");
    printf("\n Please choose your Store Location (1, 2, or 3): ");

    scanf("%d", &storeID);

    switch (storeID)
    {
      case 1:
          strcpy( storeLocation, "Del Mar" );
          taxRate = taxDelMar;
          break;

      case 2:
          strcpy( storeLocation, "Encinitas" );
          taxRate = taxEncinitas;
          break;

      case 3: 
          strcpy( storeLocation, "La Jolla" );
          taxRate = taxLaJolla;
          break;

      default:
          printf( "Error... Invalid Store ID given!\n" );
          break;
    }
  } while ( taxRate == 0.0 );

  printf("\nWelcome %s associate.\n", storeLocation);
  printf("Please enter your sub-total: $");
  scanf("%f", &subTotal);  //sale sub-total

  printf("--------------------------------\n");
  printf("Subtotal............ $%.2f\n", subTotal);
  printf("Total tax........... $%.2f\n", subTotal * taxRate);
  printf("Total amount due.... $%.2f\n", subTotal * (1+taxRate));

  return 0;
}[/PHP]

---

### Post by Can+~ on 2008-06-25
"La Jolla" shouldn't be "La Joya"?

(Spanish speaker here)

---

### Post by dwhitney67 on 2008-06-25
> **Can+~ said:**
> "La Jolla" shouldn't be "La Joya"?

(Spanish speaker here)

No he and California are correct!

La Jolla = The Jewel (?)
La Jolla, California... sits just north of San Diego.  You can read all about it here:  [http://en.wikipedia.org/wiki/La_Jolla](http://en.wikipedia.org/wiki/La_Jolla)

---

### Post by moogle1979 on 2008-06-25
I only added the goto's until I got the Store number validation down then I was going to take them out and work on the total and tax area

---

### Post by moogle1979 on 2008-06-25
That is a lot cleaner of a code you wrote but it still has the validation issue that I have been trying to solve

if someone accidentally types in 3e or decides to be play like they cannot follow the instructions then you have the unending loop that I have been trying to find a way to prevent

---

### Post by Tony Flury on 2008-06-25
The issue is i think that scanf("%d",....) does something you may not expect if the value entered is not exactly the format expected - in this case scanf expects only numeric charatcers with a terminating whitespace or newline - if the user enters "3e" i think that scanf ignores it, and continues to wait for a real integer.

if you need to validate the data, then you need read it as single characters (or as a string), and make sure that the user only entered digit characters - see isdigit(char c) - and then when you know that the data the user has entered is numeric only - then convert it to a number using something like atoi()

Hope this helps.

---

### Post by moogle1979 on 2008-06-25
Thanks Tony, I had been looking into isdigit (char c) just did not know exactly how to go about it.

---

### Post by Tony Flury on 2008-06-25
i wont post the C code here - i am sure to get the syntax wrong.

what you need to do is get characters one at a time - and check it is a digit.

It does depends on what exact input you want to accept :

for instance : 
is " 3" - leading space - valid or invalid ?
is "e3" - leading non-digit - valid (value 3) or invalid ?
is "3e" - trailing non-digits - valid (value 3) or invalid ?

and there are possible some other cases you need to think about 

you need probably at least two loops though 
1st to strip off any invalid leading characters
2nd to read in valid digits until an invalid character or whitesapce is found

and then if you have a valid input - use atoi to convert the string into a number ;

---

### Post by dwhitney67 on 2008-06-25
> **Tony Flury said:**
> i wont post the C code here - i am sure to get the syntax wrong.

what you need to do is get characters one at a time - and check it is a digit.

It does depends on what exact input you want to accept :

for instance : 
is " 3" - leading space - valid or invalid ?
is "e3" - leading non-digit - valid (value 3) or invalid ?
is "3e" - trailing non-digits - valid (value 3) or invalid ?

and there are possible some other cases you need to think about 

you need probably at least two loops though 
1st to strip off any invalid leading characters
2nd to read in valid digits until an invalid character or whitesapce is found

and then if you have a valid input - use atoi to convert the string into a number ;

EDITED:  I got semi-bored and developed a function that will query and check for a valid store ID, as per the OP's requirements:
[PHP]
#include <stdio.h>
#include <string.h>

#define isdigit(c)        ((((c) - '0') >= 0) && (((c) - '0') <= 9))
#define inrange(c,l,h)    ((((c) - '0') >= (l)) && (((c) - '0') <= (h)))

int getStoreID()
{
  int storeID = 0;

  do
  {
    printf("Enter Store Number [1, 2, 3]: ");

    char str[3] = {0};
    scanf("%2s", str);

    if ( (strlen(str) > 1) ||
         (!isdigit(str[0]) || !inrange(str[0], 1, 3)) )
    {
      while (getchar() != 0xa);
      printf("Bad input... try again fool!\n");
      continue;
    }

    storeID = str[0] - '0';
    break;

  } while(1);

  return storeID;
}

int main()
{
  printf( "Store ID = %d\n", getStoreID() );
  return 0;
}
[/PHP]

---

### Post by dwhitney67 on 2008-06-25
The full code:
[PHP]#include <stdio.h>   //for printf(), scanf()
#include <string.h>  //for strcpy()


#define isdigit(c)        ((((c) - '0') >= 0) && (((c) - '0') <= 9))
#define inrange(c,l,h)    ((((c) - '0') >= (l)) && (((c) - '0') <= (h)))

int getStoreID()
{
  int storeID = 0;

  printf("\n\tWelcome to Kudler Fine Foods\n\n\t"
         "We hope you enjoyed your shopping experience.\n");  //Welcome message

  printf("\n\t1. Del Mar\n");
  printf("\n\t2. Encinitas\n");
  printf("\n\t3. La Jolla\n");

  do
  {
    printf("\nPlease choose your Store Location (1, 2, or 3): ");

    char str[3] = {0};
    scanf("%2s", str);

    if ( (strlen(str) > 1) ||
         (!isdigit(str[0]) || !inrange(str[0], 1, 3)) )
    {
      while (getchar() != 0xa);
      printf("Bad input... try again fool!\n");
      continue;
    }

    storeID = str[0] - '0';
    break;

  } while(1);

  return storeID;
}


int main()  //starts program
{
  int   storeID = 0;
  char  storeLocation[50] = {0};;
  float taxRate = 0.0;
  float subTotal = 0.0;

  //Tax rates defined
  const float taxDelMar    = 0.0725;   //tax rate for Del Mar 7.25%
  const float taxEncinitas = 0.0750;   //tax rate for Encinitas 7.50%
  const float taxLaJolla   = 0.07750;  //tax rate for La Jolla 7.75%

  do
  {
    //User Requirements
    storeID = getStoreID();

    switch (storeID)
    {
      case 1:
          strcpy(storeLocation, "Del Mar");
          taxRate = taxDelMar;
          break;

      case 2:
          strcpy(storeLocation, "Encinitas");
          taxRate = taxEncinitas;
          break;

      case 3: 
          strcpy(storeLocation, "La Jolla");
          taxRate = taxLaJolla;
          break;

      default:
          printf("Error... Invalid Store ID given!\n");
          break;
    }
  } while (taxRate == 0.0);

  printf("\nWelcome %s associate.\n", storeLocation);
  printf("Please enter your sub-total: $");
  scanf("%f", &subTotal);  //sale sub-total

  printf("--------------------------------\n");
  printf("Subtotal............ $%.2f\n", subTotal);
  printf("Total tax........... $%.2f\n", subTotal * taxRate);
  printf("Total amount due.... $%.2f\n", subTotal * (1+taxRate));

  return 0;
}[/PHP]

---

