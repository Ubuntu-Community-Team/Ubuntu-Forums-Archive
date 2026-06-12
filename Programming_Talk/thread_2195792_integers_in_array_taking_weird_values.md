---
title: "integers in array taking weird values"
date: 2013-12-26
forum: Programming Talk
---

### Post by wingnut2626 on 2013-12-26
here is the code this time (please bear with me i am trying to learn C)

```
#include <stdio.h>


int main(){


    int nbr;
    int test_array[] = {1,2,3,4,5,6,7,8,9};
    int *pointer_to_test_array;


    int empty_array[80];
    int *pointer_to_empty_array;


        pointer_to_test_array = test_array;
	pointer_to_empty_array = empty_array;
	
	void int_copy(int *ptrA, int *ptrB, int nbr){
	  int number = 0;
	  for(number = 0; number < nbr; number++){
	    *(ptrA + number) = *(ptrB + number);
	    printf("copying %d to pointerB\n", *(ptrA + number));
	    printf("actual array value is %d\n", test_array[number]);
	    printf("1st item of array is %d\n", test_array[0]);
	    getchar();
			
			
		}
			
		}
		
		printf("What is the number to copy? ");
		scanf("%d", &nbr);
		printf("%d\n",nbr);
		getchar();
		int_copy(pointer_to_test_array,pointer_to_empty_array,nbr);
		
		printf("%d\n",*pointer_to_empty_array);
		
	
	
	




    return 0;
}



```

```
Instead of copying the values to the empty set i am getting this:

What is the number to copy? 4
4
copying -67367040 to pointerB
actual array value is -67367040
1st item of array is -67367040


copying 32767 to pointerB
actual array value is 32767
1st item of array is -67367040


copying -1427215864 to pointerB
actual array value is -1427215864
1st item of array is -67367040


copying 32764 to pointerB
actual array value is 32764
1st item of array is -67367040


-67367040

```

Any ideas of what is going on?  I dont want the direct answer, just can someone point me in the right direction?

---

### Post by wingnut2626 on 2013-12-26
i know the nested function is wrong, this is some code that i wrote before i was informed of that

---

### Post by Bachstelze on 2013-12-26
I can't immediately see the problem with your code, other than that it is terribly written. After rewriting it correctly, I do not have this problem.

```
firas@aoba ~ % cat test.c
#include <stdio.h>

int test_array[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };

void int_copy(int *ptrA, int *ptrB, int nbr)
{
    int number = 0;
    for (number = 0; number < nbr; number++) {
        ptrA[number] = ptrB[number];
        printf("copying %d to pointerB\n", ptrA[number]);
        printf("actual array value is %d\n", test_array[number]);
        printf("1st item of array is %d\n", test_array[0]);
        getchar();
    }
}


int main(void)
{
    int nbr;
    int *pointer_to_test_array;
    int empty_array[80];
    int *pointer_to_empty_array;

    pointer_to_test_array = test_array;
    pointer_to_empty_array = empty_array;

    printf("What is the number to copy? ");
    scanf("%d", &nbr);
    printf("%d\n", nbr);
    getchar();
    int_copy(pointer_to_test_array, pointer_to_empty_array, nbr);

    printf("%d\n", *pointer_to_empty_array);
    return 0;
}
firas@aoba ~ % cc -ansi -pedantic -Wall -Wextra -o test test.c 
firas@aoba ~ % ./test 
What is the number to copy? 4
4
copying 0 to pointerB
actual array value is 0
1st item of array is 0
^C
firas@aoba ~ % 

```

---

### Post by wingnut2626 on 2013-12-26
oh yeah I know it was badly written.  I'm just curious why the output was like that...

---

### Post by spjackson on 2013-12-26
> **wingnut2626 said:**
> oh yeah I know it was badly written.  I'm just curious why the output was like that...
Instead of ptrA and ptrB, why not use some meaningful names such as from and to? When I look at the function call, I assume you are copying from the 1st parameter (pointer_to_test_array) to the second parameter (pointer_to_empty_array). The function declaration (and later its definition) provide no clues about which way we are copying. The loop body is copying from the 2nd parameter (ptrB) to the 1st (ptrA), i.e. the other way round.

---

### Post by ofnuts on 2013-12-26
> **wingnut2626 said:**
> oh yeah I know it was badly written.  I'm just curious why the output was like that...

If the code were well written, you wouldn't be curious, you would know :) Believe this somewhat seasoned programmer, clean code is never a waste of time, even for quick and dirty jobs.

---

### Post by wingnut2626 on 2013-12-26
[SIZE=1]Got it.  Thank you for the advice and i will clean c[/SIZE][SIZE=1]ode up before i post in the future.[/SIZE]

---

