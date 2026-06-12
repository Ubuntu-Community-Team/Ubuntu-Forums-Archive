---
title: "C programing error check for only number"
date: 2008-06-19
forum: Programming Talk
---

### Post by Nexcompac on 2008-06-19
I have been working on a small assignment and most importantly I am very new to programing.  I am using a compiler called Miracle C to work it. (All windows jokes to follow I'm sure.)

Anyways, I can not for the life of me figure out how to prompt for error checking for a number and kick back if a letter is entered.  At the moment, it gets stuck in an eternal loop if a letter is entered.  Where am I failing?

```
#include <stdio.h>
int main(void)
{
//// Define sales tax for locations
float DELMAR = .0725;
float ENCINITAS = .0750;
float LAJOLLA = .0775;


//// Define purchase price
float PURCHASE = 0.00;
//// Define a restart point
Start:
printf("***********************************************************************\n") ;
printf("            Kudler Fine Foods Purchase Price w/tax\n");
printf("***********************************************************************\n\n") ;
printf("Please type the purchase price and then press enter.\n\n");
scanf("%f", &PURCHASE);

//// Start of if statements
	if(PURCHASE<=0.0) 
	{
		printf("Please enter a number greater than Zero\n");
		//// This will redirect the program back to the Start:
		goto Start;
	}
	 else
	{
		////if (typeof(PURCHASE) == typeof(int))
		{
			//// Display to the user the tax calculations from all three locations

			printf("***********************************************************************\n") ;
			printf("Purchase Price ----->	$%.2f\n" , (PURCHASE) ); 
			printf("Delmar's Tax   -----> +	$%.2f\n" , (DELMAR*PURCHASE) );
			printf("			=======\n") ;
			printf("Total With Tax ----->	$%.2f\n" , (DELMAR*PURCHASE)+PURCHASE );
			printf("***********************************************************************\n") ;
	
	
	
			printf("Purchase Price ----->	$%.2f\n" , (PURCHASE) ); 
			printf("Encinita's Tax -----> +	$%.2f\n" , (ENCINITAS*PURCHASE) );
			printf("			=======\n") ;
			printf("Total With Tax ----->	$%.2f\n" , (ENCINITAS*PURCHASE)+PURCHASE );
			printf("***********************************************************************\n") ;
	

	
			printf("\n") ;
			printf("Purchase Price ----->	$%.2f\n" , (PURCHASE) ); 
			printf("Lajolla's Tax  -----> +	$%.2f\n" , (LAJOLLA*PURCHASE) );
			printf("			=======\n") ;
			printf("Total With Tax ----->	$%.2f\n" , (LAJOLLA*PURCHASE)+PURCHASE );
			printf("***********************************************************************\n\n\n") ;
		}
	}

		printf("Press any key to quit") ;
		

getchar();
return 0 ;
}

```

---

### Post by LaRoza on 2008-06-19
A few thing stand out. First, scanf. That shouldn't be used, IMO. Getting input as a string then processing it is safer 

[https://www.securecoding.cert.org/confluence/display/seccode/09.+Input+Output+(FIO)](https://www.securecoding.cert.org/confluence/display/seccode/09.+Input+Output+(FIO))

Second is the way your are looping. A while loop is much more safe and recommended (and prone to less bugs). While reading your code, I couldn't follow the logic of it, because I automatically looked for a structured loop. 

As for using Miracle C (A DOS compiler, any particular reason?), your platform doesn't matter when coding standard C, just make sure it is standard.

You might want to get this: [http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable)

It can run anywhere (flash drive, or just on the desktop) and is probably more standards compliant than Miracle C. (It uses gcc)

---

### Post by Keith Hedger on 2008-06-19
Install these packages from synaptic:
c-cpp-reference and c++-annotations
They are both useful online ref works,and u probably want to use isdigit which checks if a char is a number (0-9)

---

### Post by LaRoza on 2008-06-19
> **Keith Hedger said:**
> Install these packages from synaptic:
c-cpp-reference and c++-annotations
They are both useful online ref works,and u probably want to use isdigit which checks if a char is a number (0-9)

The problem here is with scanf, which ignores input that doesn't fit the format string and waits and does weird things to the buffer.

isdigit() won't work with scanf, but it would with a safer way of getting input.

---

### Post by Nexcompac on 2008-06-19
LaRosa,
Thanks for the advice.  I will have to look at that program.  BTW, i tried the first link on the string you mentioned.  It doesn't point to anything particular.  It does have a redirect, but I am not sure if you were pointing out something particular.
As for why Miricle C?  The class I am working with offered it, so....  Free was free and I didn't know any better.
AKA, I sucomed to the man.... :guitar:

---

### Post by LaRoza on 2008-06-19
> **Nexcompac said:**
> LaRosa,
Thanks for the advice.  I will have to look at that program.  BTW, i tried the first link on the string you mentioned.  It doesn't point to anything particular.  It does have a redirect, but I am not sure if you were pointing out something particular.
As for why Miricle C?  The class I am working with offered it, so....  Free was free and I didn't know any better.
AKA, I sucomed to the man.... :guitar:

This forum parse links automatically, and when there is a ')' at the end, it truncates it. Fixed above. Miracle C isn't free that last time I looked (speech), the one I linked to is.

[https://www.securecoding.cert.org/confluence/display/seccode/09.+Input+Output+(FIO)](https://www.securecoding.cert.org/confluence/display/seccode/09.+Input+Output+(FIO))

---

