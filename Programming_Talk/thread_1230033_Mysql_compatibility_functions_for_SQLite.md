---
title: "Mysql compatibility functions for SQLite?"
date: 2009-08-02
forum: Programming Talk
---

### Post by Gannon8 on 2009-08-02
Hello all, I have some questions.
1. Is there any C code that implements some common functions found in mysql but not in sqlite (ect. INET_ATON and its reverse, ect)?
2. If not, if I open the same database in 2 different parts of the program and make the variables local and create functions in one part, will it work for the second part? Sorry if its a little hard to understand.

---

### Post by Wim Sturkenboom on 2009-08-03
1)
There are probably lots of functions in MySQL that don't exist in SQLite. For the one you asked, there is a standard C function; see *man inet_aton*

2)
If I understand you correctly the question is if a variable defined in one function is available in another one. If so, the answer is no.

Hope it helps.

---

### Post by Gannon8 on 2009-08-03
> **Wim Sturkenboom said:**
> 2)
If I understand you correctly the question is if a variable defined in one function is available in another one. If so, the answer is no.

No that's not what I meant. Something like:
```
//test1.c
#include <stdlib.h>
#include "sqlite3.h"
#include "test2.c"

static sqlite3 db*;

def main()
{
    //do connection stuff here
    do_test2_thing();

    results = db->query("SELECT a, INET_ATON(a) FROM stupidtable;");
    printf(results);
}
```
```
//test2.c
static sqlite3 db*

static void inet_aton(/* args here */);

void do_test2_thing()
{
    //do connection stuff here
    db->AddFunc(/*args here*/, inet_aton);
}

```

---

### Post by Wim Sturkenboom on 2009-08-04
```

int myinteger;

int myfunction();

int main(int argc, char *argv[])
{

        myinteger=33;
        myfunction();
        return 0;
}

```
```

#include <stdio.h>

extern int myinteger;

int myfunction()
{
        printf("Hallo\n myinteger is %d\n",myinteger);
        return 0;
}

```
This is my example with a 'global' variable. In the second file, the variable is declared as extern. I tried it with and without 'extern' (the latter I expected to give an error but it did not).

There is no reason to include test2.c ! You should compile it to an object file and link it.

Simplest way is something like
```

gcc -Wall test1.c test2.c -o yourtest

```
but if you have hundreds of sourcefiles, it's better to use a makefile.

---

### Post by Gannon8 on 2009-08-05
> **Wim Sturkenboom said:**
> see *man inet_aton*
There is no man page for that function. Can't find it online either. It's not in socket.h nor wikipedia. :confused:

Edit: Found it

---

