---
title: "Function  to count float* in C"
date: 2015-12-21
forum: Programming Talk
---

### Post by udragu on 2015-12-21
Hello all!

May be stupid question but, I've written such code
```

int count_int(int *array)
{
    int i = 0;

    while( *(array + i) != 0xff)
    {  
        i++;
    }

    return i;
}


int main()
{
   int arr[] = {1,2,3,4,5,6,7,8,9, 0xff};
   int size = count_int(arr);
   printf("N=%d", size);
   return 0;
}

```
It works fine. But what should I do if I want to count float, not only Int. How should I change my code?
What I should use instead of 0xff?

Thanks a lot!

---

### Post by DaviesX on 2015-12-21
Homework?

---

### Post by udragu on 2015-12-22
just curiosity

---

### Post by matt_symes on 2015-12-22
Hi

In your example change your int to float. 

As for using a value in the set space as the terminator - in your case 0xff in the set of valid integers - and what to use the in case of floats, this is not the way to do it.

Get the size of the array and divide by the size of one member the that array. That way you lose the terminating value from the array (0xff - the last member) and you don't lose one member of your set as the terminator.

Remember to check the array is not an empty set.

BTW: stdio.h is your friend :)

Kind regards

---

### Post by matt_symes on 2015-12-22
Hi

I'll expand at bit now i have more time. Take a look at this contrived example:

```
matthew-xu-16-04:/home/matthew:0 % cat test.c            
#include <stdio.h>

int main()
{
   {
        float arr[] = {1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0};
        int count = sizeof(arr)/ sizeof(arr[0]);
        printf("F=%d\n", count);
   }

   {
        int arr[] = {1,2,3};
        int count = sizeof(arr)/ sizeof(arr[0]);
        printf("I=%d\n", count);
   }

   {
        unsigned char arr[] = {1,2,3,4,5,6};
        int count = sizeof(arr)/ sizeof(arr[0]);
        printf("C=%d\n", count);
   }

   {   
        short arr[] = {-10,2};
        int count = sizeof(arr)/ sizeof(arr[0]);
        printf("S=%d\n", count);
   }

   return 0;
}
matthew-xu-16-04:/home/matthew:0 %
```

..and the result:

```

matthew-xu-16-04:/home/matthew:0 % gcc test.c -o test.out
matthew-xu-16-04:/home/matthew:0 % ./test.out            
F=9
I=3
C=6
S=2
matthew-xu-16-04:/home/matthew:0 
```

Using *magic numbers*, such as 0xff in your example, is a bad programming paradigm. Avoid them if you can. As a minimum, #define them or use a const or enumeration in c++ to give them a useful name that other developers or you, at a later date, will understand.

Kind regards

---

### Post by udragu on 2015-12-23
Thanks for reply!

I understand  - the best way is to take ration from sizeof(arr)/ sizeof(arr[0]);
But how to be in case with function ? Is there any method to do it inside function's body?

---

### Post by matt_symes on 2015-12-23
This is a homework assignment.

Thread closed.

---

