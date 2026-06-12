---
title: "Number Squaring Program in C"
date: 2010-02-13
forum: Programming Talk
---

### Post by jasperyate on 2010-02-13
I'm new to this and I tried to get answers from this forum on this a while ago and some people felt it necessary to either give me mysterious clues or act like my ignorance was a burden to them and write code that i didn't understand. so i just want to know what im doing wrong, why, and how to do it right. Any real help will be greatly appreciated. 

Also I haven't found any explanations around the internet.

I want to write a simple program in c that will take an input number, square it, and print the result - i dont know why i just want to. Being new to C all i've been able to do is surf around and piece together expressions that i think might get the job done. so this is what i have (with my comments of what i think i'm doing):

```
#include <stdio.h>

main()
{
	int i;					/* declare 'i'*/
	char line[256];				/* declare 'line'*/

	printf("type an integer:\n");		/* print request*/
	line[256] = getchar();			/* get char, set to line*/
	i = atoi(line, 256);			/* convert input to integer via atoi*/

	while(i < 1000)
		{
		printf("%d\n", i);
		i = i ^ 2;
                return EOF;
		}
	
	return 0;
}
```

for any input i get this output (i put return EOF because it will return infinite zeros instead of just the one):

```
Jaspers-HackBook-Mini:Desktop admin$ ./a.out
type an integer:
4
0
Abort trap
```

so thats where im stuck. i clearly dont know what im doing but im trying to learn by doing (as much as that possible without learning bad habbits). thanks for any real help.

---

### Post by saidinesh5 on 2010-02-13
char line[256];				/* declare 'line'*/

line[256] = getchar();	

i dont think this is the cause of problem , but still...how can you do this?? 

char line[256] => you have line[0] to line[255]

line[256] isnt a memory belonging to the array.

---

### Post by saidinesh5 on 2010-02-13
and hey isnt ^ the bitwise XOR operator in C??

---

### Post by baddog144 on 2010-02-13
```

#include <stdio.h>

int main()
{
    int i;                  /* declare 'i'*/

    printf("type an integer:"); /* Ask the user to type a number */
    scanf("%i", &i); /* Use scanf() to get the number (scanf works like printf in reverse) */
    printf("%i squared is %i", i, i * i); /* Display the result */
    return 0;
}

```

i ^ 2 is not the same as i * i. ^ is bitwise OR (I think), which is an entirely different thing ;)

If you have any questions about the code, feel free to ask :)

Scanf is generally a much better thing to use than getchar, because it supports things like going straight to integers, and getting more than one char at a time ;)

---

### Post by saidinesh5 on 2010-02-13
ya got your problem

^ is the bitwise XOR operator in C. if you want to square 2 numbers in C, use the math library function or simply i = i*i

so when you bitwise XOR your i with 2 

i= 0000 0000 0000 0000  0000 0000 0000 0100  (i=4)
2= 0000 0000 0000 0000  0000 0000 0000 0010
-----------------------------------------
i= 0000 0000 0000 0000  0000 0000 0000 0110

so i guess your problem is found ! :)
hpy V.DAY :)

---

### Post by Krupski on 2010-02-13
> **jasperyate said:**
> I'm new to this and I tried to get answers from this forum on this a while ago and some people felt it necessary to either give me mysterious clues or act like my ignorance was a burden to them and write code that i didn't understand.

Try this... it's full of comments to help you understand what's going on. It's by no means the best or only way to do it, but it's one way! :D

```

#include <stdio.h>
#include <string.h>

// to be sure what our buffer size is
#undef BUFSIZ
#define BUFSIZ 1024

// prototype for readline function
int readln(FILE*, char*);

int main(void)
{
	// declare variables
	char buffer[BUFSIZ];
	int integer, square;

	// prompt
	fprintf(stdout, "\nPlease enter an integer: ");

	// read user input into buffer
	readln(stdin, buffer);

	// get integer value of what's in the buffer
	integer = atoi(buffer);

	// generate the square
	square = integer * integer;

	// print the results
	fprintf(stdout, "The square of %d is %d\n", integer, square);

	return 0;
}



int readln(FILE *fp, char *str)
{
	// declare variables
	char buf[BUFSIZ];
	int len;

	// make buffer "null" if no input
	buf[0] = 0;

	// read into buffer
	fgets(buf, BUFSIZ, fp);

	// get the length of the buffer
	len = strlen(buf);

	// strip out newlines, cr, lf and other junk at the end
	while (len >= 0) {
		if (buf[len] <= 0x20) { buf[len] = 0; len--; }
		else { break; }
	}

	len++;

	// null terminate the clean line
	buf[len] = 0;

	// copy the temp buffer to the caller's buffer
	strncpy(str, buf, BUFSIZ);

	return 0;
}

```

(edit to add): This code does not check for errors, overflows or any kind of error. It could be improved by using long-long integers, reverse (square root) checks to see if the result is correct and tests for squaring negative numbers.

---

### Post by jasperyate on 2010-02-13
Thanks everyone. I tried baddog44s first, ive got a few questions.

```
#include <stdio.h>

int main()
{
    int i;                  /* declare 'i'*/

    printf("type an integer:"); /* Ask the user to type a number */
    scanf("%i", &i); /* Use scanf() to get the number (scanf works like printf in reverse) */
    printf("%i squared is %i", i, i * i); /* Display the result */
    return 0;
}
```

-why is main() sometimes declared as an int? or is it always meant to be?
-i take it that the expression scanf("%i", &i) is telling the program to expect an input value (%i) and then store it in i (&i). maybe some clarification in your own words in exactly what thats doing would be helpful, im still unclear on why use %i (as opposed to %d) and what exactly &i does.
-what is the purpose of the &i in the scanf expression?

cheers

---

### Post by baddog144 on 2010-02-13
> **jasperyate said:**
> Thanks everyone. I tried baddog44s first, ive got a few questions.

```
#include <stdio.h>

int main()
{
    int i;                  /* declare 'i'*/

    printf("type an integer:"); /* Ask the user to type a number */
    scanf("%i", &i); /* Use scanf() to get the number (scanf works like printf in reverse) */
    printf("%i squared is %i", i, i * i); /* Display the result */
    return 0;
}
```

-why is main() sometimes declared as an int? or is it always meant to be?
-i take it that the expression scanf("%i", &i) is telling the program to expect an input value (%i) and then store it in i (&i). maybe some clarification in your own words in exactly what thats doing would be helpful, im still unclear on why use %i (as opposed to %d) and what exactly &i does.
-what is the purpose of the &i in the scanf expression?

cheers

- As far as I know, main() should generally be defined as either int or void, and since you return 0, you may as well define it as int

-I actually probably should have used %d instead of %i, that was my mistake ;) 

- &i is C notation which tells the compiler the address in memory of i, which is what scanf needs to give i a new value. There is more info on pointers [here ]("http://home.netcom.com/~tjensen/ptr/pointers.htm") :)

Hope this helps

---

### Post by MadCow108 on 2010-02-13
1. main should always be declared as int because you expect programs to return success or failure per an int. This behavior is provided by declaring main int and returning an appropriate number.
And the standard says so :)

2. scanf reads formated input/output with the string defining its format. read about it with man scanf (there's also a fscanf which reads from formated file streams)
%i and %d are the same. It stands for either integer or decimal. They both define signed integer type (int)

3. The & operator returns a pointer (address) to the memory where the variable is saved. scanf takes this address and copies its result into that space.

---

### Post by gil_johnson on 2010-02-13
[QUOTE=jasperyate;8821853]

```
#include <stdio.h>

main()
{
    int i;                    /* declare 'i'*/
    char line[256];                /* declare 'line'*/

    printf("type an integer:\n");        /* print request*/
    line[256] = getchar();            /* get char, set to line*/
    i = atoi(line, 256);            /* convert input to integer via atoi*/

    while(i < 1000)
        {
        printf("%d\n", i);
        i = i ^ 2;
                return EOF;
        }    
    return 0;
}
```You also need to print the result of squaring i, and increment i in your "while" loop. A "return" in the loop ends the program there. - Gil

---

### Post by jasperyate on 2010-02-13
thanks all. much appreciated.

---

### Post by Krupski on 2010-02-14
> **jasperyate said:**
> Thanks everyone. I tried baddog44s first, ive got a few questions.


For pointers (i.e. *N and &N stuff), someone here wrote me a little piece of code that explains EVERYTHING.

Just compile this, run it, look at it's output and then go back to the source and see WHAT is generating those numbers.

It's like a picture of a thousand words!

```

#include <stdio.h>

int j, k;
int *ptr;
FILE *fp;

int main(void)
{
    fp = stdout;
    j = 1;
    k = 2;
    ptr = &k;
    fprintf(fp, "\n");
    fprintf(fp, "j has the value %d and is stored at %p\n", j, &j);
    fprintf(fp, "k has the value %d and is stored at %p\n", k, &k);
    fprintf(fp, "ptr has the value %p and is stored at %p\n", ptr, &ptr);
    fprintf(fp, "The value of the integer pointed to by ptr is %d\n", *ptr);

    return 0;
}

```

(p.s. thanks to the person who wrote this for me... wish I remembered who you were).

-- Roger

---

