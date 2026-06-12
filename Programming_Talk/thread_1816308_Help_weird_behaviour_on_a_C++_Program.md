---
title: "Help weird behaviour on a C++ Program"
date: 2011-08-01
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-08-01
Hi everybody And thanks for all

I was trying to make a program that can output the greater and lesser number introduced by the user even at ramdom order, without organizing the whole array But...

I can only output Lesser or Greater not both:


```
const int MAX_ELEM = 10;

int Lista[MAX_ELEM], i, j, Valor, MValor;

for(i = 0; i <= 9; i ++)
{
	
cout << "Introduce el valor numero " << i + 1 << ": ";	
cin >> Lista[i];	

}

cin.ignore();
	
for(i = 0; i <= 9; i ++)	
{
for(j = i + 1; j <= 9; j ++)
{	
if(Lista[i] < Lista[j])	
{

Lista[j] = Lista[i];
	
Valor = Lista[j];	
	
}	


else

{

Lista[i] = Lista[j];
	
Valor = Lista[j];	
	
}


if(Lista[i] > Lista[j])	
{

Lista[j] = Lista[i];
	
MValor = Lista[j];	
	
}	


else

{

Lista[i] = Lista[j];
	
MValor = Lista[j];	
	
}


}
}


```
	

Even if I inlclude the statement for that, it seems like it gets mess up on some part...

Please help this was running me mad the whole morning

---

### Post by F.G. on 2011-08-01
i dont understand the question (also you might want a c++ forum instead).
what do you want the program to do??

---

### Post by Bachstelze on 2011-08-01
If you don't want to reorganise the whole array, why are you changing values in it?

```
min = max = t[0];
for (int i=1; i<lt; i++) {
    if (t[i] > max) {
        max = t[i];
    } else if (t[i] < min) {
        min = t[i];
    }
}
```

---

### Post by dwhitney67 on 2011-08-01
And if the array is not required, just check for min/max as the user inputs the values:
```

#include <iostream>
#include <algorithm>
#include <limits>

int main()
{
   int min = std::numeric_limits<int>::max();
   int max = std::numeric_limits<int>::min();

   for (int i = 0; i < 10; ++i)
   {
      int numero;
      std::cout << "Introduce el valor numero: ";
      std::cin  >> numero;

      min = std::min(min, numero);
      max = std::max(max, numero);
   }

   std::cout << "El numero mas pequeno es: " << min << std::endl;
   std::cout << "El numero mas grande es : " << max << std::endl;
}

```

Alternatively, use an STL set if you wish to retain the values that are inputted (note, only unique values are retained; use a multiset to retain all values):
```

#include <iostream>
#include <set>

int main()
{
   std::set<int> lista;

   for (int i = 0; i < 10; ++i)
   {
      int numero;
      std::cout << "Introduce el valor numero: ";
      std::cin  >> numero;

      lista.insert(numero);
   }

   std::cout << "El numero mas pequeno es: " << *lista.begin() << std::endl;
   std::cout << "El numero mas grande es : " << *lista.rbegin() << std::endl;
}

```

---

