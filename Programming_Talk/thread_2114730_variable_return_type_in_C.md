---
title: "variable return type in C"
date: 2013-02-10
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-10
Hello,
Is is possible to have variable return type in C ?

My requirement is something like,
"There is a function which returns whatever is passed to it, whether it be an integer or a string."

Please have a look at the code below
```

**Don'tKnow** Myfunction(int num, char* str)
{
 if(num)
 {
  return num;
 } 
 else if(strlen(str))
 {
  return str;
 }
}

int main()
{
 **Don'tKnow** ret;
 ret=Myfunction(5,"");
 ret=Myfunction(0,"hello");
}

```

Please advise.
Thanks.

---

### Post by muteXe on 2013-02-11
sounds like a template function in C++, but not sure this is possible in C.
Not done C in a long time though :)

---

### Post by fdrake on 2013-02-11
> **IAMTubby said:**
> Hello,
Is is possible to have variable return type in C ?

My requirement is something like,
"There is a function which returns whatever is passed to it, whether it be an integer or a string."

Please have a look at the code below
```

**Don'tKnow** Myfunction(int num, char* str)
{
 if(num)
 {
  return num;
 } 
 else if(strlen(str))
 {
  return str;
 }
}

int main()
{
 **Don'tKnow** ret;
 ret=Myfunction(5,"");
 ret=Myfunction(0,"hello");
}

```

Please advise.
Thanks.

why don't you create 3 functions:
1 check for what kind of data your are sending and based on the results calls function for integer OR function for string.

---

### Post by Bachstelze on 2013-02-11
> **fdrake said:**
> why don't you create 3 functions:

More like "Why don't you just use Python?", really... But he never listens.

---

### Post by spjackson on 2013-02-11
C is statically typed; this means that the type of an expression is determined at compile time. What you are looking for is dynamic typing, where the type of an expression is determined at run time. There are other languages that do that: Lisp, Python etc.

Is it possible to emulate dynamic typing in C? Well, it's not impossible - see [Greenspun's tenth rule.]("http://en.wikipedia.org/wiki/Greenspun's_tenth_rule")

At the simplest level, you could return a struct containing a flag to indicate type and a union to hold the value. It wouldn't be pretty though, either in implementation or in usage.

---

### Post by IAMTubby on 2013-02-11
> **Bachstelze said:**
> More like "Why don't you just use Python?", really... But he never listens.
Sir, I was just trying to explore if it can be done in C.
I'm very sorry for the trouble. 

But I don't know python as of now, and really I was just trying to learn C in a better way and do more things with it rather than achieve the final objective. The scenario created by me was hypothetical.

I don't need this requirement immediately for a project/assignment etc, I was just curious to learn.    

But I'm sorry once again.

---

### Post by Warren Hill on 2013-02-11
What you want is not possible in C as the return type of a function is defined at compile time.

You could return a pointer to the value however or a structure containing both a string and a number together a flag to indicate which to use however.  The structure could save space by having the flag and a union of both return types as only one would be valid.

I don't think this is possible in C++ either as while you can have functions with the same name that return different types they must have have different argument types to distinguish them.

Also your return value 'ret'  how is your compiler supposed to know what this is both to allocate proper storage and when the value is used subsequently.

As has already been pointed out some other languages will allow what you want but not C.

---

### Post by Bachstelze on 2013-02-11
> **IAMTubby said:**
> Sir, I was just trying to explore if it can be done in C.
I'm very sorry for the trouble. 

But I don't know python as of now, and really I was just trying to learn C in a better way and do more things with it rather than achieve the final objective. The scenario created by me was hypothetical.

I don't need this requirement immediately for a project/assignment etc, I was just curious to learn.    

But I'm sorry once again.

It seems to me that you are just trying random things and then have some kind of checklist: "This can be done", "That can't", etc.

It's not a good way to go because you will go on forever like that, you will never run out of new things to try. What you need to do is do some serious thinking to understand *how* C works, then you will be able to answer those quenstions yourself as the need arises. Asking random questions like that *will not* make you learn anything.

---

### Post by xb12x on 2013-02-11
I would be interested to know why somebody might ever want to do this, other than for a 'bad code' contest.

Think about the maintenance nightmare.

---

### Post by Zugzwang on 2013-02-12
Well, if the set of possible return types is known beforehand, you can use a union.

[PHP]
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

typedef enum { TEXT, NUMBER } text_or_data_type;
short_text_or_number_union;

typedef struct{
    union {
        char text[8];
        int number;
    } data;
    text_or_data_type type;
} short_text_or_data;

short_text_or_data get_data() {
    short_text_or_data myRet;
    if (getpid() % 3 == 2) {
        myRet.type = TEXT;
        myRet.data.text[0] = 'B';
        myRet.data.text[1] = 'o';
        myRet.data.text[2] = 'o';
        myRet.data.text[3] = '!';
        myRet.data.text[4] = 0;
    } else {
        myRet.type = NUMBER;
        myRet.data.number = 42;
    }
    return myRet;
}

int main() {
    short_text_or_data surprise = get_data();
    if (surprise.type == TEXT) {
        printf("The surprise is a text, and it is: %s\n",surprise.data.text);
    } else {
        printf("The surprise is a number, and it is: %d\n",surprise.data.number);
    }
    return 0;
}
[/PHP]

---

