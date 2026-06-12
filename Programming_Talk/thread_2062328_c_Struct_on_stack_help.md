---
title: "c Struct on stack help"
date: 2012-09-24
forum: Programming Talk
---

### Post by snowlizard31 on 2012-09-24
Hi I'm learning C and I'm trying to convert some code from struct on the heap to on the stack. Can some one please explain how to do this but not convert all the code because I'd like to do at least some of it on my own

```


#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <string.h>


struct person {
    char *name;
    int age;
    int height;
    int weight;
};

struct person *person_create(char *name, int age, int height, int weight)
{
    
    struct person *who = malloc(sizeof(struct person));
    assert(who != NULL); 
    
    who ->name = strdup(name); 
    who ->age = age; 
    who ->height = height;
    who -> weight = weight;
    
    return who; 
}
void person_destroy(struct person *who)
{
    assert(who != NULL);
    
    free(who->name);
    free(who);
}

void person_print(struct person *who)
{
    printf("Name: %s\n", who->name);
    printf("\tAge: %d \n",who->age);
    printf("\tHeight: %d\n",who->height);
    printf("\tWeight: %d\n",who->weight);
}

int main(int argc, char *argv[])
{
    
    struct person *joe = person_create(
    "Joe Alex", 32, 64, 140);
    
    struct person *frank = person_create(
        "Frank Blank", 20, 72, 180);
    
    
    printf("Joe is at memory location %p:\n", joe);
    person_print(joe);
    
    printf("Frank is at memory location %p:\n",frank);
    person_print(frank);
    
    
    joe->age +=20;
    joe->height -=2;
    joe->weight +=40;
    person_print(joe);
    
    frank->age +=20;
    frank->weight+=20;
    person_print(frank);
    
    
    person_destroy(joe);
    person_destroy(frank);
    
    return 0;
}

```Here's my attempt at it I was trying to take it little by little but this is really confusing. this produces errors 
```

#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <string.h>


typedef struct {
    char *name;
    int age;
    int height;
    int weight;
}person;

person_create()
{
    
    person who;
    
    who.name = strdup(name); 
    who.age = age; 
    who.height = height;
    who.weight = weight;
    
    return who;
}



int main()
{
    person joe = ("joe", 24, 75, 140);
    printf("Hi %s!",joe.name);
    
    return 0;
}

```

---

### Post by vexorian on 2012-09-24
My non-C++  C is rusted, but I think you might need to do:

```

struct person who;

```
And

```

struct person joe = ("joe", 24, 75, 140);

```

It would help if you posted the errors you get.

---

### Post by snowlizard31 on 2012-09-24
Here are the errors 
```

cc -Wall -g    ex16a.c   -o ex16a
ex16a.c:15: warning: return type defaults to ‘int’
ex16a.c: In function ‘person_create’:
ex16a.c:19: error: ‘name’ undeclared (first use in this function)
ex16a.c:19: error: (Each undeclared identifier is reported only once
ex16a.c:19: error: for each function it appears in.)
ex16a.c:20: error: ‘age’ undeclared (first use in this function)
ex16a.c:21: error: ‘height’ undeclared (first use in this function)
ex16a.c:22: error: ‘weight’ undeclared (first use in this function)
ex16a.c:24: error: incompatible types in return
ex16a.c:25: warning: control reaches end of non-void function
ex16a.c: In function ‘main’:
ex16a.c:31: warning: left-hand operand of comma expression has no effect
ex16a.c:31: warning: left-hand operand of comma expression has no effect
ex16a.c:31: warning: left-hand operand of comma expression has no effect
ex16a.c:31: error: invalid initializer
make: *** [ex16a] Error 1

```

I tried what you suggested but the compiler came up with more errors 
```

cc -Wall -g    ex16a.c   -o ex16a
ex16a.c:15: warning: return type defaults to ‘int’
ex16a.c: In function ‘person_create’:
ex16a.c:17: error: storage size of ‘who’ isn’t known
ex16a.c:19: error: ‘name’ undeclared (first use in this function)
ex16a.c:19: error: (Each undeclared identifier is reported only once
ex16a.c:19: error: for each function it appears in.)
ex16a.c:20: error: ‘age’ undeclared (first use in this function)
ex16a.c:21: error: ‘height’ undeclared (first use in this function)
ex16a.c:22: error: ‘weight’ undeclared (first use in this function)
ex16a.c:17: warning: unused variable ‘who’
ex16a.c:25: warning: control reaches end of non-void function
ex16a.c: In function ‘main’:
ex16a.c:31: error: variable ‘joe’ has initializer but incomplete type
ex16a.c:31: warning: left-hand operand of comma expression has no effect
ex16a.c:31: warning: left-hand operand of comma expression has no effect
ex16a.c:31: warning: left-hand operand of comma expression has no effect
ex16a.c:31: error: storage size of ‘joe’ isn’t known
ex16a.c:31: warning: unused variable ‘joe’
make: *** [ex16a] Error 1


```

---

### Post by Bachstelze on 2012-09-24
```
#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <string.h>


struct person {
    char *name;
    int age;
    int height;
    int weight;
};

struct person person_create(char *name, int age, int height, int weight)
{
    struct person who;   
    who.name = strdup(name); 
    who.age = age; 
    who.height = height;
    who.weight = weight;
    return who;
}



int main(void)
{
    struct person joe = {"joe", 24, 75, 140};
    printf("Hi %s!\n", joe.name);
    free(joe.name);
    return 0;
}

```

---

### Post by Bachstelze on 2012-09-24
Also you don't need person_create() if you are going to initialise your struct like that...

---

### Post by snowlizard31 on 2012-09-24
Thanks it worked:) but when I run it I get this error
```

Hi joe!
ex16a(187) malloc: *** error for object 0x100000edc: pointer being freed was not allocated
*** set a breakpoint in malloc_error_break to debug
Abort trap

``` How can I fixed this and print out the location of a 'person' I create as in like person_create in the first script without using malloc.

I was thinking I didn't need person_create(2nd script)  but if i don't use it, I can still create multiple persons with struct person right?

also when you did :
struct person joe = {"joe",24, 75, 140};

did you make an array? I thought I needed to use square brackets

---

### Post by Bachstelze on 2012-09-24
Oh sorry, remove the call to free(), you only need it if you use person_create() (to free the memory allocated by strdup()).

And no, this does not "create an arrray", it just initialises the fields of the struct, which I suppose is what you wanted to do in your proposed code.

---

### Post by snowlizard31 on 2012-09-24
Thanks for the help! I appreciate it but if its no problem I like to ask for some more help.
```

struct person {
    char *name;
    int age;
    int height;
    int weight;
};

struct person person_create(char *name, int age, int height, int weight)
{
    struct person who;   
    who.name = strdup(name); 
    who.age = age; 
    who.height = height;
    who.weight = weight;
    return who;
}

void person_destroy(struct person who)
{
    assert(who != NULL);
    
    free(who.name);
    free(who);
}

void person_print(struct person who)
{
    printf("Name: %s\n", who.name);
    printf("\tAge: %d \n",who.age);
    printf("\tHeight: %d\n",who.height);
    printf("\tWeight: %d\n",who.weight);
}

int main(void)
{
    struct person joe = {"joe", 24, 75, 140};
    struct person frank = {"frank",19, 80, 210};
    
    person_print(struct person joe);
    
    return 0;
}

```From my understanding if i create  a 'create' function I also need a destroy function. Because it can cause memory problems. I've tried adding all the functions from the first script but I've still have some errors; fewer than what I started with thanks for that. Can you please explain a solution

```

cc -Wall -g    ex16a.c   -o ex16a
ex16a.c: In function &#8216;person_destroy&#8217;:
ex16a.c:26: error: invalid operands to binary != (have &#8216;struct person&#8217; and &#8216;void *&#8217;)
ex16a.c:29: error: incompatible type for argument 1 of &#8216;free&#8217;
ex16a.c: In function &#8216;main&#8217;:
ex16a.c:45: error: expected expression before &#8216;struct&#8217;
ex16a.c:43: warning: unused variable &#8216;frank&#8217;
ex16a.c:42: warning: unused variable &#8216;joe&#8217;
make: *** [ex16a] Error 1

```P.S 
Do I even need assert( who != NULL)
OK so I was trying to fix this and instead of having 
print_person(struct person joe)
I got rid of struct person and left joe so now I'm down to the assert error and free(who.name)

---

### Post by ofnuts on 2012-09-24
<stupid me... forgot that modern C will copy structs when they are returned from functions>

---

### Post by Bachstelze on 2012-09-24
> **snowlizard31 said:**
> From my understanding if i create  a 'create' function I also need a destroy function. Because it can cause memory problems.

Not really.  What you need is to free() any memory that you have allocated with malloc() or a similar function.  Creating specific create() and destroy() function is one way to do it, but there is nothing that mandates doing it that way.

> I've tried adding all the functions from the first script but I've still have some errors; fewer than what I started with thanks for that. Can you please explain a solution

Post the code.

---

### Post by snowlizard31 on 2012-09-24
```

#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <string.h>


struct person {
    char *name;
    int age;
    int height;
    int weight;
};

struct person person_create(char *name, int age, int height, int weight)
{
    struct person who;   
    who.name = strdup(name); 
    who.age = age; 
    who.height = height;
    who.weight = weight;
    return who;
}

void person_destroy(struct person who)
{
    assert(who != NULL);
    
    free(who.name);
    free(who);
}

void person_print(struct person who)
{
    printf("Name: %s\n", who.name);
    printf("\tAge: %d \n",who.age);
    printf("\tHeight: %d\n",who.height);
    printf("\tWeight: %d\n",who.weight);
}

int main(void)
{
    struct person joe = {"joe", 24, 75, 140};
    struct person frank = {"frank",19, 80, 210};
    
    person_print(joe);
    person_print(frank);
    
    return 0;
}

```
And here's the errors 
```

c -Wall -g    ex16a.c   -o ex16a
ex16a.c: In function ‘person_destroy’:
ex16a.c:26: error: invalid operands to binary != (have ‘struct person’ and ‘void *’)
ex16a.c:29: error: incompatible type for argument 1 of ‘free’
make: *** [ex16a] Error 1

```
So does that mean I don't need the person_destroy function? I only need it if I use malloc?

---

### Post by Bachstelze on 2012-09-24
who is not a pointer, you can't compare it to NULL or pass it as argument to free().

---

### Post by snowlizard31 on 2012-09-24
oh who is a struct right nested inside sturct person_create.
So structures in C are kind of like classes in python right you use dot notation to access elements of the class but in C you also have to declare the struct inside the function you want to use it in? Thank btw I finally got the code bug free!!

---

### Post by Bachstelze on 2012-09-24
person_create() is a function...

---

