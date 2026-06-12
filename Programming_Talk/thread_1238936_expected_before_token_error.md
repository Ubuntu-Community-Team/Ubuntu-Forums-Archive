---
title: "expected before token error"
date: 2009-08-13
forum: Programming Talk
---

### Post by studybuddy09 on 2009-08-13
I am getting the following error ,
 [COLOR=Black]
[COLOR=DarkRed]expected ')' before '[' token[/COLOR][/COLOR]
during the compilation of the following line,

[COLOR=DarkRed]int binsrch(a[n],n,x)[/COLOR]
which is a function definition.

whats my mistake?

---

### Post by Krupski on 2009-08-13
> **studybuddy09 said:**
> I am getting the following error ,
 [COLOR=Black]
[COLOR=DarkRed]expected ')' before '[' token[/COLOR][/COLOR]
during the compilation of the following line,

[COLOR=DarkRed]int binsrch(a[n],n,x)[/COLOR]
which is a function definition.

whats my mistake?

No semicolon after the function call?

Should be:

```

int binsrch(a[n],n,x)[COLOR="Red"]**;**[/COLOR]

```


-- Roger

---

### Post by nvteighen on 2009-08-13
Er... what are you trying to do, call a function or declare it in a header? Apart from the lacking semicolon, there might be other errors:

If you're calling the function, the **int** makes no sense.

If your declaring the function in a header, then you have to provide the arguments' data types.

---

### Post by studybuddy09 on 2009-08-13
Thats the function definition where i think, semicolon does not appear as per the syntax,
 To be more clear here is a part of the code,

[COLOR=DarkRed]#include<stdio.h>
main()
{
int n,i,x,ans;
printf("ENTER THE NO.OF ELEMENTS\n");
scanf("%d",&n);
int a[n];
prinf("ENTER THE ELEMENTS\n");
for(i=0;i<=n-1;i++)
{
scanf("%d",&a[n]);
}
printf("ENTER THE ELEMENT TO BE SEARCHED FOR\n");
scanf("%d",&x);
int binsrch(int,int,int); // function prototype
ans=binsrc(a[n],n,x);  // function call
printf("FINAL RESULT=\t",ans);
}

int binsrch(a[n],n,x) // function definition<error>
{
[/COLOR](remaining code)
[COLOR=DarkRed]}[/COLOR]

is there any mistake in the code for which it gives the error??

---

### Post by Habbit on 2009-08-13
The function definition is wrong. You need to state the types of the arguments, like "int f(double x, int y)" instead of just the parameter names. Furthermore, the syntax "T a[n]" in a parameter specification tells the compiler that the function  takes a fixed-length array of n elements of type T, but your prototype and the actual call shows that you try to pass it a _single_ element of type int.

---

### Post by studybuddy09 on 2009-08-14
Thanks a lot to all of you ...the error got cleared.

---

