---
title: "[C] Prove me I'm stupid"
date: 2008-06-28
forum: Programming Talk
---

### Post by nvteighen on 2008-06-28
OK, see this is absurd piece of code:
[PHP]
#include <stdio.h>

/* ... */

static size_t file_length(FILE *file)
{
	int buffer[2];
	buffer[0] = 0; /* Obsessive initializing */
	buffer[1] = 0; /* The same as above */

	size_t length = 0;
	while(fscanf(file, "%d,%d", &buffer[0], &buffer[1]) != EOF)
		length++;

	/* Pairs counted! */
	
	return (length * 2); /* Total amount of integers returned */
}

/* ... */
[/PHP]

Please tell me that 'buffer' int array is useless and there's something better/more rational than that to count how many numbers are in a comma-separated data file.

The file format is straight simple:
```

2,3
445,555
23,445
12,2
1,12
23,44

```

Thanks in advance!

---

### Post by geirha on 2008-06-28
How about using fgetc() and count the number of '\n's?

---

### Post by nvteighen on 2008-06-28
> **geirha said:**
> How about using fgetc() and count the number of '\n's?
Thanks! That's the idea, just that instead of '\n' I'll go for counting commas.

[PHP]
static size_t file_length(FILE *file)
{
	size_t length = 0;
	while(!feof(file))
	{
		int buffer = fgetc(file);
		if(buffer == ',')	
			length++;
	}
	
	return (length * 2);
}
[/PHP]

More senseful now.

---

### Post by Phristen on 2008-06-28
> More senseful now.Yet, slower.

You original code is fine, but why do you need an array?
You can just reuse the same variable here:**while(fscanf(file, "%d,%d", &junk, &junk) != EOF)**

---

### Post by nvteighen on 2008-06-28
> **Phristen said:**
> Yet, slower.

You original code is fine, but why do you need an array?
You can just reuse the same variable here:**while(fscanf(file, "%d,%d", &junk, &junk) != EOF)**

First, the code had a treacherous bug: it didn't rewind the file. That caused a big disruption elsewhere; now solved.

Anyway, I/O functions are not time critical, so if I happen to lose a little fraction of a second, I really don't mind (actually, both ways run exactly on the same time, from what I measured: 0.002s for the **whole** executable). It's a personal exercise, not a "real" project...

But thanks!

---

### Post by geirha on 2008-06-28
> **Phristen said:**
> Yet, slower.
How can it possibly be slower?

---

### Post by Phristen on 2008-06-28
Actually, nvm, I think all the stdio functions are using buffering...

---

### Post by nvteighen on 2008-06-28
> **geirha said:**
> How can it possibly be slower?
Maybe because in one you're checking just one condition (if the read character is not EOF) and the other, two (if the read character is not EOF and then if the buffer variable is ',').

But there's no really measurable bottleneck. So it seems just to be a matter of style... as almost always in C threads.

In conclusion, I have both versions in the source code, one commented out and I'll decide which I like better later. It's "just" a helper function specific to the main module; I don't want to lose too much time in interface, but continue working on the implementation (by the way, I'm trying to create multi-branched dynamic trees).

---

### Post by Phristen on 2008-06-28
Another advantage (may or may not be important) is that %d,%d will check the format as it goes (and will segfault if it's a wrong format), while counting comas will do just that... Say you have a a file containing ",,,,,", right? No integer pairs at all, but your function will return 5.

---

### Post by dwhitney67 on 2008-06-28
Slower?  For sure!  Why are you reading each character in the file, one by one.  It would be more efficient to read an entire line.

You did not specify whether the file could have any erroneous data, so assuming it doesn't, here's how I would have determined the number count:
[PHP]unsigned int numValues(FILE *fp)
{
  unsigned int numValues = 0;
  char buf[80] = {0};

  while (fgets(buf, sizeof(buf), fp) != 0)
  { 
    ++numValues;
  } 
  return numValues * 2;
}[/PHP]

---

### Post by Phristen on 2008-06-28
> **dwhitney67 said:**
> Slower?  For sure!  Why are you reading each character in the file, one by one.  It would be more efficient to read an entire line.

You did not specify whether the file could have any erroneous data, so assuming it doesn't, here's how I would have determined the number count:
[PHP]unsigned int numValues(FILE *fp)
{
  unsigned int numValues = 0;
  char buf[80] = {0};

  while (fgets(buf, sizeof(buf), fp) != 0)
  { 
    ++numValues;
  } 
  return numValues * 2;
}[/PHP]
That's what I thought initially, but there may actually be buffering going on behind getc as well, I cannot remember.

---

### Post by nvteighen on 2008-06-29
> **dwhitney67 said:**
> Slower?  For sure!  Why are you reading each character in the file, one by one.  It would be more efficient to read an entire line.

Because in the mental state in which I was yesterday I automatically went for that approach without even thinking on an alternative.

A little phrase from Classical Philology: "If you have chosen the wrong hypothesis, it's because you haven't considered all of them".

Thank you!

---

