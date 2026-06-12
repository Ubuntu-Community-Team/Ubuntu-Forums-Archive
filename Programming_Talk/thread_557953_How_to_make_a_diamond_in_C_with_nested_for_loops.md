---
title: "How to make a diamond in C with nested for loops"
date: 2007-09-23
forum: Programming Talk
---

### Post by climatewarrior on 2007-09-23
Hi this is a solution to a common programming exercise where you have to make a program that makes diamonds using nested for loops. This is only one way you can do it. There are many ither ways to do it




#include <stdio.h>
int main()
{
	int i,j,k;
	
	printf("Select Size \n");
	scanf("%d",&k);
	
	
	for(i=1; i<=k; i++)
		
	{
	
	for(j=1; j<=k-i; j++)
		
		{
		printf(" ");
		}
		
	for(j=1; j<=2*i-1; j++)

		{
		printf("*");
		}
	
	printf("\n");		
		
	}
	
	for(i=1; i<k; i++)

	{

	for(j=1; j<=i; j++)

		{
			printf(" ");
		}
		
	for(j=2*k-2*i-1; j>=1; j--)
		
		{
		printf("*");
		}	

	printf("\n");	

	}		

return(0);		
		
}

---

### Post by Smygis on 2007-09-23
And?

Btw, Always use [ code ] taggs when posting code.

---

### Post by Jessehk on 2007-09-23
That's nice.

---

### Post by Arwen on 2007-09-23
Cute :-)

---

### Post by CptPicard on 2007-09-23
It's also a typical homework assignment, so it would probably be better form not to spread code around, especially considering that I'm afraid you will not be getting any mad props for this yet.. ;)

---

### Post by slavik on 2007-09-23
I had to do something similar ... but in assembly :(

---

### Post by red_hax0r on 2012-10-22
Here's a more elegant, but equally long example.  It fixes a few problems such as making the number of vertical and horizontal asterisks equal to the actual size given.  Also note that an even size yields an even number of stars on every line.

```

#include <stdio.h>
#include <stdlib.h>

#define SIZE_LEN 3

int get_size()
{
    char input_str[SIZE_LEN];
    
    printf("What size diamond? ");
    fgets(input_str, SIZE_LEN, stdin);
    printf("\n");
    return atoi(input_str);
}

void print_chars(int n_times, char c)
{
    int i;
    for (i=0; i<n_times; i++)
    {
	printf("%c", c);
    }
}

int main()
{
    int i;
    int odd=0, even=0;
    int size;

    int n_stars=1;
    int reverse=0;
    
    size = get_size();
    
    if (size%2!=0)
	odd=1;
    else
	even=1;
    
    for (i=0; i<size; i++)
    {
	print_chars(size/2-n_stars+odd, ' ');
	print_chars(n_stars*2-odd, '*');
	print_chars(1, '\n');
	if (!reverse)
	    n_stars+=1;
	else
	    n_stars-=1;
	if (n_stars>size/2-even)
	    reverse=1;
	else if (n_stars<=0)
	    break;
    }
    return 0;
}

```

---

### Post by overdrank on 2012-10-22
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

