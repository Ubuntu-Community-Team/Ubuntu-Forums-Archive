---
title: "Can't Compile"
date: 2009-11-20
forum: Programming Talk
---

### Post by PostChache on 2009-11-20
For some reason gcc test.c -o 123 isn't making an executable file. It'll compile it but I can't do ./123 This use to work and I don't know what happened. Any ideas?

Okay actually for some reason whenever I compile this program it doesn't make an executable file so I don't know what's wrong with it because it was working last night.

This is the code that I'm trying to compile
```

#include <stdio.h>
const double k_ftc = (1.8 * n) + 32; //Fahrenheit to Celsius
const double k_ctk = 273.16; //Celsius to Kelvin 
void Tempature(double n);

int main(void)
{
	double F;
	int status;
	printf("Hello, let's convert Fahrenheit to Celsius, then Celsius to Kelvin!\n");
	printf("Please enter the tempature in Fahrenheit\n");
	status = scanf("%lf", &F);
	while (status == 1)
	{
		Tempature(F);
		printf("If you would like to continue type in a new tempature, or enter q to quit.\n");
		status = scanf("%lf", &F);
	}
	return 0;
}

void Tempature(double n)
{
	printf("%.2lf Fahrenheit is %.2lf Celsius which is %.2lf Kelvin.\n", n, k_ftc, k_ftc + k_ctk);
}

```

---

### Post by Slimbo on 2009-11-20
```
main.cpp:2: error: &#8216;n&#8217; was not declared in this scope
```

Get rid of all the errors and you should be fine.

---

### Post by PostChache on 2009-11-20
> **Slimbo said:**
> ```
main.cpp:2: error: ‘n’ was not declared in this scope
```

Get rid of all the errors and you should be fine.

I've fixed it, but my real question is why is it that it would make an executable before even though it had this error?

---

### Post by Tony Flury on 2009-11-20
It would never have worked - a const defines a constant value - and you were trying to use to define a formula : 
```

const double k_ftc = (1.8 * n) + 32; //Fahrenheit to Celsius

```

Depending on the value of n this would create a single fixed value and the output would always be exactly the same - regardless of the input.

If you want to define a formula - use a function.

---

### Post by Arndt on 2009-11-20
> **PostChache said:**
> I've fixed it, but my real question is why is it that it would make an executable before even though it had this error?

If there are compilation errors, the output file shouldn't be created at all. If there are linking errors, it is created but then not made executable. Maybe at some point you had linking errors but not compilation errors.

(It's spelled "temperature", by the way.)

---

### Post by PostChache on 2009-11-21
> **Tony Flury said:**
> It would never have worked - a const defines a constant value - and you were trying to use to define a formula : 
```

const double k_ftc = (1.8 * n) + 32; //Fahrenheit to Celsius

```

Depending on the value of n this would create a single fixed value and the output would always be exactly the same - regardless of the input.

If you want to define a formula - use a function.

Okay thank you.

> **Arndt said:**
> If there are compilation errors, the output file shouldn't be created at all. If there are linking errors, it is created but then not made executable. Maybe at some point you had linking errors but not compilation errors.

(It's spelled "temperature", by the way.)

Thanks, I didn't even notice.

---

