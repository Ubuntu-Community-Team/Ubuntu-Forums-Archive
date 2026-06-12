---
title: "compiling error in beginner's program"
date: 2007-10-02
forum: Programming Talk
---

### Post by xboxbman on 2007-10-02
I'm learning how to write C and I have a program I'm trying to write, but keep getting these compiler errors.  I can't for the life of me figure out why, i think the code is good. Here it is
```
#include <stdio.h>
#include <math.h>
	
int main()
{

	double expo, biomaroot, biomabov, carbon, M_PI, lon, circum, diameter; 
	
	printf("This caculation only works for softwood trees.  What is the circumference of the tree?\n");
	scanf("%d", &circum);

	lon = 2.718281828459;

	biomabov = pow(1.019, expo);
	biomaroot = biomabov*0.2;
	carbon = 0.5*(biomabov+biomaroot);

	diameter = circum*/M_PI;
	expo = ln*diameter*(2.391-2.413);

	printf("here is diameter %diameter \n");
	printf("here is expo %expo \n");

return(0);
}
```

the error i get is :
```
bman@wherewulf:~$ gcc -lm trees.c -o tree 
trees.c: In function ‘main’:
trees.c:7: error: expected identifier or ‘(’ before numeric constant
trees.c:10: error: ‘circum’ undeclared (first use in this function)
trees.c:10: error: (Each undeclared identifier is reported only once
trees.c:10: error: for each function it appears in.)
trees.c:14: error: ‘lon’ undeclared (first use in this function)
trees.c:20: error: ‘diameter’ undeclared (first use in this function)
trees.c:20: error: expected expression before ‘/’ token
trees.c:21: error: ‘ln’ undeclared (first use in this function)

```

the code is incomplete.  I'm just trying to test out the math first before I write the whole thing out.  I know it's a silly error I've made, but I can't find it.  Help me Ubuntu Forums, you're my only hope

---

### Post by aks44 on 2007-10-02
> **xboxbman said:**
> ```
	double expo, biomaroot, biomabov, carbon, M_PI, lon, circum, diameter;
```
M_PI is declared in <math.h> (as a macro). It expands as 3.14159..., so your above line is indeed expanded as

```
	double expo, biomaroot, biomabov, carbon, 3.14159, lon, circum, diameter;
```

Why did you feel the need to "redeclare" it anyway (notwithstanding the error)?


The rest of the errors are just typos you made, once you'll have removed that M_PI "declaration" you should be able to sort them out if you read the error messages and act accordingly. ;)

---

### Post by xboxbman on 2007-10-02
i redeclared it cause i didn't know it wasn't necessary. I knew it was something stupid.  Thanks dude.

> **aks44 said:**
> M_PI is declared in <math.h> (as a macro). It expands as 3.14159..., so your above line is indeed expanded as

```
	double expo, biomaroot, biomabov, carbon, 3.14159, lon, circum, diameter;
```

Why did you feel the need to "redeclare" it anyway (notwithstanding the error)?


The rest of the errors are just typos you made, once you'll have removed that M_PI "declaration" you should be able to sort them out if you read the error messages and act accordingly. ;)

---

### Post by Compyx on 2007-10-02
Apart from the errors aks44 already pointed out, here's a few more:

> **xboxbman said:**
> 
```

	scanf("%d", &circum);

```
Undefined behavior: you tell scanf() to expect a pointer to a signed int but you pass it a pointer to double; change the specifier to '%g'.

> ```

	printf("here is diameter %diameter \n");
	printf("here is expo %expo \n");

```
This isn't Perl or PHP, C doesn't do interpolation of variables, if you want to print the contents of 'diameter' do this:
```

    printf("here is diameter %g"\n", diameter);

```
The same goes for 'expo'.

> 
```

return(0);

```
No need for parentheses: return isn't a function, it's a keyword (but it's harmless).


You might also want to get into the habit of cranking up your compilers warnings, at the very least these:
```

-g -Wall -Wextra -pedantic -ansi -O2

```

HTH

---

### Post by aks44 on 2007-10-02
Good points Compyx, looks like my C is becoming quite rusty. :oops:

---

### Post by Compyx on 2007-10-02
> **aks44 said:**
> Good points Compyx, looks like my C is becoming quite rusty. :oops:

Well, I code in C nearly every day, so that keeps me on my toes. ;)

---

### Post by dwhitney67 on 2007-10-02
Fix this problem too:
```
diameter = circum*/M_PI;
```

It should be:
```
diameter = circum / M_PI;
```

---

