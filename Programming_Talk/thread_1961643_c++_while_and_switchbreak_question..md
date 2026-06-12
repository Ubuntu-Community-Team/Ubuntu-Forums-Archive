---
title: "c++ while and switch/break question."
date: 2012-04-19
forum: Programming Talk
---

### Post by rafaelcbf on 2012-04-19
[PHP]#include <stdio.h>
#include <iostream>
int a,b,c,d,e,f,g,h,i,j=1,k=0,l=0,m=0,n=1,o=0,p=0,q=0,r=1;
int main()
{
printf("Ingrece primer numero, primera fila, de izquierda a derecha:");
scanf("%i",&a);
printf("Ingrece segundo numero, primera fila, de izquierda a derecha:");
scanf("%i",&b);
printf("Ingrece tercer numero, primera fila, de izquierda a derecha:");
scanf("%i",&c);
printf("Ingrece primer numero, segunda fila, de izquierda a derecha:");
scanf("%i",&d);
printf("Ingrece segundo numero, segunda fila, de izquierda a derecha:");
scanf("%i",&e);
printf("Ingrece tercer numero, segunda fila, de izquierda a derecha:");
scanf("%i",&f);
printf("Ingrece primer numero, tercer fila, de izquierda a derecha:");
scanf("%i",&g);
printf("Ingrece segundo numero, tercer fila, de izquierda a derecha:");
scanf("%i",&h);
printf("Ingrece tercer numero, tercer fila, de izquierda a derecha:");
scanf("%i",&i);
printf("%i %i %i:%i %i %i\n%i %i %i:%i %i %i\n%i %i %i:%i %i %i\n\n", a,b,c,j,k,l,d,e,f,m,n,o,g,h,i,p,q,r);
if (a==1&&b==0&&c==0&&d==0&&e==1&&f==0&&g==0&&h==0&&i==1)
{
printf("%i %i %i:%i %i %i\n%i %i %i:%i %i %i\n%i %i %i:%i %i %i", a,b,c,j,k,l,d,e,f,m,n,o,g,h,i,p,q,r);
}
else if(a!=1&&b!=0&&c!=0&&d!=0&&e!=1&&f!=0&&g!=0&&h!=0&&i!=1)
{	
clrscr();
int Función, a1, b1, c1, d1, e1, f1, g1, h1 ,i1, j1, k1, l1;
do
{
	clrscr();
	printf("Selecióne función:");
	printf("1.  F1-F2\n");
	printf("2.  F1-F3\n");
	printf("3.  F2-F1\n");
	printf("4.  F2-F3\n");
	printf("5.  F3-F1\n");
	printf("6.  F3-F2\n");
	printf("7.  F1+F2\n");
	printf("8.  F1+F3\n");
	printf("9.  F2+F1\n");
	printf("10. F2+F3\n");
	printf("11. F3+F1\n");
	pritnf("12. F3+F2\n");
	printf("13. Terminar\n");
	scanf("%i", &Función);
	switch(Función)
	{
		caso 1:
		a=a-d;
		b=b-e;
		c=c-f;
		j=j-m;
		k=k-n;
		l=l-o;
		printf("%i %i %i:%i %i %i\n%i %i %i:%i %i %i\n%i %i %i:%i %i %i", a,b,c,j,k,l,d,e,f,m,n,o,g,h,i,p,q,r),
}
}

[/PHP]


Ok so I'm w righting this program, it's to help me do inverse matrix (I don't know what the plural is.). Again, I know it's sloppy as heck, that's not the point. The problem comes at the bottom, when I try to use "switch/break", obviously I'm not doing it right, can someone point me in the right direction, please.

---

### Post by SledgeHammer_999 on 2012-04-19
It's a simple mistake. You didn't delimit your last printf correctly. You put a ',' instead of a ';".

---

### Post by Vaphell on 2012-04-19
if it's for practical purposes, why reinvent the wheel?
can't you use let's say python with scipy/numpy?

---

### Post by rafaelcbf on 2012-04-19
> **SledgeHammer_999 said:**
> It's a simple mistake. You didn't delimit your last printf correctly. You put a ',' instead of a ';".

¬¬ Is should've paid more attention. But even so, is there a good tutorial somewhere out there to better understand switch/break and while?

---

### Post by rafaelcbf on 2012-04-19
> **Vaphell said:**
> if it's for practical purposes, why reinvent the wheel?
can't you use let's say python with scipy/numpy?

I probably could, but yes, I'm doing it for practice, I just barely started learning about programming, I'm just doing it for myself.

---

### Post by Vaphell on 2012-04-19
in that case my advice would be 'stop what you are doing and read about *for* loops and arrays' :)
in programming recognizing occuring patterns and reusing code is key. Maybe initial results will come later due to the lack of practice, but at least the approach will be more scalable and easier to modify.

```
for( int row=1; row<=3; row++ )
{
  for( int col=1; col<=3; col++ )
    printf( "%i ", matrix[row][col]);
  printf("\n");
}
```
is easier on the eyes than the huge prinf oneliner
btw try not to mix C and C++ together (stdio.h is C, iostream is C++)

---

### Post by rafaelcbf on 2012-04-19
> **Vaphell said:**
> in that case my advice would be 'stop what you are doing and read about *for* loops and arrays' :)
in programming recognizing occuring patterns and reusing code is key. Maybe initial results will come later due to the lack of practice, but at least the approach will be more scalable and easier to modify.

btw try not to mix C and C++ together (stdio.h is C, iostream is C++)

what could I use in place of <stdio.h> or would it be enough to just use <iostream>?

I know I could have used for at the beginning, the thing is, With for, I don't know how to make it print out the specific thing I want it to say, it would just print out the same sentence 9 times.

---

### Post by Vaphell on 2012-04-19
stdio.h features are covered by iostream, io=input/output
that's not a big deal though if you do use stdio.h at least for now, on the other hand not using loops in case of matrices is criminal ;-)

---

### Post by rafaelcbf on 2012-04-19
> **Vaphell said:**
> stdio.h features are covered by iostream, io=input/output
that's not a big deal though if you do use stdio.h at least for now, on the other hand not using loops in case of matrices is criminal ;-)

¬¬ Hmmm? Sounds like you're trying to send a secret message, maybe I haven't learned the true power of for. I'll look into it ASAP. Thank you.

---

### Post by SledgeHammer_999 on 2012-04-19
@rafaelcbf

IMHO the best C++ online tutorial is this -> [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by rafaelcbf on 2012-04-19
> **SledgeHammer_999 said:**
> @rafaelcbf

IMHO the best C++ online tutorial is this -> [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Thank you, I guess that's it for now.

---

