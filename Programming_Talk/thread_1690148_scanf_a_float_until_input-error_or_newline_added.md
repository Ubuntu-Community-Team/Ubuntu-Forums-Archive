---
title: "scanf a float until input-error or newline added"
date: 2011-02-17
forum: Programming Talk
---

### Post by cguy on 2011-02-17
I want to read floats from the keyboard and display them along the time when they were read.
Upon invalid input or the insertion of a newline the program should terminate.

Here's my code, which does not treat the newline part because I don't know how to do it. Also, when the input is invalid (ie: inserted a letter), the second scanf (at the bottom of the "while") is being skipped and the while condition is evaluated to true, even though scan_ret IS 0.

[PHP]	int scan_ret = scanf("%f", &freq);
	while (( scan_ret != 0 ) || ( scan_ret != EOF ))
	{
		time(now);
		now_tm = localtime(now);
		/* TODO: replace stdout with f
		 * TODO: replace \n with \t
		 */
		if ( fprintf(stdout, "%.3f %d:%d:%d\n", freq,	now_tm->tm_hour,
								now_tm->tm_min,	now_tm->tm_sec)  < 0)
		{
			fprintf(stderr, "Could not write to file. Exiting.");
			exit(EXIT_FAILURE);
		}
		
		scan_ret = scanf("%f", &freq);
	}[/PHP]

So what's wrong with it and how can I fix it?

Also, which is the "proper" way to read an unknown number of numbers from the keyboard until newline/a letter is entered?


Thanks!

---

### Post by Some Penguin on 2011-02-18
(A != B) || (A != C)

is always going to be true unless B == C.

---

### Post by matrronchi on 2011-02-18
you should put a switch case in the while instead of the if

```


switch(freq){

case freq is a number:
                                   whatever you need
                                   break;
default:                   
                                   exit from while loop;
                                   break;

}


```

It's a pseudocode solution..you should make him do what you need..
consider that you'll go in the default case only if freq doesn't match any expression of the other cases.

So in your code you should need only one case expression to determin wether freq is a number or not...
if it is you can print it with the time if it isn't you can put a condition that will let you exit the while loop

---

### Post by cguy on 2011-02-18
thanks!

In my solution, as wrong as it is, why does the scanf inside the loop stop asking me for input after I enter a letter?

---

