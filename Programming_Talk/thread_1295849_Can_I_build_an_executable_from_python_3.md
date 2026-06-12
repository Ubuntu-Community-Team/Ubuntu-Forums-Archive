---
title: "Can I build an executable from python 3???"
date: 2009-10-20
forum: Programming Talk
---

### Post by Ricardi on 2009-10-20
I google it and i found solution like py2exe; but it doesnt work in python 3 some alternative, can i do it manually???, they are simple codes.

---

### Post by snova on 2009-10-20
> **Ricardi said:**
> I google it and i found solution like py2exe; but it doesnt work in python 3 some alternative, can i do it manually???, they are simple codes.

Then why are you using Python 3? It breaks compatibility and as such tools written for 2.x are not available, including py2exe.

Also, what do you mean by "manually"?

---

### Post by SunSpyda on 2009-10-20
^ Because Python 3 is the better language?

I found this. It may or may not work. It supposidly translated Python 3 to Python 2, so you can then run py2exe on it.
[http://bitbucket.org/amentajo/lib3to2/](http://bitbucket.org/amentajo/lib3to2/)

^ Again, i just found it, & i haven't used it, so use it at your own risk.

---

### Post by snova on 2009-10-20
> **SunSpyda said:**
> ^ Because Python 3 is the better language?

Not really. The language itself has some improvements, but there is still relatively little third party support (a rather big problem, as that includes things like GUIs), and 2.x will be improved for years to come. 2.6 is current, and 2.7 is in development.

> I found this. It may or may not work. It supposidly translated Python 3 to Python 2, so you can then run py2exe on it.
[http://bitbucket.org/amentajo/lib3to2/](http://bitbucket.org/amentajo/lib3to2/)

Then why write Py3K code in the first place?

---

### Post by Ricardi on 2009-10-20
ty for the answer, i will test [http://bitbucket.org/amentajo/lib3to2/](http://bitbucket.org/amentajo/lib3to2/)

but now i rewrote my code in python 2.6 and however i get some errors when i execute it and i think is annoying, for the size of the files (libraries, interpreters etc) and i only use a simple plot... so i think is more easy to translate it to c or c++ but i'm beginner programming.

someone to help me to translate it from python to c or some language easy to compile in windows???.

```
import numpy
import pylab
n=80;
t=1;
f=2;
w=2*numpy.pi*f;
i=1;
res=0;
f=[];
x2=[];
while t<=2:
    while i<=n:
        res=res+(1/i)*numpy.sin(i*w*t);
        i=i+2;
    f.append((4/numpy.pi)*res)
    x2.append(t);
    i=1;
    t=t+.01;
    res=0
    
pylab.plot(x2, f,'r--')
pylab.xlabel('T/2')
pylab.ylabel('F(t)')
pylab.title('Graficando una Serie de Fourier')
pylab.grid(True)
pylab.savefig('simple_plot')
pylab.show()
```i did this, but i don't know how to define lists and while loops and append data to some variable

```
#include <stdio.h>
#define pi 3.14159f
int main(void)
{
float n = 0.0f;
float f = 0.0f;
float w = 0.0f;
float i = 0.0f;
float res = 0.0f;
float x = 1.0f;
printf("N=");
scanf("%f", &n);
printf("F=");
scanf("%f", &f);
w=2*pi*f;
printf("W= %f\n", w);
  return 0;
}
```and in c float is "decimal" numbers, cause in python 3 when i did some operation with decimal it give me the same result of calculator and in python 2 it didnt happen and give wrong results.

---

### Post by hessiess on 2009-10-20
> **Ricardi said:**
> ty for the answer, i will test [http://bitbucket.org/amentajo/lib3to2/](http://bitbucket.org/amentajo/lib3to2/)

but now i rewrote my code in python 2.6 and however i get some errors when i execute it and i think is annoying, for the size of the files (libraries, interpreters etc) and i only use a simple plot... so i think is more easy to translate it to c or c++ but i'm beginner programming.

someone to help me to translate it from python to c or some language easy to compile in windows???.

```
import numpy
import pylab
n=80;
t=1;
f=2;
w=2*numpy.pi*f;
i=1;
res=0;
f=[];
x2=[];
while t<=2:
    while i<=n:
        res=res+(1/i)*numpy.sin(i*w*t);
        i=i+2;
    f.append((4/numpy.pi)*res)
    x2.append(t);
    i=1;
    t=t+.01;
    res=0
    
pylab.plot(x2, f,'r--')
pylab.xlabel('T/2')
pylab.ylabel('F(t)')
pylab.title('Graficando una Serie de Fourier')
pylab.grid(True)
pylab.savefig('simple_plot')
pylab.show()
```i did this, but i don't know how to define lists and while loops and append data to some variable

```
#include <stdio.h>
#define pi 3.14159f
int main(void)
{
float n = 0.0f;
float f = 0.0f;
float w = 0.0f;
float i = 0.0f;
float res = 0.0f;
float x = 1.0f;
printf("N=");
scanf("%f", &n);
printf("F=");
scanf("%f", &f);
w=2*pi*f;
printf("W= %f\n", w);
  return 0;
}
```and in c float is "decimal" numbers, cause in python 3 when i did some operation with decimal it give me the same result of calculator and in python 2 it didnt happen and give wrong results.

C does not have lists as a language feature, though you can implement them quite easely with structures and pointers (google it). Or just use C++ std::list or std::vector.

While loops are basically the same
```

while(<some logical expression>)
{
    <do this untill experession evaluates to false>
}

```

---

### Post by Ricardi on 2009-10-21
> **hessiess said:**
> C does not have lists as a language feature, though you can implement them quite easely with structures and pointers (google it). Or just use C++ std::list or std::vector.

While loops are basically the same
```

while(<some logical expression>)
{
    <do this untill experession evaluates to false>
}

```

ty for help, i continued reading and finally i used arrays

check it

```
#include <stdio.h>
#include <math.h>
int main(void)

{
int n = 0;
int z = 0;
float f = 0.0f;
float t = 0.0f;
float w = 0.0f;
int i = 1.0;
int zz = 100;
float res = 0.0f;
float x = 1.0f;
printf("Programa que grafica una Serie de Forier\n");
printf("N=");
scanf("%d", &n);
printf("F=");
scanf("%f", &f);
w=2*M_PI*f;
printf("W= %f\n", w);
float ft[zz-1];
float x2[zz-1];

while(t<zz)
{
    while(i<n)
    {
        res=res+(1/i) * sin (i*w*t);
        i=i+2;
    }
    ft[z]=(4/M_PI)*res;
    x2[z]=t;
    i=1;
    t=t+1;
    res=0;
    z=z+1;
}
for (z=0;z < zz; z++)
{
printf("%f\n",ft[z]);
printf("%f\n",x2[z]);
}
return 0;
}
```but now i want to plot x2,ft

i google it and found koolplot, plplot but i dont understand how it works with arrays

---

### Post by Marco A on 2009-10-21
.

---

### Post by hessiess on 2009-10-21
```

float ft[zz-1];
float x2[zz-1];

```

This will only work if the value of zz can be determined at compile time, which it currently can, however if you allowed the user to input this value you would have to use
malloc instead.

```

float *ft = malloc(sizeof(float) * (zz - 1));
float *x2 = malloc(sizeof(float) * (zz - 1));

--at end of program
free(ft);
free(x2);

```

---

### Post by Ricardi on 2009-10-21
ty for the tip, i didnt know it... =)

now im searching for a C plot library (easy) =P...

do you recommend someone?

---

### Post by cascade9 on 2009-10-21
> **Ricardi said:**
> ty for the answer, i will test [http://bitbucket.org/amentajo/lib3to2/](http://bitbucket.org/amentajo/lib3to2/)

but now i rewrote my code in python 2.6 and however i get some errors when i execute it and i think is annoying, for the size of the files (libraries, interpreters etc) and i only use a simple plot... so i think is more easy to translate it to c or c++ but i'm beginner programming.

someone to help me to translate it from python to c or some language easy to compile in windows???.


Forgive my ignorance, but why? I've run python apps under windows fine.

---

### Post by Ricardi on 2009-10-21
> **cascade9 said:**
> Forgive my ignorance, but why? I've run python apps under windows fine.

> but now i rewrote my code in python 2.6 and however i get some errors when i execute it and i think is annoying, for the size of the files (libraries, interpreters etc) and i only use a simple plot... so i think is more easy to translate it to c or c++ but i'm beginner programming.yes python works perfectly on windows, but sometimes i need to execute some programs in pcs without interprete installed


nothing about pplotting libraries? in c?

---

