---
title: "Re: cos() function not working on gcc (C language)"
date: 2012-10-21
forum: Programming Talk
---

### Post by ashrithhcs on 2012-10-21
**gcc -lm filename.c doesn't seem to work here. I have posted the code below, I have included math.h library and have sin() and cos() funstions in fft() function. Please help!**

```

#include <stdio.h>
#include <math.h>
#define e 2.7182818284590452353602875

struct stud{
       double real,value,complex;
       };
typedef struct stud create;
int n;

void reverse(create x[n])
{
create x1[n];
int i=1,count=0,cnt=1,p,j,num=n,k=0,wi;
while(i!=n)
{
i=i*2;
count++;
}

for(i=1;i<count;i++)
{
for(p=0;p<cnt;p++)
{
k=0;
for(j=0;j<num*(p);j++,k++){}
if(p==0)j=k=0;
for(;j<num*(p+1);j++)
{
if(k>=(p+1)*num)k=k-num+1;
x1[j].real=x[k].real;
x1[j].value=x[k].value;
k+=2;
}
}
cnt*=2;
num/=2;
for(j=0;j<n;j++)
{
x[j].real=x1[j].real;
x[j].value=x1[j].value;
}
}}

void fft(create x[n])
{
create x1[n];
double constant=(2*3.14)/n,omg;
int k,i;
for(k=0;k<n;k++)
x1[k].real=x1[k].complex=0;

for(k=0;k<n;k++)
for(i=0;i<n;i++)
{
omg=constant*k*x[i].value;
x1[k].real=x1[k].real+x[i].real*(cos(omg));
x1[k].complex=x1[k].complex-x[i].real*(sin(omg));
}
for(k=0;k<n;k++)
{x[k].real=x1[k].real;
x[k].complex=x1[k].complex;}
}

int main()
{
int p;
printf("Enter the DIT FFT point\n");
scanf("%d",&n);
create x[n];
    
printf("Enter %d real and complex inputs\n",n);
for(p=0;p<n;p++)
{
scanf("%lf",&x[p].real);
x[p].value=p;
}

reverse(x);
fft(x);
for(p=0;p<n;p++)
printf("%lf+%lfj\n",x[p].real,x[p].complex);
return 0;
}

```

**Error Shown**
[noparse]/tmp/cchV7CWV.o: In function `fft':
fft.c:(.text+0x3c0): undefined reference to `cos'
fft.c:(.text+0x411): undefined reference to `sin'
collect2: ld returned 1 exit status[/noparse]
****

---

### Post by sisco311 on 2012-10-21
Please don't bump old threads.

Post moved to its own thread. 

Original one is here: [http://ubuntuforums.org/showthread.php?t=1445242](http://ubuntuforums.org/showthread.php?t=1445242)

---

### Post by trent.josephsen on 2012-10-21
Indentation, man. Use it.

And put -lm at the end of the command line instead of between the command and the source file. It should work that way, although both variations work for me (not Ubuntu).

---

