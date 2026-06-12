---
title: "need some c help"
date: 2008-12-04
forum: Programming Talk
---

### Post by lilbrownjumpsuit on 2008-12-04
Hey guys,

I'm having some problems with a c program I wrote:

#include <stdio.h>
#include <math.h>

int main(int argc, char * argv[])
{
	double A,B,to,t,tau,vct;
	
	printf("enter value for A ");
	scanf("%lf",&A);
	
	printf("enter a value for B ");
	scanf("%lf",&B);

	printf("enter a value for to ");
	scanf("%lf",&to);

	printf("enter a value for tau ");
	scanf("%lf",&tau);

	printf("enter a value for vct ");
	scanf("%lf",&vct);

	t=-tau*log(vct-A/B)+to;
	printf("%lf",&t);
	return 0;
}


I'm getting an error: "file.c:26: warning: format ‘%lf’ expects type ‘double’, but argument 2 has type ‘double *’

Not sure what I did wrong. Any help will be appreciated.

---

### Post by PandaGoat on 2008-12-04
In the scanf's you pass it the reference (actually you pass a pointer to the reference in C)--this is what & does--so it can modify the variable to what the user inputs.

The printf function takes just a variable--a copy of its value--not a pointer to it since it does not need to modify it.  Change "printf("%lf",&t);" to "printf("%lf",t);"

---

### Post by jpkotta on 2008-12-04
You're referencing t.  &t is a pointer to double, but printf is expecting a double.

---

