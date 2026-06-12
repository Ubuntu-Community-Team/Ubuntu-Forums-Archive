---
title: "Format independent input in C"
date: 2007-10-12
forum: Programming Talk
---

### Post by osiris2258 on 2007-10-12
I am looking to read dollar values into C. Here's the code: .
```
 Program to calculate the change for any given dollar amount. it is designed to take input from a file 
 rather than the user, which is why there are no prompts. use with an input redirect or replace scanf with appropriate fscanf.*/

#include <stdio.h>

int main(){

unsigned int quarters, dimes, nickels, pennies, active, cents=0; int dollars=0; char input[13]; 
             /*break the input into dollars and cents, initial sets insure that badd input or 0 cents return zeroes*/

	while (1){ /*loop to cycle until EOF. This will always be true. without break(else at bottom of loop), is an infinte loop*/
	fgets(input,13,stdin);  /*scanf("%d.%d",&dollars,&cents); this would be the scanf version. replaced to prevent errors
                            from incorrectly formatted input*/
	sscanf(input,"%d.%d",&dollars,&cents); /*take data from input, place in dollars and cents.
                                            if input is of the form .x, will not assign new values to dollars and cents*/
	
		if (dollars>=0){ /* check for end of input*/
		active=dollars*100+cents; /* join dollar and cent information into total cents*/
		quarters=active/25;
		active=active%25; /* the modulo will give the remaining change without the quarters*/ 
		dimes=active/10;
		active=active%10;
		nickels=active/5;
		active=active%5;
		pennies=active;
		
		printf("$%d.%02d: %d %s %d %s %d %s %d %s\n",
                          dollars,cents,quarters,((quarters==1)?"quarter":"quarters"),
                          dimes,((dimes==1)?"dime":"dimes"),nickels,((nickels==1)?"nickel":"nickels"),
                          pennies,((pennies==1)?"penny":"pennies")); 
                          /* in order to be gramatical, check to see if the plural is needed. 
                          (x==y)?l:m if the statement is parenthesis is true, then replace this string with l, 
                          otherewise replace with m.*/
                          dollars=0; cents=0;}
                          /*reset values so that if there is an input error or there are no cents zeroes are printed*/
		else {
		break;} /* the end of input has beeen reached, so exit the loop*/
	} 
}

```

The problem is that if the input is .x, that is nothing before the decimal, then the sscanf never assigns values to anything in the line. I have set dollars and cents to 0 manually so it is obvious when this happens, but I need some way to have the program see .x and set dollars=0, cents=x.

---

### Post by mjwood0 on 2007-10-12
Using scanf is really risky for the reasons you've already found out.

Your best bet is to use
```
fgets()
```
and parse it using
```
strtok
```

This is much safer and will allow you to catch bad input which doesn't meet your formatting.  As a general rule, never use scanf for anything...  And gets() is really risky too.

For complete details, see [http://everything2.com/index.pl?node_id=611528]("http://everything2.com/index.pl?node_id=611528")

---

### Post by Adnarim on 2007-10-13
> **mjwood0 said:**
> Using scanf is really risky 

Just wanna say that scanf can also be correct used without being risky.
wrong:
```

#include <stdio.h>

int main (void) {
      char buff[10];
      scanf("%s",buff);
}

```
correct:
```

#include <stdio.h>

int main (void) {
      char buff[10];
      scanf("%10s",buff);
}

```

---

### Post by mjwood0 on 2007-10-13
> **Adnarim said:**
> Just wanna say that scanf can also be correct used without being risky.
correct:
```

#include <stdio.h>

int main (void) {
      char buff[10];
      scanf("%10s",buff);
}

```

While this is indeed less risky, I still find fgets cleaner.  It forces the user to select a max length -- scanf doesn't.

But you are right.  You can make it mostly safe.

---

### Post by hod139 on 2007-10-13
> **Adnarim said:**
> Just wanna say that scanf can also be correct used without being risky.
<snip>
Your example, imo, show just how risky scanf is.  Their is not type checking between the format identifier and what is being passed to it.  This isn't a problem with just scanf, but all functions that take format identifiers.  Good 'ol C doesn't bother making sure that the variables and format specifiers are matching types before using them.  To me, that makes them risky.

---

### Post by Adnarim on 2007-10-13
@hod139: Of course something like this will crash you're app:
```

#include <stdio.h>

int main (void) {
      int buff;
      scanf("%s",buff);
}

```

But fgets(buff,8,stdin); will crash it the same way. So that's something the coder has to check in every case.

---

### Post by hod139 on 2007-10-13
> **Adnarim said:**
> But fgets(buff,8,stdin); will crash it the same way. So that's something the coder has to check in every case.

 fgets(buff,8,stdin); won't compile, the buffer must be a char *.  And yes, I agree with you that the coder has to be careful.  This is why I say the string functions in C are risky.

---

### Post by Adnarim on 2007-10-13
It compiles, I tested it now but it spites a warning message. But it compiles.

---

### Post by hod139 on 2007-10-13
oops, you are correct.  In C++ (using g++) that throws an error, but in C (using gcc) that throws only a warning.  I'm glad g++ makes that warning an error, and surprised that gcc didn't.

---

### Post by slavik on 2007-10-13
you can make gcc consider warnings as errors (-Werror flag I think)

---

### Post by mjwood0 on 2007-10-13
If we're talking about ANSI C, there is really no strong typing involved.  Hence the advent of Ada for military critical applications.

---

### Post by gnusci on 2007-10-14
I did few changes to your code, it seems work well...

[PHP]
/*
 Program to calculate the change for any given dollar amount. it is designed to take input from a file
 rather than the user, which is why there are no prompts. use with an input redirect or replace scanf with appropriate fscanf.
 */

#include <stdio.h>
#include <stdlib.h>

int main(){

unsigned int quarters, dimes, nickels, pennies, active, cents=0; int dollars=0; char input[13];
             /*break the input into dollars and cents, initial sets insure that badd input or 0 cents return zeroes*/

        while (1){ /*loop to cycle until EOF. This will always be true. without break(else at bottom of loop), is an infinte loop*/
        fgets(input,13,stdin);  /*scanf("%d.%d",&dollars,&cents); this would be the scanf version. replaced to prevent errors
                            from incorrectly formatted input*/
        //
        float _money = atof(input);
        sprintf(input,"%0.2f",_money);
        printf("money: %s \n",input);
        ///
        sscanf(input,"%d.%d",&dollars,&cents); /*take data from input, place in dollars and cents.
                                            if input is of the form .x, will not assign new values to dollars and cents*/

                if (dollars>=0){ /* check for end of input*/
                active=dollars*100+cents; /* join dollar and cent information into total cents*/
                quarters=active/25;
                active=active%25; /* the modulo will give the remaining change without the quarters*/
                dimes=active/10;
                active=active%10;
                nickels=active/5;
                active=active%5;
                pennies=active;

                printf("$%d.%02d: %d %s %d %s %d %s %d %s\n",
                          dollars,cents,quarters,((quarters==1)?"quarter":"quarters"),
                          dimes,((dimes==1)?"dime":"dimes"),nickels,((nickels==1)?"nickel":"nickels"),
                          pennies,((pennies==1)?"penny":"pennies"));
                          /* in order to be gramatical, check to see if the plural is needed.
                          (x==y)?l:m if the statement is parenthesis is true, then replace this string with l,
                          otherewise replace with m.*/
                          dollars=0; cents=0;}
                          /*reset values so that if there is an input error or there are no cents zeroes are printed*/
                else {
                break;} /* the end of input has beeen reached, so exit the loop*/
        }
}

[/PHP]

---

### Post by ankursethi on 2007-10-14
Bah. Real men read input character by character using getchar().

---

### Post by mjwood0 on 2007-10-14
> **ankursethi said:**
> Bah. Real men read input character by character using getchar().

Do these same "real men" actually have paid jobs programming?  j/k

---

### Post by ankursethi on 2007-10-14
> **mjwood0 said:**
> Do these same "real men" actually have paid jobs programming?  j/k

It was intended as a sort of joke. Looks like it didn't come out funny enough. Oh well, I'm notorious for these.

Anyway, real-er men would probably write their own platform specific input routine in assembly.

---

### Post by weresheep on 2007-10-14
A few (hopefully helpful) comments...

You have an unofficial signature for your main function. it should be

```
int main(void)
```
or
```
int main(int argc, char **argv)
```

The main method has a return type of int so it should be returning an int. Typically a return value of 0 (zero) means no error and non-zero indicates an error.

fgets and ([sf])scanf have return values for a reason. If fgets returns NULL it means EOF (or error). The scanf family of functions return the number of successfully read parameters. You should use these return values.

Your character array is not initialised or wiped inbetween loops. Coupled with your lack of fgets return value checking will lead to unpredictable results when EOF.

I would suggest a main loop along the lines of 

```

#include <stdio.h>

#define MAX_BUF 13 /* Magic numbers are bad. Use a constant. */

int main(void) {
  char buf[MAX_BUF];
  char *p;

  while ((p = fgets(buf, MAX_BUF, stdin)) != NULL) {
    /* At this point p == &buf[0] so you can use s or buf in sscanf */
  }

  return 0; /* Program exited successfully. */
}

```

I also suggest installing the development man pages (apt-get install manpages-dev) after which you'll be able to get information on the various C standard library functions (e.g. man fgets). They are a great resource to have.

-weresheep :)

---

### Post by Jessehk on 2007-10-14
I was taught to read numerical input similar to this in C:
```

#include <stdio.h>
#include <stdlib.h>

#define BUFFSIZE 64

void error( const char *msg ) {
    fprintf( stderr, "%s\n", msg );
    exit( EXIT_FAILURE );
}

int readInt( const char *prompt ) {
    char buffer[BUFFSIZE];
    int result;
    
    printf( "%s", prompt );
    if ( fgets( buffer, BUFFSIZE, stdin ) == NULL )
        error( "Error reading input" );
        
    if ( sscanf( buffer, "%d", &result ) < 1 )
        error( "Invalid input" );
   
    return result;
}

int main( void ) {
    int numb = readInt( "Enter an integer: " );
    printf( "You entered %d\n", numb );
    
    return 0;
}

```

I think the **sscanf** and **fgets** functions are the recommended ones. :)

---

### Post by osiris2258 on 2007-10-16
Here is the final version of the program. I have covered almost all bases, the only thing left is that .1 and .01 are indistinguishable since integers ignore leading 0s.

Sorry about the side scrolling. Why are windows for code so small? Shouldn't they auto scale to the browser window?


[PHP]/* Program to calculate the change for any given dollar amount. it is designed to take input from a file rather than the user, which is why there are no prompts. use with an input redirect or replace scanf with appropriate fscanf.
    IMPORTANT: Cents values must be in 2 digit format. .1 will be processed the same as .01, to distinguish use .10
    Do not exceed maximum value of an int. this will prduce 2 erroneous lines of output.*/

#include <stdio.h>

int main(){

  unsigned int quarters, dimes, nickels, pennies, active, cents=0; int dollars=0; char input[13];
  /*break the input into dollars and cents, initial sets insure that blank input or 0 cents return zeroes*/

  while (1){ /*loop to cycle until EOF. This will always be true. without break(else at bottom of loop), is an infinte loop*/

    fgets(input,13,stdin);  /*scanf("%d.%d",&dollars,&cents); this would be the scanf version. replaced to prevent errors from incorrectly formatted input*/

    if((sscanf(input,"%d.%u",&dollars,&cents))==0) /*take data from input, place in dollars and cents. will read nothing if dollars is blank, nothing into cents if cents are blank.*/
    sscanf(input,".%u",&cents); /*reads into cents only if dollars is blank. leading zeros and implied zeros are ignored. Cents must be in format .xx*/

    if (dollars>=0){ /* check for end of input*/

      active=dollars*100+cents; /* join dollar and cent information into total cents*/
      quarters=active/25;
      active=active%25; /* the modulo will give the remaining change without the quarters*/
      dimes=active/10;
      active=active%10;
      nickels=active/5;
      active=active%5;
      pennies=active;

      printf("$%d.%02d: %d %s %d %s %d %s %d %s\n",
             dollars,cents,quarters,((quarters==1)?"quarter":"quarters"),       dimes,((dimes==1)?"dime":"dimes"),
nickels,((nickels==1)?"nickel":"nickels"),
             pennies,((pennies==1)?"penny":"pennies"));

      /* in order to be gramatical, check to see if the plural is needed.                                (x==y)?l:m if the statement is parenthesis is true, then replace this string with l, otherewise replace with m.*/

      dollars=0; cents=0;}    /*reset values so that if there are no dollars or no cents zeroes are printed*/

    else {
      break;} /* the end of input has beeen reached, so exit the loop*/
  }
return 0;}[/PHP]

---

