---
title: "about templates"
date: 2008-06-06
forum: Programming Talk
---

### Post by lixx on 2008-06-06
Im quite baffled with the code I'm dealing with:

```

template <typename T>
int getSize(T *arrayname) {
    return sizeof(arrayname)/sizeof(T);
}
....
int test[16];
cout << sizeof(test) << endl;

```

On my computer, it displays 1. Upon further tracing
of variables, sizeof(arrayname) is equal to 4 and also
sizeof(T). So 4/4=1. So I can infer that the int size
on my pc is about 4 bytes. Does templates really
doesn't work with sizeof???

---

### Post by StOoZ on 2008-06-06
what u are doing is basically asking for the size of the type of the pointer.... it wont give u 64 in this case (if int = 4 byte).
it wont work even without templates... this is because its a pointer.

---

### Post by JupiterV2 on 2008-06-06
The size of a pointer is static so (example in C):
[PHP]#include <stdio.h>
#include <stdlib.h>

int main()
{
	int* x;
	
	printf("sizeof(x)=%d\n", sizeof(x));
	
	x = calloc(10, sizeof(int));
	
	printf("sizeof(x)=%d\n", sizeof(x));
	
	return 0;
}[/PHP]

...will always return the same value no matter the contents of x nor the amount of memory allocated to x (in my case, 4 bytes). The only way I know to retain the number of elements in an array is to store it in some fashion (example in C):
[PHP]#include <stdio.h>
#include <stdlib.h>

typedef struct
{
	int length;
	int* array;
} array_t;

int main()
{
	array_t my_array;
	
	my_array.length = 5;
	my_array.array = (int*) calloc(my_array.length, sizeof(int));
	
	printf("The size of my_array is %d.\n", my_array.length);
	
	return 0;
}[/PHP]

In C++, though, it's typically better practice to use one of the STL types like a vector rather than an array (example in C++):
[PHP]#include <iostream>
#include <vector>

int main()
{
  std::vector<int> my_int_array;
  
  for(int x = 0; x < 5; x++) my_int_array.push_back(x);
  
  std::cout << "Size of my array: " << my_int_array.size() << std::endl;
  
  return 0;
}[/PHP]

---

