---
title: "Problem accessing the elements of a 2-D array in C"
date: 2007-11-24
forum: Programming Talk
---

### Post by fredscripts on 2007-11-24
Hi!

I've been asked to do a program to multiply two matrixes, whose dimensions are entered by the user, so I must use pointers.


I'm starting step by step because for me pointers are quite difficult. Firtst, I need to declare a matrix of floats, (with a doble pointer) and get used to work with it (fill it, print it and so). Here is my code:

```
float **m
int rows,columns;
int i,j,offset=0; 
float filler=0.0;

printf("Enter the rows of the matrix:  ");
scanf("%d",&rows);

printf("Enter the columns of the matrix: ");
scanf("%d",&columns);

m = (float **) malloc(rows*columns*sizeof(float));

for (i=0;i<rows;i++) {
         for (j=0;j<columns;j++) {
                    **(m+offset) = filler;
                    offset++;
                    filler++;
        }
}
```

Then, I supose I've filled the matrix with consecutive numbers. Of course I would do it with scanf's, so the user fills the matrix, that's just for testing.

Te problem appears when I want to print the matrix I've filled. Extrange (for me) things happens when I try something like:

```

i=0;
j=0;
offset=0;
for (i=0;i<rows;i++) {
         for (j=0;j<columns;j++) {
                 printf("position %d %d apears %f \n",i,j,**(m+offset));
                 offset++;
        }
}
```


I do not receive the correct matrix I've filled before printed. I think I have to understand better the double pointers, because I do not access the elements in the right way. 

Could anyone help me understanding the double pointer stuff? Thank you very much!!!!

---

### Post by aks44 on 2007-11-24
Nevermind, you just edited your post and added the missing parts.

---

### Post by fredscripts on 2007-11-24
Yes, sorry I forgot to add the malloc part. But the problem is still there, when I print the matrix, did not appear the correct values :(

---

### Post by aks44 on 2007-11-24
A float** is a pointer to a pointer to float, ie. an array of pointers to float, ie. an array of arrays of float.

But what you're actually doing is indexing it as if it was an array of floats, ie. a float*, but still dereferencing the pointers twice.

Choose one way or another, but don't mix both... :p

---

### Post by fredscripts on 2007-11-24
Thanks for answering. Yes I realize I treat the **m like a single *m just indexing **(m+i) but I don't find out the right way of accessing the elements of a double point. I understand the meaning of it, but can't get into the solucion, I've tried with accessing with a single pointer like *(m+i) but stills gives me problems. 

Could you give me a little example of accessing the elements of a double pointer? (just a dummie example, I really want to lean the stuff :))


Thanks again!

---

### Post by aks44 on 2007-11-24
You have two solutions:

1) Keep your indexing as it is (ie. offset = column + (row * columns)) and use a simple array of floats instead of a float**
The problem with your current code is that you declare m and dereference it as an array of pointers to floats, but you allocate the memory and index it as if it was an array of floats.

2) If you really want to use an array of arrays, you gotta:
- allocate an array of *rows* float*
- for each item in that array, allocate an array of *columns* floats
(or you can put columns outermost and rows innermost if you wish, it doesn't really matter)


Hope this is clear enough.

---

### Post by geirha on 2007-11-24
You can't malloc a two dimentional array in one go. Your matrix is an array of rows, so you need to first malloc an array of arrays 
```
float **m;
m= malloc(rows*sizeof(float*));

```

Then iterate this array, and malloc each row:
```
m[i]= malloc(columns*sizeof(float));
```

now you can use m[i][j] to assign and read values from your matrix.

I find it easier to just use one-dimensional arrays though.

---

### Post by fredscripts on 2007-11-24
Thank you very much for answering. I'm gonna try it :)

---

### Post by fredscripts on 2007-11-25
Hi again, I did a little work on that but I found a problem again.

The code:

```
#include <stdio.h>
#include <alloc.h>
#include <stdlib.h>

main() {

	float **a;
	int fa,ca;
	int i,j;
	float aux=1.0;

	printf("enter rows of a: ");
	scanf("%d",&fa);

	printf("enter columns of a: ");
	scanf("%d",&ca);
	
	a= malloc(fa*sizeof(float*));
	
	for (i=0;i<fa;i++) {
		a[i]= malloc(ca*sizeof(float*));
	}
	
	i=0;
	for(i=0;i<fa;i++) {
		for(j=0;j<ca;j++) {
			a[i][j] = aux;
			aux++;
		}
	}
	
	i=0;
	j=0;
	
	for(i=0;i<fa;i++) {
		for(j=0;j<ca;j++) {
			printf("a[%d][%d]: %f\n",i,j,a[i][j]);
			
		}
	}
	
	return 0;

}
```

I thought I was the good way, but when I run it, and enter rows = 3 and columns = 3, it is supposed to print a[0][0] = 1.0, a[0][1] = 2.0,...a[2][2] = 9.0. But it don't exactly do it. It says that a[0][2] = 0.0 and a[1][2] =0.0. 

I know it's not easy to get started with pointers (even thought I like the phylosophie of them) , I've read the "Pointers and arrays" part of "The C Programming language" which is a fantastic book, and I thought I understand it quite well, but it's seems that not at all.

So, if only someone could help me a little with this. I really want to get used to pointers and understand them. Why this code acts the way it does?

Thanks you very much in advance!!

---

### Post by geirha on 2007-11-25
> **fredscripts said:**
> 
```

		a[i]= malloc(ca*sizeof(float[COLOR="Red"]*[/COLOR]));

```


You want an array of float here, not array of float*

EDIT: Also, make sure you free up those arrays you've malloced, typically in "opposite" order, like 
```
for (i...) free(a[i]);
free(a);
```
And you should also check if malloc returns NULL, which it will do if it was unable to allocate the memory, so exit or something if that happens.

---

### Post by fredscripts on 2007-11-25
Oh thanks! I didn't see that float*!  I've changed to float and it works perfect! Thanks for remembering me to free all the memory I completely forgot ! :)

Thank you very much!!!


By the way, I'm now doing a function to fill a matrix (and then will do another to print a matrix):

 
```
fillMatrix(int r,int c,float **m) {
	int i,j;
	
	for(i=0;i<r;i++) {
		for(j=0;j<c;j++) {
			printf("Enter element %d %d ",i,j);
			scanf("%f",m[i][j]);
			printf("\n");
		}
	}
	return 0;
}
```


The error (When the program is executed):

Enter element 0 0: floating point numbers not linked
Abnormal program termination


      


EDIT: There's definitely a problem with that scanf statement. If I fill the matrix with random numbers instead of asking with scanf it works perfectly. I'm kind of confused because I've always used scanf that ways and never had problems :S

---

### Post by fredscripts on 2007-11-25
Any suggestions about why can the scanf statement produces that error on that peace of code?:(

---

### Post by geirha on 2007-11-25
you are passing scanf a float, while what you want to do, is to pass the address of where it should store a float. (hint: &)

---

### Post by aks44 on 2007-11-25
Just as side note: functions implicitly returning an int are deprecated since 1999.

Bad:
```
main(void)
{
  return 0;
}
```

Good:
```
int main(void)
{
  return 0;
}
```


The same goes for your fillMatrix() function (which should really return void BTW, the int it returns is quite pointless).

---

### Post by stroyan on 2007-11-25
If you care about the speed with which your program runs then you should reconsider the implementation of a two dimensional array as an array of pointers to one dimensional arrays.  The "m[i][j]" source code to access through an array of pointers looks simpler.  But the pointer reference is actually much more expensive than computing an index into a one dimensional array with m[i*columns+j];  Multiplication and addition are faster than an extra memory indirection.

---

### Post by fredscripts on 2007-11-26
Thank you very much for your answers! very interesting the fact of not returning an int:). Also, I considered doing it considering a matrix  with a single pointer, but I thought that to understand more the pointer's world I would learn more using double pointers. Didn't know about the speed, so if I get the program done with double pointers I'm gonna do it with single's  :)

I still don't realize why I still get the "floating point formats not linked" error, even though I've corrected the code (I hope).
```

void fillMatrix(int r,int c,float **m) {
	int i,j;
	
	for(i=0;i<r;i++) {
		for(j=0;j<c;j++) {
			printf("Enter element %d %d ",i,j);
			scanf("%f",&m[i][j]);
			printf("\n");
		}
	}
}

```

Quite confusing behavior :S I've read information about scanf and I understand why needs an address and not a value (so I did when asking for the rows and columns of the matrix), so I give scanf the address of a float (&m[i][j],thanks for your answer geirha). 

So I know I'm being kind of tedious, but I would be very grateful if someone could suggest me an idea of what's going on with that.

Thanks again!

---

### Post by fredscripts on 2007-11-26
Hi!! I've found one solution to the problem! 
```

void fillMatrix(int r,int c,float **m) {
	int i,j;
	float num=0.0;
	for(i=0;i<r;i++) {
		for(j=0;j<c;j++) {
			printf("Enter element %d %d ",i,j);
			scanf("%f",&num);
			m[i][j] = num;
			printf("\n");
		}
	}
}
```

Now it works perfectly! Could anyone explain to me why this works and not the other way? I'm very curious with this :)

Thanks again!

---

### Post by smartbei on 2007-11-26
Not sure if this would solve the problem, but you may need parenthases to indicate to the compiler what you want the & to apply to. That is, try this:
```

scanf("%f",&(m[i][j]));

```

What the compiler might have been doing is (&m)[i][j] which is quite undefined behaviour.

---

### Post by stroyan on 2007-11-26
That "floating point formats not linked" is new to me.  It is a problem with Borland Turbo-C trying to optimize away the linking of floating point scanf code when it does not detect operations involving floating point numbers.  It is question 14.13 at
[http://www.faqs.org/faqs/C-faq/abridged/](http://www.faqs.org/faqs/C-faq/abridged/)

Your working version is probably triggering the linking of floating point scanf libraries by the assignment of "num = 0.0";

It should not be an issue with ubuntu and gcc.  Both versions of your fillMatrix function are valid C.

---

