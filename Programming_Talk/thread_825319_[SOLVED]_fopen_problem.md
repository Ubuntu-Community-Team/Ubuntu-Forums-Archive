---
title: "[SOLVED] fopen problem"
date: 2008-06-10
forum: Programming Talk
---

### Post by spadewarrior on 2008-06-10
Hello.

I'm writing a simple program to take a bunch of integers from one text file, sort them in size, then save them in another file.

Everything appears to work except for the latter. The file is created but nothing is written to it and it returns NULL.

Any ideas?

Thanks.

[PHP]#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	FILE *p;
	FILE *w;
	int num[10], numOrd[10], n, temp, count;
	
	p = fopen("/home/sean/number", "rt");
	
	if(p==NULL)
	{
		printf("\nError opening file. Exiting...\n");
		getchar();
		exit(1);
	}
	
	n=0;
	while(!feof(p))
	{
		fscanf(p, "%i", &num[n]);
		n++;
	}
	
	fclose(p);
	printf("\nThe following was read from the file:\n");
	
	for(n=0; n<10; n++)
	{
		printf("%i\n", num[n]);
	}
	
	getchar();
	
	// Now to copy over num[] to numOrd[] for sorting...
	
	for(n=0; n<10; n++)
	{
		numOrd[n] = num[n];
	}
	
	// Now to arrange the numOrd[] array in ascending order...
	
	
	printf("\nHere are the numbers in order:");
	
	
	
	for(count=0; count<10; count++)
	{
		for(n=0; n<10; n++)
		{
			if(numOrd[n] > numOrd[n+1])
			{
				temp = numOrd[n]; // store 1st in temp
				numOrd[n] = numOrd[n+1]; // copy across 2nd number to 1st 
				numOrd[n+1] = temp; // copy temp to numord[n]
				temp = 0;
			}
		}	
	}
	// Now to print out the ordered numbers...
	
	for(n=0; n<10; n++)
	{
		printf("\n%d", numOrd[n]);
	}
	
	printf("\nPress a key to write them to a file...");
	
	getchar();
	
	w = fopen("/home/sean/number2", "w+"); 
	
	if(w==NULL);
	{
		printf("\nError opening file. Press any key to exit...\n");
		getchar();
		exit(1);
	}
	
	
	// Now to write them to the new file
	for(n=0; n<10; n++)
	{
		fprintf(w, "%i\n", numOrd[n]);
	}
	
	fclose(w);
	fclose(p);
	printf("\nThese have been written to the file 'numbersordered'.\n");
	
	
	getchar();
	return 0;
}
[/PHP]

---

### Post by unutbu on 2008-06-10
```
    if(w==NULL)**;**
    {
        printf("\nError opening file. Press any key to exit...\n");
        getchar();
        exit(1);
    } 
```

Remove the semicolon from the first line.

Also remove the second call (line 91) of

```
fclose(p);
```

You are calling it twice.

---

### Post by iansane on 2008-06-10
I'm not familiar with your method of opening and writing to a file, but I'm newb. I use #include <fstream> and the method here at cplusplus.com

[http://www.cplusplus.com/reference/iostream/fstream/open.html](http://www.cplusplus.com/reference/iostream/fstream/open.html)

I would cout << numOrd[n] somewhere with a pause after it to make sure the numbers are actually making it into numOrd and it's not some other crazy problem. Never can tell.

---

### Post by iansane on 2008-06-10
Ok never mind. I was too slow :-)

---

### Post by KingTermite on 2008-06-11
> **iansane said:**
> I'm not familiar with your method of opening and writing to a file, but I'm newb. I use #include <fstream> and the method here at cplusplus.com

[http://www.cplusplus.com/reference/iostream/fstream/open.html](http://www.cplusplus.com/reference/iostream/fstream/open.html)

I would cout << numOrd[n] somewhere with a pause after it to make sure the numbers are actually making it into numOrd and it's not some other crazy problem. Never can tell.
His method is old school "C". It's the original way it was done.

Streams are more of a C++ thing and came about later.

---

