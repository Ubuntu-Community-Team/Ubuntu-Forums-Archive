---
title: "expected primary-expression with unsigned arr[4]"
date: 2009-07-05
forum: Programming Talk
---

### Post by gyppo on 2009-07-05
While I can write:

```
unsigned int null, small, full;
    null=0x0000u;
    small=0x000au;
    full=0xffffu;
```and have it compile no problem, and also:

```
unsigned int grid[4]={0x0000u,0x000au,0xffffu,0x1111u};

```if I try:

```
unsigned int grid[4];
grid={0x0000u,0x000au,0xffffu,0x1111u};

```I get compilation errors:
```

ints.c:26: error: expected primary-expression before ‘{’ token
ints.c:26: error: expected `;' before ‘{’ token
```why? I'm using g++.

---

### Post by MadCow108 on 2009-07-05
it is not allowed to assign values to an array in c/c++

unsigned int grid[4]={0x0000u,0x000au,0xffffu,0x1111u};
this is a declaration no assignment.

whereas
unsigned int grid[4];
grid={0x0000u,0x000au,0xffffu,0x1111u};
tries to assign the list to an already declared array and is not allowed

---

### Post by gyppo on 2009-07-05
Thanks.

So if I want to change the entire array later in the program, do I have to do it element by element?

---

### Post by lisati on 2009-07-05
> **gyppo said:**
> Thanks.

So if I want to change the entire array later in the program, do I have to do it element by element?

That's the way I've had to do it in most of the programming languages I've used: either use the initialization as part of the declaration - illustrated by MadCow108 - or find some way to work through the array element by element.

---

### Post by gyppo on 2009-07-05
Ok, thanks. That's a little annoying, as I'm used to python's list comprehensions, but I suppose that's what I expected when I decided to learn C.

Thanks again.

---

### Post by MadCow108 on 2009-07-05
hehe going from python to c can be very annoying
c is incredibly stupid :)

just something you'll probably stumble over:
you mostly need to save the size of your array and pass it to whatever functions which works with the array
the sizeof operator an arrays only gives correct results if used in the same scope as the array declaration

```

void function(int *ar)
{
 std::cout << sizeof(ar)/sizeof(int) << std::endl; //ohoh wrong result
}

int ar[4]={1,2,3,4};
std::cout << sizeof(ar)/sizeof(int) << std::endl; // ok
function(ar);

```

---

### Post by lisati on 2009-07-05
> **MadCow108 said:**
> 
just something you'll probably stumble over:
you mostly need to save the size of your array and pass it to whatever functions which works with the array
the sizeof operator an arrays only gives correct results if used in the same scope as the array declaration


That's a good tip, which I should have thought of. One thing I've seen done is use of the sizeof operator more than once in an expression to figure out the correct number of elements. A trivial example would be something like this (apologies if the syntax isn't quite right):
```

int my_array[100];
unsigned int element_count = sizeof(my_array)/sizeof(int);

```

<excuse>perhaps I should brush up on my C skills a bit, haven't used C much</excuse>

---

### Post by gyppo on 2009-07-05
Thanks, I'll bear that in mind.

Meanwhile, I've come against another problem, which takes considerably longer to explain:

```
unsigned int* z;

unsigned int RL[4]=  {0x0000,0x8000,0x8000,0x8880};

..... so on for all elements of 'all'...

unsigned int* all[12]={RL,Rt,Rsq,R3d,BLm,BLe,Bz3d,Bz2d,YT5,YT6,Yz,YL};

int*
Xrot(int *tet){
    Yflip(tet);
    Zflip(tet);
    return tet;
}

void test(){[INDENT]for (i=0;i<12;i++){[INDENT]z=Xrot((*)all[i]);    //  <----- line 197
printf("z is %u",*z);
[/INDENT]}
[/INDENT]}

```gives me an error "197: error: expected primary-expression before &#8216;)&#8217; token"
what's going on? And what even is a primary-expression? Sorry if I should have put this in a new thread, but you're being very helpful here.

---

### Post by MadCow108 on 2009-07-05
there are a few problems in that code:
Xrot works with int's whereas all is unsigned int

the (*) is no valid c syntax. if you were trying to dereference all[i] you end up with an int (the first element of all[i]) but Xrot takes an pointer to an int. (note all[i] is the same as *(all+i) which is in your case again an array, so the[i] operator dereferences the pointer+i)

I guess z is again an array. You can't print arrays with printf only basic types (e.g. z[0]).
If z is no array then why not return a normal int instead of a pointer to an int with Xrot?

(yes C seems to make arrays very confusing :) just remember arrays in C are just pointers to continous stored values in memory)


> **lisati said:**
> That's a good tip, which I should have thought of. One thing I've seen done is use of the sizeof operator more than once in an expression to figure out the correct number of elements. A trivial example would be something like this (apologies if the syntax isn't quite right):
```

int my_array[100];
unsigned int element_count = sizeof(my_array)/sizeof(int);

```

<excuse>perhaps I should brush up on my C skills a bit, haven't used C much</excuse>
what I actually wanted to say is the the sizeof operator is very dangerous with C arrays. Its no equivalent of higher level constructs like e.g. c++ vectors size() method.
A better way would be:
```

const unsigned int element_count = 100;
int my_array[element_count];

```

---

### Post by gyppo on 2009-07-05
Oh dear lord. Thanks, I'll look into that. You've pointed me in the right direction, but I suspect I have a lot of reading to do!

---

### Post by lisati on 2009-07-05
> **MadCow108 said:**
> there are a few problems in that code:
Xrot works with int's whereas all is unsigned int

the (*) is no valid c syntax. if you were trying to dereference all[i] you end up with an int (the first element of all[i]) but Xrot takes an pointer to an int. (note all[i] is the same as *(all+i) which is in your case again an array, so the[i] operator dereferences the pointer+i)

I guess z is again an array. You can't print arrays with printf only basic types (e.g. z[0]).
If z is no array then why not return a normal int instead of a pointer to an int with Xrot?

(yes C seems to make arrays very confusing :) just remember arrays in C are just pointers to continous stored values in memory)



what I actually wanted to say is the the sizeof operator is very dangerous with C arrays. Its no equivalent of higher level constructs like e.g. c++ vectors size() method.
A better way would be:
```

const unsigned int element_count = 100;
int my_array[element_count];

```

Good point. That example looks like a safer and more elegant programming practice. (I don't have much experience with the "C" family of programming languages, and sometimes it shows.....)

---

