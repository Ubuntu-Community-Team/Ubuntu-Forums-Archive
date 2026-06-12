---
title: "Issue with algebra in C"
date: 2012-02-21
forum: Programming Talk
---

### Post by alegomaster on 2012-02-21
I am working on a practice question for programming and it tells me to implement a specific mathematical function in it. The issue is I am always getting 0 for my output. The code is below:
```



#include <stdio.h>
#include <math.h>

int main ()
{
	double A;
	double H;
	double M;
	double t=0;
	
	scanf("%lg", &H);
	scanf("%lg", &M);
	
	while (M!=t) 
	{
		A= -6*pow(t,4)+H*pow(t,3)+2*pow(t, 2)+t; //The mathematical Function
		
		if (A<=0) 
		{
			printf("You touched the ground at: %lg", t);
			goto end;
		}
		else 
		{
			t++;
		}	
	}
	printf("The ballon didn't touch the ground");
end:
	return 0;
}

```

I am wondering if someone can help me with this code, I am not familiar with using algebra in C

---

### Post by Bachstelze on 2012-02-21
Do you know about Valgrind?

---

### Post by lisati on 2012-02-21
What value does t have when the loop starts?

---

### Post by alegomaster on 2012-02-21
> **lisati said:**
> What value does t have when the loop starts?

In my code I assigned it 0, but I removed it here to make the code look cleaner.

---

### Post by lisati on 2012-02-21
[s]The way the code as posted stands, t is uninitialised, which means that it could contain any old rubbish.[/s]

My bad, I took another look.

---

### Post by Bachstelze on 2012-02-21
> **alegomaster said:**
> In my code I assigned it 0, but I removed it here to make the code look cleaner.

Well, if t is 0, what do you think A will be?

> **lisati said:**
> [s]The way the code as posted stands, t is uninitialised, which means that it could contain any old rubbish.[/s]

My bad, I took another look.

He edited it, it was uninitialised, though that's not the real problem.

---

### Post by matt_symes on 2012-02-21
Hi

t = 0 is the problem here. A will always be 0 if t is 0.

Start with t = 1.

Kind regards

---

### Post by alegomaster on 2012-02-21
> **matt_symes said:**
> Hi

t = 0 is the problem here. A will always be 0 if t is 0.

Start with t = 1.

Kind regards

Thanks, it works great now. I must have spent too much time thinking that the
 A= (-6)*pow(t,4)+H*pow(t,3)+2*pow(t, 2)+t; line was incorrect.

---

