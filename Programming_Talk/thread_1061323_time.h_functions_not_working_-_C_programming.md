---
title: "time.h functions not working - C programming"
date: 2009-02-05
forum: Programming Talk
---

### Post by barefootsanders on 2009-02-05
Hi all.  I'm trying to use count() in a program to record running time and for some reason it keeps returning 0.  Is there something special I have to do in order to use these functions like link a library when using gcc or something?  Below is just a test case and always prints 0 to the screen.  BTW, I'm running ubuntu 8.10.

Any help would be much appreciated.

#include <stdlib.h>
#include <stdio.h>
#include <time.h>
```

int main(void) {
    double tmp;
    tmp = clock();
    printf("Count is: %f", tmp);
}
```

This always prints 0.  I'm compiling and running like this:

"gcc myfile.c -o out && ./out"

Any suggestions?

---

### Post by snova on 2009-02-05
> **barefootsanders said:**
> Is there something special I have to do in order to use these functions like link a library when using gcc or something?

If the function was contained in an external library, you would get errors- "undefined reference" and so on.

I can't find this function anywhere, at least certainly not in any of those headers. What is is supposed to do?

> to record running time

clock()?

---

### Post by JMJ_coder on 2009-02-05
I'm surprised that it even compiles for you. You should get an undefined reference error because there is no count() function. The function you are looking for is clock(), which will return the time since the program start. You can read more about it [here (http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.15.html)]("http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.15.html") and [here (http://opengroup.org/onlinepubs/007908799/xsh/time.h.html)]("http://opengroup.org/onlinepubs/007908799/xsh/time.h.html").

---

### Post by barefootsanders on 2009-02-05
I'm sorry, that should be clock();

Typo.  I will fix it. 

With that error fixed, any suggestions?

---

### Post by JMJ_coder on 2009-02-05
> **barefootsanders said:**
> I'm sorry, that should be clock();

Typo.  I will fix it. 

With that error fixed, any suggestions?

Check the return type of clock(); -- it doesn't return a floating point value. It returns a value of type clock_t.

---

### Post by barefootsanders on 2009-02-05
> **JMJ_coder said:**
> Check the return type of clock(); -- it doesn't return a floating point value. It returns a value of type clock_t.

Ive seen this done numerous places and people saying this works.   Ive also tried what you suggest,
```

clock_t tmp;
tmp = clock();
printf("%f", (double)tmp);
```

which doesnt work either.

---

### Post by barefootsanders on 2009-02-05
also, the code I posted originally works on my windows machine but not on ubuntu which leads me to believe something isnt linked properly.

---

### Post by snova on 2009-02-05
> **barefootsanders said:**
> ```

clock_t tmp;
tmp = clock();
printf("%f", (double)tmp);
```

Try using %i- this is not a floating point number, this is an integer, and that will mess up printf().

> **barefootsanders said:**
> also, the code I posted originally works on my windows machine but not on ubuntu which leads me to believe something isnt linked properly.

If it wasn't linked properly, there would be no executable to run.

---

### Post by JMJ_coder on 2009-02-05
> **barefootsanders said:**
> Ive seen this done numerous places and people saying this works.   Ive also tried what you suggest,
```

clock_t tmp;
tmp = clock();
printf("%f", (double)tmp);
```

which doesnt work either.

This code example came straight from the first site I linked you:

```
#include<time.h>
#include<stdio.h>

int main(void)
{
        clock_t ticks1, ticks2;

        ticks1=clock();
        ticks2=ticks1;
        while((ticks2/CLOCKS_PER_SEC-ticks1/CLOCKS_PER_SEC)<1)
                ticks2=clock();

        printf("Took %ld ticks to wait one second.\n",ticks2-ticks1);
        printf("This value should be the same as CLOCKS_PER_SEC which is %ld.\n",CLOCKS_PER_SEC);
        return 0;
}
```

Note, it probably should work with floating point values. clock_t is typedef'd, which in most implementations I think is a long unsigned int.

But, notice that clock() is returning a raw number of clock ticks, not a value like 5.2 ms. To get that value, as this example illustrates, you need to divide by CLOCKS_PER_SEC.

---

### Post by barefootsanders on 2009-02-05
The code you posted above seems to work but when I try to imitate it in my program it doesnt work.  Below is what I'm trying to do.  I'm trying to time how long it takes to generate different n by n matrices. I've included the source along w/ the output, which is all zeros again... Maybe I'm missing/overlooking something?  Any help would be much apprecieated.

```

#include<time.h>
#include<stdio.h>

int main(void) {
	
	clock_t startTime, endTime, elapsedTime;
	int i, j, n;
	
	// DEBUG
	n = 1000;
	
	// Generate random n x n array
	int array[n][n];
	
	// Initialize random seed
	srand(time(NULL));
	
	// Get start time
	startTime = clock();		

	// Populate n x n array
	for(i=0; i<n; i++) {
		for(j=0; j<n; j++) {
			// Generate a random number between 1 and 100
			array[i][j] = (rand()%100) + 1;
		}	
	}
	
	// Get end time
	endTime = clock();

	
        // Calculate elapsedTime
	elapsedTime = endTime - startTime;

	printf("Start time: %ld\n", startTime/CLOCKS_PER_SEC);
	printf("End time: %ld\n", endTime/CLOCKS_PER_SEC);
	printf("Time elapsed: %ld\n", elapsedTime/CLOCKS_PER_SEC);
	printf("Clocks per sec: %ld\n", CLOCKS_PER_SEC);

}

```


The output is:

Start time: 0
End time: 0
Time elapsed: 0
Clocks per sec: 1000000

I'm lost :/

---

### Post by cyfur01 on 2009-02-05
The operations you are doing are VERY quick, thus the ticks value only works out to 80000 or so (on my machine while debugging), so when you integer divide 80000 by 1000000, the result is naturally 0.

This works on my laptop:
```

#include<time.h>
#include<stdio.h>

int main(void) {
	
	double startTime, endTime, elapsedTime;

	int i, j, n;
	
	// DEBUG
	n = 1000;
	
	// Generate random n x n array
	int array[n][n];
	
	// Initialize random seed
	srand(time(NULL));
	
	// Get start time
	startTime = clock();		

	// Populate n x n array
	for(i=0; i<n; i++) {
		for(j=0; j<n; j++) {
			// Generate a random number between 1 and 100
			array[i][j] = (rand()%100) + 1;
		}	
	}
	
	// Get end time
	endTime = clock();

	
        // Calculate elapsedTime
	elapsedTime = endTime - startTime;

	printf("Start time: %lf\n", startTime/CLOCKS_PER_SEC);
	printf("End time: %lf\n", endTime/CLOCKS_PER_SEC);
	printf("Time elapsed: %lf\n", elapsedTime/CLOCKS_PER_SEC);
	printf("Clocks per sec: %ld\n", CLOCKS_PER_SEC);

}


```

```

Start time: 0.000000
End time: 0.070000
Time elapsed: 0.070000
Clocks per sec: 1000000

```

---

### Post by barefootsanders on 2009-02-05
> **cyfur01 said:**
> The operations you are doing are VERY quick, thus the ticks value only works out to 80000 or so (on my machine while debugging), so when you integer divide 80000 by 1000000, the result is naturally 0.

This works on my laptop:
```

#include<time.h>
#include<stdio.h>

int main(void) {
	
	double startTime, endTime, elapsedTime;

	int i, j, n;
	
	// DEBUG
	n = 1000;
	
	// Generate random n x n array
	int array[n][n];
	
	// Initialize random seed
	srand(time(NULL));
	
	// Get start time
	startTime = clock();		

	// Populate n x n array
	for(i=0; i<n; i++) {
		for(j=0; j<n; j++) {
			// Generate a random number between 1 and 100
			array[i][j] = (rand()%100) + 1;
		}	
	}
	
	// Get end time
	endTime = clock();

	
        // Calculate elapsedTime
	elapsedTime = endTime - startTime;

	printf("Start time: %lf\n", startTime/CLOCKS_PER_SEC);
	printf("End time: %lf\n", endTime/CLOCKS_PER_SEC);
	printf("Time elapsed: %lf\n", elapsedTime/CLOCKS_PER_SEC);
	printf("Clocks per sec: %ld\n", CLOCKS_PER_SEC);

}


```

```

Start time: 0.000000
End time: 0.070000
Time elapsed: 0.070000
Clocks per sec: 1000000

```

Ahh thank you so much.  I guess I should review my printf specifiers.  Probably core 2 duo with 4 gigs of ram doesn't help slow down those calculations either heh.  

Thanks again.  I can finally see results.

---

### Post by cyfur01 on 2009-02-05
> I guess I should review my printf specifiers.
Note that there are 2 changes. That was one of them, the other was the declaration of startTime/etc as doubles (which I believe you were trying earlier).

clock() does return a clock_t, but this is a typedef of an integer (whatever length), and thus C has no gripes automatically upconverting from an integer-type to a double.

---

