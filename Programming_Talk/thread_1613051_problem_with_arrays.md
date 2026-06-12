---
title: "problem with arrays"
date: 2010-11-04
forum: Programming Talk
---

### Post by cvvieth on 2010-11-04
having a problem when i compile and run the code. not sure if the entered data in the array is being stored in the same place as when i try to print it to the screen later.

```
#include<stdio.h>
int main(void)
{
    printf("How many bars would you like the graph to have. Enter a number no bigger than 10.\n");
    int bars=0;
    scanf("%d",&bars);

    int barData[bars][2];
    
    int i=0;
    int o=0;
    do{
        printf("Please enter the amount for bar %d.\n",i+1);        
        scanf("%d",&barData[i][1]);
        

        i++;
    }while(i<bars);
    
    i=0;    
    
    do{    
        do{
            printf("*");
            o++;    
        }while(o<barData[i][1]);
    }while(i+1<bars);
    return 0;
}

```

---

### Post by worksofcraft on 2010-11-04
I did a minimum number of changes to make it work (not counting adding the indentation back in).

[php]
#include<stdio.h>
int main(void) {
	printf("How many bars would you like the graph to have. Enter a number no bigger than 10.\n");
	int bars=0;
	scanf("%d",&bars);

	int barData[bars][2];

	int i=0;
	do{
		printf("Please enter the amount for bar %d.\n",i+1); 
		scanf("%d", &barData[i][1]);
		i++;
	} while (i < bars);

	i = 0;
	do { 
		int o = 0;
		do {
			printf("*");
			o++; 
		} while (o < barData[i][1]);
		printf("\n");
	} while( ++i < bars );
	return 0;
}
[/php]

spot the difference ;)

---

### Post by Some Penguin on 2010-11-04
```

   i=0;    
    
    do{    
        do{
            printf("*");
            o++;    
        }while(o<barData[i][1]);
    }while(i+1<bars);

```

Perhaps 'i' should change during the loop.

---

### Post by dwhitney67 on 2010-11-04
Why is this declaration as so...
```

int barData[bars][2];

```
This would have sufficed:
```

int barData[bars];

```
Of course, the code would need to be modified; for example:
```

    do{
        printf("Please enter the amount for bar %d.\n",i+1);        
        **scanf("%d",&barData[i]);**
        

        i++;
    }while(i<bars);


```

---

### Post by trent.josephsen on 2010-11-04
Not related to your problem: don't use scanf.

```
char buf[80], *endp;
printf("How many bars would you like the graph to have (1-10)? ");
fflush(stdout);		/* makes sure prompt without newline is printed */
fgets(buf, sizeof buf, stdin);
/* I'm skipping bounds- and error-checking with fgets for clarity */
unsigned long bars = strtoul(buf, &endp, 10);
if (endp == buf) {
	fprintf(stderr, "Error: non-numeric input\n");
	return -1;
} else if (bars < 1 || bars > 10) {
	fprintf(stderr, "Error: input out of bounds\n");
	return -1;
}
```

Being able to distinguish between nonsensical input and out-of-bounds input is always a good thing.

---

