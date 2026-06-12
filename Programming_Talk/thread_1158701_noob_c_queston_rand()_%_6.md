---
title: "noob c queston: rand() % 6"
date: 2009-05-13
forum: Programming Talk
---

### Post by badperson on 2009-05-13
Hi,
I followed some code that I basically copied verbatim out of a book that uses random numbers...here's the code: 

```
/* random dice tester*/

#include <stdio.h>
#include <stdlib.h>

	int main( void ){

	printf("\n**** WELCOME TO THE RANDOM NUMBER DICE TESTER ***\n");

	int frequency1=0;
	int frequency2=0;
	int frequency3=0;
	int frequency4=0;
	int frequency5=0;
	int frequency6=0;

	int roll;
	int face;

		for(roll=1;roll<=6000;roll++){
			face = 1 + rand() % 6; /* should be random number from 1 to 6 */

			switch(face){
				case 1: 
				++frequency1;
				break;

				case 2: 
				++frequency2;
				break;

				case 3: 
				++frequency3;
				break;

				case 4: 
				++frequency4;
				break;

				case 5: 
				++frequency5;
				break;

				case 6: 
				++frequency6;
				break;


			} /* end switch */

		} /* end for */

	/* now display results */
	printf("%s%13s\n", "Face", "Frequency");
	printf("	1%13d\n", frequency1);
	printf("	2%13d\n", frequency2);
	printf("	3%13d\n", frequency3);
	printf("	4%13d\n", frequency4);
	printf("	5%13d\n", frequency5);
	printf("	6%13d\n", frequency6);



	return (0);
	} /* end main */
```
It compiles and runs fine...but when I run it multiple times, I always get the same answer...here's the output of multiple runs:

```
jason@jason-desktop:/media/files/code/CFiles/intro$ ./dice

**** WELCOME TO THE RANDOM NUMBER DICE TESTER ***
Face    Frequency
	1          980
	2          993
	3         1030
	4         1009
	5         1002
	6          986
jason@jason-desktop:/media/files/code/CFiles/intro$ ./dice

**** WELCOME TO THE RANDOM NUMBER DICE TESTER ***
Face    Frequency
	1          980
	2          993
	3         1030
	4         1009
	5         1002
	6          986
jason@jason-desktop:/media/files/code/CFiles/intro$ gcc dicetest.c -o dice -lm
jason@jason-desktop:/media/files/code/CFiles/intro$ ./dice

**** WELCOME TO THE RANDOM NUMBER DICE TESTER ***
Face    Frequency
	1          980
	2          993
	3         1030
	4         1009
	5         1002
	6          986
jason@jason-desktop:/media/files/code/CFiles/intro$ 

```

Is that normal? Shouldn't the results be different everytime it's run? Here are the commands I used to compile and run, respectively:

```
gcc dicetest.c -o dice -lm
./dice


```

thanks,
bp

---

### Post by badperson on 2009-05-13
okay...had I read the NEXT PARAGRAPH I would have seen that's expected behavior...friggin' newb...):P):P

---

### Post by lisati on 2009-05-13
> **badperson said:**
> okay...had I read the NEXT PARAGRAPH I would have seen that's expected behavior...friggin' newb...):P):P

):P That's common: I'm not sure of what the equivalent is in C, having never used random numbers in C, but a "randomize" statement/function is commonly useful. (Thinks: I vaguely recall something about srand().....)

---

### Post by sonofusion82 on 2009-05-13
> **lisati said:**
> ):P That's common: I'm not sure of what the equivalent is in C, having never used random numbers in C, but a "randomize" statement/function is commonly useful. (Thinks: I vaguely recall something about srand().....)


badperson, yes, it is expected behavior. rand() function is a pseudo random number generator... NOT a real random number generator because computers are just big friggin calculator and its calculation and logic is always meant to be predictable (unless less there are bug ;))
for real random number generator, it will require real external random noise source, most PC does not contain such capability and will use things like user mouse movement and keystrokes as a kind of random source.

srand() function will just initialize the rand() function to a different pseudo output sequence. if you input srand with the same value everytime, it will output the same result.

so, lisati is right, in C, have a look at srand() function.
it will seed the random number generator.
usually the formula is to seed it with current time with something like:

srand(time(NULL));

this will return different result every time u run the program unless you run it multiple time during the same 1 second period.

---

### Post by Sockerdrickan on 2009-05-15
srand(time(0));

---

### Post by jon zendatta on 2009-05-15
first you need the header file
[PHP]#include<time.h>[/PHP]
then to seed the random number generator
 [PHP]srand((unsigned)time (NULL));[/PHP]
next number generated will be
[PHP]srand(1);[/PHP]

---

### Post by Sockerdrickan on 2009-05-15
> **jon zendatta said:**
> first you need the header file
[php]#include<time.h>[/php]then to seed the random number generator
 [php]srand((unsigned)time (NULL));[/php]next number generated will be
[php]srand(1);[/php]
[SIZE=5]**-_-**[/SIZE] [SIZE=2]*time* does not take a pointer, as stated in the previous post.[/SIZE] ):P So it should not be NULL, but 0.

---

### Post by Arndt on 2009-05-15
> **Tux0r said:**
> [SIZE=5]**-_-**[/SIZE] [SIZE=2]*time* does not take a pointer, as stated in the previous post.[/SIZE] ):P So it should not be NULL, but 0.

No, but it makes no difference.

---

### Post by Sockerdrickan on 2009-05-15
> **Arndt said:**
> No, but it makes no difference.
It makes difference in readable code so don't teach people to use time(NULL) please.

---

### Post by stroyan on 2009-05-15
time() isn't a very good seed value.  It is awfully predictable and doesn't change often enough.  Linux has /dev/random and /dev/urandom for getting random seeds.  Reading from /dev/random may block waiting for the kernel to have enough 'entropy' to provide high quality random bytes.  Reads from /dev/urandom always return promptly even if the results are not of as high of quality.  See "man urandom" for more information.
```

#include <fcntl.h>
        int seed;
        int fildes;

                fildes = open("/dev/urandom", O_RDONLY);
                if (fildes == -1) {
                        printf("random seeding failed\n");
                        return 1;
                }
                read(fildes, &seed, sizeof(seed));
                close(fildes);
                srand(seed);


```

---

### Post by Arndt on 2009-05-15
> **Tux0r said:**
> It makes difference in readable code so don't teach people to use time(NULL) please.

You make no sense. The argument is a pointer, and NULL signals that it's the NULL pointer. 0 does the same, if you know it's a pointer. If you don't know, you may be fooled into thinking it's not a pointer.

It's all the same to the compiler, as long as a correct declaration of 'time' has been made (explicitly or by including the proper include file).

I could say that I prefer time((time_t *) 0), but I'm not sure what I prefer, actually. 'time_t' didn't always exist.

---

### Post by nrs on 2009-05-15
> **Tux0r said:**
> [SIZE=5]**-_-**[/SIZE] [SIZE=2]*time* does not take a pointer[/SIZE]
time does take a pointer. check the man pages.

---

### Post by Sockerdrickan on 2009-05-16
Ok then I blame my GCC warnings because it said it doesn't.

---

