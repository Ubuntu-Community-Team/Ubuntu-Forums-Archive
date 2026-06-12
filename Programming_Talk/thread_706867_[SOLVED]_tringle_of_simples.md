---
title: "[SOLVED] tringle of simples?"
date: 2008-02-24
forum: Programming Talk
---

### Post by chris200x9 on 2008-02-24
in c++ how would I make a triangle of symbols I have one side but it's not  fully done. 


```
 int counter;
int number;
char ch;
cout << "enter a number";
cin >> number;
ch = '*';
counter = 0;
while ( counter < number )
{
cout << setw(number - counter);
cout << ch << endl;
counter = counter + 1;
}
 
 
 
 
	return 0;
}

```

it is supposed to be a solid triangle, or rather a pyramid.

---

### Post by matja on 2008-02-25
Hi Chris200x9,

Here's _one_ solution using std::string:

```

#include <iostream>
#include <string>

void
print_triangle(int height, char symbol)
{

   std::string layer(1, symbol);
   for(int indent = height - 1; indent >= 0; --indent) {

      std::cout << std::string(indent, ' ') << layer << '\n';
      layer.append(2, symbol);

   }

}

```

Hope it helps!

---

### Post by chris200x9 on 2008-02-26
thanks!

---

