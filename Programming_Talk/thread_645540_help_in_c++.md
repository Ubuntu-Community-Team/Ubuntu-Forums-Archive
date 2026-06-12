---
title: "help in c++"
date: 2007-12-20
forum: Programming Talk
---

### Post by crookshangs on 2007-12-20
hi everyone...i need you help please..i need to do a ejercice, i'm a
student..
i have this table
#define COLS   4

#define ROWS   5

int Sum[COLS] = { 0 };

int Array[ROWS][COLS] =

{

   { 192, 48, 206, 45 },

   { 180, 20, 320, 16 },

   {  221,  90,   140,  20  },

   {  432,  50,   821,  14  },

   {  820,  61,   946,  18  },

};

and § print the data in similar screen to the previous table,
remembers to use repetitive. § printf at the end of each column the
total of votes of each candidate. § printf in outstanding form the
voted candidate more. § Add one more a row to the table than
indicates, if the candidate obtained 50% of the votes, winner, the
others second round.

thanks you very much for you help!!!!!!!

---

### Post by samjh on 2007-12-20
Please don't ask us to do your homework or assignment for you.

Always try to solve the problem yourself first.  Use resources like Google or various C++ tutorials (eg. [www.cplusplus.com](www.cplusplus.com)) to formulate your own answer.

After you've given your best shot, if you still have trouble, then ask us specific questions about the parts of the program you need help with.

To get you started, here are some resources you might find helpful for this exercise:
[http://www.cplusplus.com/doc/tutorial/arrays.html](http://www.cplusplus.com/doc/tutorial/arrays.html)
[http://www.cplusplus.com/reference/clibrary/cstdio/printf.html](http://www.cplusplus.com/reference/clibrary/cstdio/printf.html)

I do wonder why you're using C++ as your programming language, but your exercise requires you to use a C function, printf.

---

### Post by iharrold on 2007-12-20
Give it a shot first ... put some work into solving it on your own.

You will need a nested "for" loop.

i.e. something like:
```

for (i = 0; i < MAX_W; i++)
{
    for (j = 0; j < MAX_H; j++)
    {
         //Do something
    }
}

```

I also agree with samjh, printf is a part of the C language not a C++ (though supported).  Also, rather than using "#define" it would be better to have a constant value.  #define are compile time replacement, which generally work great... but to me it is better to use a const. 

Do some work and atleast put some effort into it.  This is a very easy assignment (of course if you are new to programming you'll like beg to differ... we all started where you are at one time or another).

---

### Post by bapoumba on 2007-12-20
UF is not a place to ask for homework, sorry.
Thread closed.

---

