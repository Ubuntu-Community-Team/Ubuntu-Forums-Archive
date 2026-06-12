---
title: "Why does this happen?"
date: 2008-06-28
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-06-28
Here's my code. It attempts to sort an array (using a selection sort) by passing it into the selection_sort function along with it's length. However, I get the following error:
```

/tmp/cc4HOdzl.o: In function `main':
selection sort.cpp:(.text+0x26f): undefined reference to `selection_sort(int, int)'
collect2: ld returned 1 exit status
Compilation failed.

```
It's worth mentioning that it compiles fine. The failure occurs at the build.

[PHP]
#include <iostream>
using namespace std;

#define LENGTH 5

void selection_sort(int, int);

int main(){
	int array[LENGTH];

	for (int index = 0; index <= LENGTH; index++){
		cout << "Enter a number: ";
		cin >> array[index];
	}
	
	selection_sort(array[LENGTH], LENGTH);
	
	for (int index = 0; index <= LENGTH; index++){
		cout << array[index] << endl;
	}
	
	return 0;
}

void selection_sort(int input_array[], int input_size){
	int i, j;
	int small, temp;
	
	for (i = input_size - 1; i > 0; i--){
		small = 0;
		
		for (j = 1; j <= i; j++){
			if (input_array[j] < input_array[small]){
				small = j;
			}
		}
		temp = input_array[small];
		input_array[small] = input_array[i];
		input_array[i] = temp;
	}
}
[/PHP]

---

### Post by LaRoza on 2008-06-28
> **Sinkingships7 said:**
> Here's my code. It attempts to sort an array (using a selection sort) by passing it into the selection_sort function along with it's length. However, I get the following error:

It's worth mentioning that it compiles fine. The failure occurs at the build.


Because there is no function "selection_sort(int, int)" defined.

---

### Post by Sinkingships7 on 2008-06-28
I knew it meant that, but as far as I can tell, it's defined just fine. Prototype and all. Is there something I'm missing? Help me out a bit?

---

### Post by LaRoza on 2008-06-28
> **Sinkingships7 said:**
> I knew it meant that, but as far as I can tell, it's defined just fine. Prototype and all. Is there something I'm missing? Help me out a bit?

int, int isn't the same as int[], int which is what it is. (You'll alse see some more errors once you fix that, but at least it won't be that error ;))

---

### Post by Sinkingships7 on 2008-06-28
> **LaRoza said:**
> int, int isn't the same as int[], int which is what it is. (You'll alse see some more errors once you fix that, but at least it won't be that error ;))

Well, that was fun. :lolflag:

On to fix the other errors -_-

---

