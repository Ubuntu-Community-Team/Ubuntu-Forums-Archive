---
title: "Weird GCC error"
date: 2008-04-06
forum: Packaging and Compiling Programs
---

### Post by jesse_adkins on 2008-04-06
I was messing around one day, and I got this error message...

///
test.c:8 error: called object 'x' is not a function.
///

From this code...

///
struct x {
    int x;
};

void x(int v)
{
    struct x x;
    x(x.x);
}
///

I'm no expert at C, nor would I be caught with this in 'real code'. However, this one seems curious to me, since GCC doesn't give any errors about the function sharing a name with a variable and/or a struct. Am I just overreacting, or could this be a bug of some sort?

gcc 4.2.3, Ubuntu 8.04 (Hardy)

---

### Post by Zugzwang on 2008-04-06
Looks correct to me as you can re-define variable names for inner blocks ({...}):

[PHP]
#include "stdio.h"

int main() {
	int i;
	for (i=0;i<3;i++) {
		int i;
		for (i=0;i<4;i++) {
			printf("Hello from no. %i\n",i);
		}
	}
}
[/PHP]
The code above execute in the same way as it would have done if the for-variable of the outer loop was "j".

Now being able to re-define (or overload? Don't know the actual correct term here) a function name with a variable just seems straight-forward to me since you define the variable x *inside* such a block.

Anyway, you should have written this in the "Programming Talk" section. ;-)

---

