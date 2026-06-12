---
title: "C Types"
date: 2008-10-11
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-11
how would you pass a type into a C function. Like a makeshift C++ template

---

### Post by yabbadabbadont on 2008-10-11
I think that you need to elaborate as to what exactly you are trying to accomplish.  All parameters passed to C functions have a "type".  :)

---

### Post by Mr.Macdonald on 2008-10-11
pass the type of a parameter

void funct(void * data, "type" ty) {
}

---

### Post by yabbadabbadont on 2008-10-11
What I have done in the past, is to have the first field of a structure contain a flag indicating the type of the structure.  (all of the possible structures contain this same field)  Then once I know which type of structure it is, I can cast the pointer accordingly to access the individual fields.  I've used this method in the past when reading data from disk files that contain multiple data formats.

Edit: you can also do this using unions.

---

### Post by PandaGoat on 2008-10-11
The above post seems to be the best way.  This is what he means if you did not understand:

[PHP]
#define TYPE_DEMO_STRUCT 0x01
#define TYPE_SOMETHING_ELSE 0x02
/*. . .*/

struct demo_struct
{
    char type; /* only use a byte to hold what type it is */
    int some_int;
};

void some_function(void* var)
{
    char type = *(char*)var;
    if(type == TYPE_DEMO_STRUCT)
      {
           struct demo_struct* ds = (struct demo_struct*)var;
           printf("%i\n", ds->some_int);
      }
};

int main()
{
    struct demo_struct ds = {TYPE_DEMO_STRUCT, 666};
    some_function(&ds);
    return 1;
}
[/PHP]

The glaring question is why I casted var to a char* in some_function.  Any variable can be represented as an array of bytes (an array of chars).  You cannot just dereference var as a void* to get the first byte, so you must cast it as a char*.

---

### Post by yabbadabbadont on 2008-10-11
I didn't provide an example because I wanted them to do their homework by themselves...  :D

You know the drill, "The rest is left as an exercise for the student."

---

### Post by Mr.Macdonald on 2008-10-11
Sorry to rant but ...
> homework by themselves
THIS ISN'T HOMEWORK. I feel that people should answer the questions and not assume that this is homework. Just because I asked a general question doesn't mean that it is homework. in fact I am making a vector header for future use.

The fact is that if someone is taking a computer science class, they probably aren't being forced to take it. That said if they wish to cheat on learning something they want to learn then they are pathetic.



Alright then, So there isn't a data type that hold the type of a variable.

like
```

type * datatype = &int;
(*datatype) variable = 234;

```

---

### Post by PandaGoat on 2008-10-11
Nope there is not in c, only in c++.

---

### Post by Mr.Macdonald on 2008-10-11
How about Enumerations

---

