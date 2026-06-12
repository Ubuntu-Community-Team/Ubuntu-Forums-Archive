---
title: "(simple C program) Do-while loop isn't working"
date: 2006-09-27
forum: Programming Talk
---

### Post by akudewan on 2006-09-27
I'm learning C, and I'm currently breaking my head over a simple program that calculates the volume of a sphere multiple times. This is what I want the program to do:
1) Take input from user (radius of sphere)
2) Check if this is greater than 0, if not, quit the program
3) Calculate volume of sphere and print the output.
4) Check if the user wishes to enter another radius. If yes, continue, else exit.

Here's the code that I made:

```

#include<stdio.h>
void main()
{
float r,vol;
char choice;
do
{
printf("\nEnter the radius: ");
scanf("%f",&r);
if(r<0)
  {
   printf("\nPlease enter only positive values");
   break;
  }
else
	{
   vol=(4*3.14*r*r*r)/3;
   printf("\nThe volume is %f",vol);
   printf("\nDo you wish to enter another radius? (Y/N): ");
   choice=getchar();
   printf("\nYour choice is %c",choice);
	}
}while(choice=='y'||choice=='Y');
printf("\n");
}

```

The program isn't working, it doesn't stop to ask for 'choice'. Whats wrong here??

(Using gcc to compile.)

Thanks

---

### Post by beathan on 2006-09-27
I think your initial problem is going to be your usage of scanf to read in your radius value. I suspect that there's still some garbage hanging around in stdin after you read in that float, perhaps a '\n' or '\r', that's making the program skip your 'choice = getchar()'. So, maybe something like the following, although I'm sure there's a cleaner, more approriate solution. This is just off the top of my head. What we do is add a while loop to flush out stdin, making sure that anything hanging out there is removed from the buffer and allowing getchar() to wait for input.

```

#include<stdio.h>

int main() {
        float r,vol;
        char choice;

        do
        {
                printf("\nEnter the radius: ");
                scanf("%f", &r);

                if(r<0)
                {
                        printf("\nPlease enter only positive values");
                        break;
                }
                else
                {
                        vol=(4*3.14*r*r*r)/3;

                        while(choice != '\n') {
                                choice = getchar();
                        }

                        printf("\nThe volume is %f",vol);
                        printf("\nDo you wish to enter another radius? (Y/N): ");
                        choice=getchar();
                        printf("\nYour choice is %c",choice);
                }
        }
        while(choice=='y'||choice=='Y');
        printf("\n");

        return 0;
}

```

I tested this on my box and it seemed to work fine. I changed the return type of main() to int and added a 'return 0;'.

I think the best solution would be to avoid scanf completely, perhaps using fgets instead to read into a buffer and then convert the resulting string into the float or double. Who knows :-)

---

### Post by beathan on 2006-09-27
Keep in mind that scanf() can be a quirky creature and it can take some time to fully understand what's going on with it. Check out [this link]("http://www.gidnetwork.com/b-64.html") for a little info on why it might be a good idea to skip scanf() and use other routines instead.

---

### Post by beathan on 2006-09-27
OK, so I'm a little bored. Thought I'd give this a little spin without using scanf(). I'm certain there are better ways to do this, but at least this seems to work.

I'm relatively new to C myself, so if anyone wants to step in with some tips, I'd gladly take them. The only thing I'm uncertain of is the call to fgets, wherein I specify a length of 100. This was an arbitrary choice. Smaller values, e.g. sizeof(float), cause the program to terminate silently after a couple trips through the while loop. I'm not quite sure why.

```

#include <stdio.h>
#include <stdlib.h>

int main() {
	
	float radius, vol;
	char choice = 'y';
	char * buf = malloc(sizeof(float));

	//Changed from do/while loop. Felt it was more readable this way.
	while(choice == 'y' || choice == 'Y') {

		printf("\nEnter the radius: ");
		
		//Make sure fgets works properly
		if(!(fgets(buf, 100, stdin))) {
			printf("Problem reading stdin with fgets.\n");
			exit(1);
		}
	
		//Convert buf to a float and assign to r
		radius = atof(buf);
		
		//Make sure r is a valid value
		if(radius < 0) {
			printf("Values greater than 0 are required. Try again.\n");
			continue; //Go to beginning of while loop
		}

		vol = (4 * 3.14 * radius * radius * radius) / 3;
		printf("The volume is: %f\n\n", vol);
		printf("Do you wish to enter another radius? (y/n): ");
		choice = getc(stdin);
		
		//Make sure stdin is clear
		while(getc(stdin) != '\n') ;

	}

	printf("\n");

	return 0;
}

```

---

### Post by Greg Knight on 2006-09-28
Hi,
 
For this kind of program there is nothing wrong with scanf. You just forgot to tell it to ignore the '\n' character after reading the radius.
 
The scanf line should read:
 
```
scanf("%f%*c",&r);
```
 
The '%f' tells it the input (radius) is going to be a float, and the '%*c' tells it to ignore the following '\n'.

The whole thing (using only scanf to read user input) could look this:

```

#include<stdio.h>

int main()
{
    float r,vol;
    char choice;

    do
    {
        printf("\nEnter the radius: ");
        scanf("%f%*c",&r);
        if(r<0)
        {
            printf("\nPlease enter only positive values\n");
            break;
        }
        else
        {
            vol=(4*3.14*r*r*r)/3;
			
            printf("\nThe volume is %f",vol);
            printf("\nDo you wish to enter another radius? (Y/N): ");
            /*this can be done with scanf too*/
            scanf("%c%*c",&choice);
            printf("\nYour choice is %c\n",choice);
        }
    }while(choice=='y'||choice=='Y');
    
    return 0;
}

```

Cheers!

Greg

---

### Post by akudewan on 2006-09-28
Hi beathan and Greg.

Thanks for your response.

Greg: > The '%f' tells it the input (radius) is going to be a float, and the '%*c' tells it to ignore the following '\n'.
*The following '\n'* - is this the \n that is entered by the user when he presses Enter?

beathan: That page you linked me to has some great info Thanks! :) I must admit that I haven't understood the other code that you wrote, but now I've got some new things to learn.

Another thing that I noticed: If I just declare a character, and print it, it takes a value of -73. Apart from the whitespaces, it was this -73 value that caused the loop to break. What is this -73? There aren't any negative Ascii values, right ?

```
#include<stdio.h>
int main()
{
char choice;
printf("%d",choice);
return 0;
}

```

---

### Post by DavidBell on 2006-09-28
> **akudewan said:**
> There aren't any negative Ascii values, right ?

char is just a type that is handly for ascii, it's not ascii. Range of char is -128 to 127, unsigned char is 0 to 255. Numbers out of range C rolls over and starts counting from begining again. (ie char 127  + 1 = -128 )

If you don't define it, the variable could be anything.

DB

---

### Post by akudewan on 2006-09-28
Ah, ok now I get it. Since I haven't assigned any value to the variable, any value will be allocated to it. (Thanks David!)

But then again, why is it always -73. Why isn't it random?

Sorry for being such a bother!

---

### Post by DavidBell on 2006-09-28
Even though it may seem that way you can't always guarantee it will be -73. I'm not an expert with compilers but AFAIK when you declare a variable C compilers just allocate the memory and you get whatever is there from the last time it was used. DB

---

