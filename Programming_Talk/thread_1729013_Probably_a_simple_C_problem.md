---
title: "Probably a simple C problem"
date: 2011-04-14
forum: Programming Talk
---

### Post by TheStroj on 2011-04-14
Hi everyone!

I'm working with a really long array of numbers and I ran into a really weird problem that I cannot fix. So I thought you might know ;D

I'm simply trying to print the array containing numbers, 1 number at time. It is exactly 1000 characters long. Code:

```

#include <stdio.h>

int main()
{
	char numbers[1000]="7316717653133062491922511967442657474235534919493496983520312774506326239578318016984801869478851843858615607891129494954595017379583319528532088055111254069874715852386305071569329096329522744304355766896648950445244523161731856403098711121722383113622298934233803081353362766142828064444866452387493035890729629049156044077239071381051585930796086670172427121883998797908792274921901699720888093776657273330010533678812202354218097512545405947522435258490771167055601360483958644670632441572215539753697817977846174064955149290862569321978468622482839722413756570560574902614079729686524145351004748216637048440319989000889524345065854122758866688116427171479924442928230863465674813919123162824586178664583591245665294765456828489128831426076900422421902267105562632111110937054421750694165896040807198403850962455444362981230987879927244284909188845801561660979191338754992005240636899125607176060588611646710940507754100225698315520005593572972571636269561882670428252483600823257530420752963450";
	
        int i;
	
	for(i=0; i<1000; i++)
	{
	       printf("%d", numbers[i]);
	}
	
	return 0;
}

```
(I was cleaning the code in this window to make it more readable, I hope everything is still there, if not, just add it :P).


As a result I get numbers all mixed up.

Hopefully you can help :)

Thanks in advance!

---

### Post by Simian Man on 2011-04-14
You actually have 1001 characters there.  Even if you had 1000, you did not make room for the NULL terminator.

You real problem, however, is your printf code.  You are using %d which is for decimal numbers.  What you have isn't decimal numbers, though - they are characters.  Changing the %d to %c produces the output you probably expect.

---

### Post by TheStroj on 2011-04-14
> **Simian Man said:**
> You actually have 1001 characters there.  Even if you had 1000, you did not make room for the NULL terminator.

You real problem, however, is your printf code.  You are using %d which is for decimal numbers.  What you have isn't decimal numbers, though - they are characters.  Changing the %d to %c produces the output you probably expect.

I thought of everything but %c -.- 
thanks for your help man :)

---

### Post by stchman on 2011-04-14
All looks good.

Remember, when you do a %d on a character you will get its ASCII in dec.  Use %c and this will give you the output you want.

7 = 55 in ASCII
3 = 51 in ASCII

Try this out.

[PHP]
#include <stdio.h>
#include <string.h>

int main()
{
    char numbers[ 1000 ] = "7316717653133062491922511967442657474235534919493496983520312774506326239578318016984801869478851843858615607891129494954595017379583319528532088055111254069874715852386305071569329096329522744304355766896648950445244523161731856403098711121722383113622298934233803081353362766142828064444866452387493035890729629049156044077239071381051585930796086670172427121883998797908792274921901699720888093776657273330010533678812202354218097512545405947522435258490771167055601360483958644670632441572215539753697817977846174064955149290862569321978468622482839722413756570560574902614079729686524145351004748216637048440319989000889524345065854122758866688116427171479924442928230863465674813919123162824586178664583591245665294765456828489128831426076900422421902267105562632111110937054421750694165896040807198403850962455444362981230987879927244284909188845801561660979191338754992005240636899125607176060588611646710940507754100225698315520005593572972571636269561882670428252483600823257530420752963450";
    
    int i;
    
    printf( "%d\n\n", strlen( numbers ) );
    
    
    for( i = 0; i < 1000; i++)
    {
        printf( "%d", numbers[ i ] );
    }
    
    printf( "\n\n" );
    
    for( i = 0; i < 1000; i++ )
    {
        printf( "%c", numbers[ i ] );
    }
    
    return 0;
}
[/PHP]Your character array is exactly 1000 characters.

---

### Post by r-senior on 2011-04-14
Is it also worth adding that you don't need to specify the array dimensions when initializing from a constant? For example:

```

char numbers[] = "1234567890";

```

Then, of course, your loop becomes:

```

for (i = 0; i < strlen(numbers); i++) {
...
}

```

Which all makes the code more maintainable because you don't have to change multiple occurrences of 1000 if you change the length of the string. I know it's only an example but good habits are good habits.

(For clarity, I've ignored the fact that strlen is called many times).

---

### Post by stchman on 2011-04-14
> **Simian Man said:**
> You actually have 1001 characters there.  Even if you had 1000, you did not make room for the NULL terminator.

You real problem, however, is your printf code.  You are using %d which is for decimal numbers.  What you have isn't decimal numbers, though - they are characters.  Changing the %d to %c produces the output you probably expect.

When you initialize a character array like that the compiler puts a null terminator on the end of the array for you.  This would indeed make the array 1001 characters long.

He initialized it wrong and should have used the method r-senior suggested, otherwise the compiler will not put a null terminator.

The correct code would be:

[PHP]
#include <stdio.h>
#include <string.h>

int main()
{
    char numbers[] = "7316717653133062491922511967442657474235534919493496983520312774506326239578318016984801869478851843858615607891129494954595017379583319528532088055111254069874715852386305071569329096329522744304355766896648950445244523161731856403098711121722383113622298934233803081353362766142828064444866452387493035890729629049156044077239071381051585930796086670172427121883998797908792274921901699720888093776657273330010533678812202354218097512545405947522435258490771167055601360483958644670632441572215539753697817977846174064955149290862569321978468622482839722413756570560574902614079729686524145351004748216637048440319989000889524345065854122758866688116427171479924442928230863465674813919123162824586178664583591245665294765456828489128831426076900422421902267105562632111110937054421750694165896040807198403850962455444362981230987879927244284909188845801561660979191338754992005240636899125607176060588611646710940507754100225698315520005593572972571636269561882670428252483600823257530420752963450";
    
    int i;
    
    for( i = 0; i < sizeof( numbers) / sizeof( char ); i++ )
    {
        printf( "%c", numbers[ i ] );
    }
    
    return 0;
}  

[/PHP]

---

### Post by Simian Man on 2011-04-14
> **stchman said:**
> When you initialize a character array like that the compiler puts a null terminator on the end of the array for you.  This would indeed make the array 1001 characters long.


Obviously, but he actually included 1001 actual digits.  At least that's what wc told me.  So if he *did* want to specify the size, it would have to be 1002.

---

### Post by Phenax on 2011-04-14
> **stchman said:**
> 
The correct code would be:


It's worth mentioning that sizeof(char) will always be 1 therefore it is not needed.

---

### Post by stchman on 2011-04-14
> **Simian Man said:**
> Obviously, but he actually included 1001 actual digits.  At least that's what wc told me.  So if he *did* want to specify the size, it would have to be 1002.

[PHP]

#include <stdio.h>
#include <string.h>

int main( void )
{
    char numbers[] = "7316717653133062491922511967442657474235534919493496983520312774506326239578318016984801869478851843858615607891129494954595017379583319528532088055111254069874715852386305071569329096329522744304355766896648950445244523161731856403098711121722383113622298934233803081353362766142828064444866452387493035890729629049156044077239071381051585930796086670172427121883998797908792274921901699720888093776657273330010533678812202354218097512545405947522435258490771167055601360483958644670632441572215539753697817977846174064955149290862569321978468622482839722413756570560574902614079729686524145351004748216637048440319989000889524345065854122758866688116427171479924442928230863465674813919123162824586178664583591245665294765456828489128831426076900422421902267105562632111110937054421750694165896040807198403850962455444362981230987879927244284909188845801561660979191338754992005240636899125607176060588611646710940507754100225698315520005593572972571636269561882670428252483600823257530420752963450";

    printf( "Number of elements in array numbers (sizeof) = %d\n\n", sizeof( numbers ) / sizeof( char ) );
    printf( "Number of elements in array numbers (strlen) = %d\n\n", strlen( numbers ) );

    return 0;
}

[/PHP]The resulting output is:

```

Number of elements in array numbers (sizeof) = 1001

Number of elements in array numbers (strlen) = 1000

```

---

### Post by stchman on 2011-04-14
> **Phenax said:**
> It's worth mentioning that sizeof(char) will always be 1 therefore it is not needed.

You are right, but I use that for the sake of clarity for when I do doubles, floats, ints, etc.

---

### Post by JupiterV2 on 2011-04-14
> **stchman said:**
> 
[PHP]for( i = 0; i < sizeof( numbers) / sizeof( char ); i++ )[/PHP]

I realize this was just an example but is it not considered good practice to use the following:

[PHP]
int size = strlen (numbers); /* or sizeof (numbers) / sizeof (char); */

for (i = 0; i < size; i++) { ... }
[/PHP]

This is because every time the for loop iterates, the statement [PHP]sizeof (numbers) / sizeof (char)[/PHP] is reevaluated, which can get quite costly.

---

### Post by Tony Flury on 2011-04-15
> **JupiterV2 said:**
> I realize this was just an example but is it not considered good practice to use the following:

[PHP]
int size = strlen (numbers); /* or sizeof (numbers) / sizeof (char); */

for (i = 0; i < size; i++) { ... }
[/PHP]

This is because every time the for loop iterates, the statement [PHP]sizeof (numbers) / sizeof (char)[/PHP] is reevaluated, which can get quite costly.

I think you will find that sizeof is calculated at compile time for this example, and therefore it does not matter that it is re-evaluated - although what might be re-evaluated is the division, and even then  i would imagine that gcc and most other decent compilers would optimise expression away as it does not change.

Premature optimisation is the root of bad code.

---

### Post by Arndt on 2011-04-15
> **Simian Man said:**
> Obviously, but he actually included 1001 actual digits.  At least that's what wc told me.  So if he *did* want to specify the size, it would have to be 1002.

Did you get a newline included when you used wc?

It seems gcc warns by default if the literal is too long:

"warning: initializer-string for array of chars is too long"

---

