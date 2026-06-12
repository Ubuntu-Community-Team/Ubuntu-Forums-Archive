---
title: "Structures in C"
date: 2011-10-03
forum: Programming Talk
---

### Post by bikewrecker on 2011-10-03
Hi everybody. Sorry if I posted this in the wrong place. The "development and Programming" forum was closed.

I'm having trouble passing structures to functions. I'm quite new with C as I've taught myself over the past month. Here is a basic program I am trying to run.

```

#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};

int my_other_function(struct myStruct*);

main()
{
    int answer;
    struct FuncArgs myStruct; //*pointer;
    //pointer = &myStruct;
    myStruct.a = 1;
    myStruct.b = 2;
    myStruct.c = 3;
    answer = my_other_function(FuncArgs &myStruct);
    printf("You're value is %d\n", answer);
}

int my_other_function(myStruct*)
{
    int return_value;
    return_value = myStruct.a * myStruct.b * myStruct.c;
    return return_value;
}

```And here are the errors I'm getting.

```

daniel@daniel-EP45-UD3L:~/Desktop/CProgramming/Ch5$ cc -o ST MyStruct.c
MyStruct.c:10:30: warning: &#8216;struct myStruct&#8217; declared inside parameter list [enabled by default]
MyStruct.c:10:30: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
MyStruct.c: In function &#8216;main&#8217;:
MyStruct.c:20:29: error: &#8216;FuncArgs&#8217; undeclared (first use in this function)
MyStruct.c:20:29: note: each undeclared identifier is reported only once for each function it appears in
MyStruct.c: At top level:
MyStruct.c:24:23: error: unknown type name &#8216;myStruct&#8217;

```Any help you can give me is much appreciated. And please move the thread if there is another spot I should have put it

---

### Post by Slim Odds on 2011-10-03
You don't include parameter types in function calls.

Change this:```
answer = my_other_function(FuncArgs &myStruct);
```
To this:```
answer = my_other_function(&myStruct);
```

---

### Post by nothingspecial on 2011-10-03
> **bikewrecker said:**
> Hi everybody. Sorry if I posted this in the wrong place. The "development and Programming" forum was closed.



It's alive and well

moved.

---

### Post by Doug S on 2011-10-03
I don't usually look in the development and Programming forum, but I saw this and worked on it before it got moved. I would just make the structure global.
```
#include <stdio.h>
struct FuncArgs
{
    int a;
    int b;
    int c;
};
struct FuncArgs myStruct;
int my_other_function();
main(){
    int answer;
    //pointer = &myStruct;
    myStruct.a = 1;
    myStruct.b = 2;
    myStruct.c = 3;
//  answer = my_other_function(FuncArgs &myStruct);
    answer = my_other_function();
    printf("You're value is %d\n", answer);
}
int my_other_function(){
    int return_value;
    return_value = myStruct.a * myStruct.b * myStruct.c;
    return return_value;
}
```

---

### Post by bikewrecker on 2011-10-03
Hmm. Ok. Well thank you for moving it! Ok I changed the function call and I also made the structure global.  Heres my new code and new errors. Am I missing a header file or something?

```

#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};
struct FuncArgs myStruct; //*pointer;
int my_other_function(struct myStruct*);

main()
{
    int answer;
    myStruct.a = 1;
    myStruct.b = 2;
    myStruct.c = 3;
    answer = my_other_function(&myStruct);
    printf("You're value is %d\n", answer);
}

int my_other_function(myStruct*)
{
    int return_value;
    return_value = myStruct.a * myStruct.b * myStruct.c;
    return return_value;
}

```

```

daniel@daniel-EP45-UD3L:~/Desktop/CProgramming/Ch5$ cc -o ST MyStruct.c
MyStruct.c:10:30: warning: ‘struct myStruct’ declared inside parameter list [enabled by default]
MyStruct.c:10:30: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
MyStruct.c: In function ‘main’:
MyStruct.c:18:2: warning: passing argument 1 of ‘my_other_function’ from incompatible pointer type [enabled by default]
MyStruct.c:10:5: note: expected ‘struct myStruct *’ but argument is of type ‘struct FuncArgs *’
MyStruct.c: At top level:
MyStruct.c:22:23: error: expected declaration specifiers or ‘...’ before ‘myStruct’

```

---

### Post by Bachstelze on 2011-10-03
```
#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};
struct FuncArgs myStruct;

int my_other_function(void);

int main(void)
{
    int answer;
    myStruct.a = 1;
    myStruct.b = 2;
    myStruct.c = 3;
    answer = my_other_function();
    printf("Your value is %d\n", answer);
}

int my_other_function(void)
{
    int return_value;
    return_value = myStruct.a * myStruct.b * myStruct.c;
    return return_value;
}

```

Since myStruct is a global variable, passing it as argument is redundant.

---

### Post by bikewrecker on 2011-10-03
> **Bachstelze said:**
> ```
#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};
struct FuncArgs myStruct;

int my_other_function(void);

int main(void)
{
    int answer;
    myStruct.a = 1;
    myStruct.b = 2;
    myStruct.c = 3;
    answer = my_other_function();
    printf("Your value is %d\n", answer);
}

int my_other_function(void)
{
    int return_value;
    return_value = myStruct.a * myStruct.b * myStruct.c;
    return return_value;
}

```Since myStruct is a global variable, passing it as argument is redundant.

Oh yea duh. That wasn't the case a second ago. Thank you soo much! It's working now. 

So When I make structures I should just make them global or is that bad programming technique? Thanks for all your help guys. I really appreciate it!

---

### Post by ofnuts on 2011-10-03
Fairly rusty in C, but when you declare:

```
int my_other_function(myStruct*)
```you are basically telling C that the function argument is a pointer to myStruct, so your code should access the contents using the pointer derefeence:

```
return_value = myStruct->a
```and not direct access ("dot").

---

### Post by Bachstelze on 2011-10-03
> **bikewrecker said:**
> Oh yea duh. That wasn't the case a second ago. Thank you soo much! It's working now. 

So When I make structures I should just make them global or is that bad programming technique? Thanks for all your help guys. I really appreciate it!

Global variables aren't a bad thing *per se* but don't overdo it. Basically, you use them for data that you need to access in a lot of different parts of your programs, in order to avoid having to pass arguments all over the place. Here, the program is short and adding an argument to the function doesn't hurt (since there is none), so I would not use a global variable.

---

### Post by ofnuts on 2011-10-03
> **bikewrecker said:**
> Oh yea duh. That wasn't the case a second ago. Thank you soo much! It's working now. 

So When I make structures I should just make them global or is that bad programming technique? Thanks for all your help guys. I really appreciate it!Very bad programming... You can pass struct as pointers (or even, for small ones, as values) as long as you access them properly. Usually, structs are the result of a malloc() so you should know how to handle pointers to structs.

---

### Post by bikewrecker on 2011-10-03
> **ofnuts said:**
> Very bad programming... You can pass struct as pointers (or even, for small ones, as values) as long as you access them properly. Usually, structs are the result of a malloc() so you should know how to handle pointers to structs.

Ok well I used the site ([http://www.taranets.net/cgi/ts/1.37/ts.ws.pl?w=329;b=282](http://www.taranets.net/cgi/ts/1.37/ts.ws.pl?w=329;b=282)) and I've copied the same syntax they're using. Would you consider this better programming technique for my program?
```

#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};

main()
{
    struct FuncArgs myStruct;
    struct FuncArgs *pointer;
    pointer = &myStruct;
    int answer;

    int my_other_function(struct FuncArgs *pointer);

    pointer->a = 1;
    pointer->b = 2;
    pointer->c = 3;
    answer = my_other_function(pointer);
    printf("You're value is %d\n", answer);
}

int my_other_function(struct FuncArgs *pointer)
{
    int return_value;
    return_value = (*pointer).a * (*pointer).b * (*pointer).c;
    return return_value;
}

```

Thanks again for your input.

---

### Post by karlson on 2011-10-03
> **bikewrecker said:**
> Ok well I used the site ([http://www.taranets.net/cgi/ts/1.37/ts.ws.pl?w=329;b=282](http://www.taranets.net/cgi/ts/1.37/ts.ws.pl?w=329;b=282)) and I've copied the same syntax they're using. Would you consider this better programming technique for my program?
```

#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};

main()
{
    struct FuncArgs myStruct;
    struct FuncArgs *pointer;
    pointer = &myStruct;
    int answer;

    int my_other_function(struct FuncArgs *pointer);

    pointer->a = 1;
    pointer->b = 2;
    pointer->c = 3;
    answer = my_other_function(pointer);
    printf("You're value is %d\n", answer);
}

int my_other_function(struct FuncArgs *pointer)
{
    int return_value;
    return_value = (*pointer).a * (*pointer).b * (*pointer).c;
    return return_value;
}

```

Thanks again for your input.

Not really.  This would be better:

```

#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};

int my_other_function(struct FuncArgs *pointer);

main()
{
    struct FuncArgs myStruct;
    int answer;

    myStruct.a = 1;
    myStruct.b = 2;
    myStruct.c = 3;
    answer = my_other_function(&myStruct);
    printf("You're value is %d\n", answer);
}

int my_other_function(struct FuncArgs *pointer)
{
    int return_value;
    return_value = pointer->a * pointer->b * pointer->c;
    return return_value;
}

```

Your code introduces variables that are unnecessary.

Although with compiler optimization(-O3 on gcc) the code would look identical.

---

### Post by bikewrecker on 2011-10-03
> **karlson said:**
> Not really.  This would be better:

```

#include <stdio.h>

struct FuncArgs
{
    int a;
    int b;
    int c;
};

int my_other_function(struct FuncArgs *pointer);

main()
{
    struct FuncArgs myStruct;
    int answer;

    myStruct.a = 1;
    myStruct.b = 2;
    myStruct.c = 3;
    answer = my_other_function(&myStruct);
    printf("You're value is %d\n", answer);
}

int my_other_function(struct FuncArgs *pointer)
{
    int return_value;
    return_value = pointer->a * pointer->b * pointer->c;
    return return_value;
}

```Your code introduces variables that are unnecessary.

Although with compiler optimization(-O3 on gcc) the code would look identical.
Ok that makes sense. Thanks for your help!

---

