---
title: "Learning C, problem with an exercise."
date: 2008-10-15
forum: Programming Talk
---

### Post by medeshago on 2008-10-15
I have to do the following:
Read a number and calculate the following sequence:
1-1/2+1/3-1/4+1/5...1/n

This is the way I'm doing it, but it doesn't work:

```
#include <stdio.h>

int main()
{
	int a=0, n, suma=0;
	float den;
	
	printf ("\n Ingrese el número : ");
	scanf ("%i", &n);
	
	while (a<n)
	{
		if (a%2==0){
			a++;
			den=1/a;
			suma-=den;}
		
		else{
			a++;
			den=1/a;
			suma+=den;}
	}
	
	
	printf ("\n Resultado secuencia = %i", suma);
	
	return 0;
}
```

---

### Post by dmm1285 on 2008-10-15
```



		if (a%2==0){
			a++;
			den=1/a;
			suma-=den;}
		
		else{
			a++;
			den=1/a;
			suma+=den;}
	}
	
	
}
```

Try switching your addition and subtraction like this.

---

### Post by medeshago on 2008-10-15
Just did it, still not working.

---

### Post by Can+~ on 2008-10-15
Problem is, you're doing integer division:

1/2 = [0.5] = 0
1/3 = [0.33333..] = 0
1/4 = [0.25] = 0

To circumvent this issue, work with floats.

---

### Post by medeshago on 2008-10-15
This is how it looks now:

```
#include <stdio.h>

int main()
{
	int a=0, n;
	float den, suma=0.0;
	
	printf ("\n Ingrese el número : ");
	scanf ("%i", &n);
	
	while (a<n)
	{
		if (a%2==0){
			a++;
			den=1.0/a;
			suma-=den;}
		
		else{
			a++;
			den=1.0/a;
			suma+=den;}
	}
	
	printf("%d", den);
	printf ("\n Resultado secuencia = %d", suma);
	
	return 0;
}
```

But this is what I get:

Ingrese el número : 5
Resultado secuencia = 536870912

---

### Post by Can+~ on 2008-10-15
Now you got a printing problem:

```
printf("%d", den);
printf ("\n Resultado secuencia = %d", suma);
```

Should be

```
printf("%f", den);
printf ("\n Resultado secuencia = %f", suma);
```

btw, here's my implementation (with for, and inverting sign)

[PHP]int main(int argc, char** argv)
{
	float total=0;
	int count, sign=1, max=20;
	
	for (count=1; count < max; count++)
	{
		total += sign*(1.0/count);
		printf("%d : %.8f\n", count, total);
		
		sign = -sign;
	}	
	
	printf("%.8f", total);
	
	return 0;
}[/PHP]

sign inverts each iteration, meaning that you don't need that "if" in between.

---

### Post by medeshago on 2008-10-15
Thanks, man, now it works great.

---

