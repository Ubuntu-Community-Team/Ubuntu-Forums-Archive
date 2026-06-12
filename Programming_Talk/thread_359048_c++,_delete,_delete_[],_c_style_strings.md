---
title: "c++, delete, delete [], c style strings"
date: 2007-02-11
forum: Programming Talk
---

### Post by rbprogrammer on 2007-02-11
ok, so i have this little bit of code:
```

rbpstring& rbpstring::operator + (char* &param)
{
    int newLength = length() + lengthof(param) + 1;
    char *buffer = data;
    data = new char[newLength];
    strcpy(data,buffer);
    strcat( data, param );
    delete [ ] buffer;
    size = newLength;
    return *this;
}
```
[LIST]
[*]length() = gets the length of the original string
[*]lengthof(param) = gets the length of the second string
[*]data = is the original string stored as a char* in the class rbpstring
[*]size = is the length of data
[/LIST]
now the problem is when i do the: delete [ ] buffer. i get this error:
```
*** glibc detected *** ./rbp: munmap_chunk(): invalid pointer: 0x08048e4c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x18a)[0xb7dbdb4a]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7f6dfc1]
/usr/lib/libstdc++.so.6(_ZdaPv+0x1d)[0xb7f6e01d]
./rbp[0x8048b8a]
./rbp[0x8048c7f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7d6c8cc]
./rbp(__gxx_personality_v0+0x6d)[0x80487a1]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:11 11010105   /media/usbdisk/development/rbp/debug/src/rbp
0804a000-0804b000 rw-p 00001000 08:11 11010105   /media/usbdisk/development/rbp/debug/src/rbp
0804b000-0806c000 rw-p 0804b000 00:00 0          [heap]
b7d56000-b7d57000 rw-p b7d56000 00:00 0
b7d57000-b7e84000 r-xp 00000000 08:02 843688     /lib/tls/i686/cmov/libc-2.4.so
b7e84000-b7e86000 r--p 0012c000 08:02 843688     /lib/tls/i686/cmov/libc-2.4.so
b7e86000-b7e88000 rw-p 0012e000 08:02 843688     /lib/tls/i686/cmov/libc-2.4.so
b7e88000-b7e8c000 rw-p b7e88000 00:00 0
b7e8c000-b7e96000 r-xp 00000000 08:02 811267     /lib/libgcc_s.so.1
b7e96000-b7e97000 rw-p 00009000 08:02 811267     /lib/libgcc_s.so.1
b7e97000-b7ebb000 r-xp 00000000 08:02 843716     /lib/tls/i686/cmov/libm-2.4.so
b7ebb000-b7ebd000 rw-p 00023000 08:02 843716     /lib/tls/i686/cmov/libm-2.4.so
b7ebd000-b7f91000 r-xp 00000000 08:02 18622      /usr/lib/libstdc++.so.6.0.8
b7f91000-b7f94000 r--p 000d4000 08:02 18622      /usr/lib/libstdc++.so.6.0.8
b7f94000-b7f96000 rw-p 000d7000 08:02 18622      /usr/lib/libstdc++.so.6.0.8
b7f96000-b7f9c000 rw-p b7f96000 00:00 0
b7fad000-b7fb0000 rw-p b7fad000 00:00 0
b7fb0000-b7fc9000 r-xp 00000000 08:02 811222     /lib/ld-2.4.so
b7fc9000-b7fcb000 rw-p 00018000 08:02 811222     /lib/ld-2.4.so
bfc7e000-bfc94000 rw-p bfc7e000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

```
i dont know what this means. also, how do i delete the the data ( *information* ) stored in the memory where "buffer" points to?

i'm not sure, but once the function ends, doesnt the memory get deleted anyway? but if i know how to free up this memory, it will come in handy later on in the program.....

---

### Post by Wybiral on 2007-02-11
Where did "data" come from?

EDIT:

Ooops... Just read the list under the code, nm...

---

### Post by Wybiral on 2007-02-11
Since "data" already points to something that hasn't been deleted, you probably shouldn't use "data = new char[newLength];" before it's deleted.

---

### Post by po0f on 2007-02-11
rbprogrammer,

Is this just an exercise in building your own string class?  If not, why aren't you using std::string instead?

---

### Post by rbprogrammer on 2007-02-11
> **po0f said:**
> Is this just an exercise in building your own string class?  If not, why aren't you using std::string instead?
yea, it's pretty much an exercise, i just dont know how to properly delete the "array"

---

### Post by kfjethro on 2007-02-11
rbprogrammer,

I assume that your constructor takes a char * as a parameter which is the
initial value. If so, how do you allocate the "data" field in your constructor ?
Did you use "new" or a variant of malloc() such as malloc() or strdup () ?
The two types of memory allocation have to be used in pairs.

Items that are new'd will not get delete'd when your rbstring instance goes
out of scope. You must delete them in your destructor.

HTH

---

### Post by WW on 2007-02-11
If your destructor does something like this:
```
delete [] char;
```
and you do something like this in a block of code:
```

{
    char *h = " How are you?";
    rbstring s("Hello, world.");
    rbstring t = s + h;
}
```
then, after the last statement, both s and t are really the same object.  The destructor for both s and t will be called.  The first destructor will work, and the second destructor will crash, because it will try to delete memory that was already deleted.

---

### Post by kfjethro on 2007-02-11
> **WW said:**
> If your destructor does something like this:
```
delete [] char;
```
and you do something like this in a block of code:
```

{
    char *h = " How are you?";
    rbstring s("Hello, world.");
    rbstring t = s + h;
}
```
then, after the last statement, both s and t are really the same object.  The destructor for both s and t will be called.  The first destructor will work, and the second destructor will crash, because it will try to delete memory that was already deleted.

Not neccessarily - it depends on how the rbstring copy constructor is implemented.
The copy constructor needs to do a deep copy of at least the "data" member.

---

### Post by WW on 2007-02-11
kfjethro: True.  Actually, considering the comments at the end of the original post, I don't know if rbprogrammer has implemented a destructor or copy constructor.

rbprogrammer: It would help to see more of the code to know what is going wrong.  The problem is not necessarily related to using delete [] like you did (but it might be).

---

### Post by rbprogrammer on 2007-02-11
for in the constructor all i have is:
```

rbpstring::rbpstring(char* &param)
{
    data = new char[lengthof(param)];
    data = param;
}

```
[LIST]
[*]lengthof() = just finds the length of the character array
[/LIST]
to update my question, i dont know how to delete the (char*) variable data.  so how do i do that?  i'm assuming the: delete[] data should work, but i get that long weird error message.......

---

### Post by kfjethro on 2007-02-11
> **rbprogrammer said:**
> for in the constructor all i have is:
```

rbpstring::rbpstring(char* &param)
{
    data = new char[lengthof(param)];
    data = param;
}

```
[LIST]
[*]lengthof() = just finds the length of the character array
[/LIST]
to update my question, i dont know how to delete the (char*) variable data.  so how do i do that?  i'm assuming the: delete[] data should work, but i get that long weird error message.......

You have to copy the contents pointed to by "param" to the "data" field
using something like this:

#include <string.h>

rbpstring::rbpstring(char* &param)
{
    data = new char[lengthof(param)];
    memcpy ((void *) data, (void *)param, strlen(param) + 1);
   // your old code "data = param" was just assigning the value
   // of the param pointer to the data pointer (not the contents). The data pointed to by param
  // was probably not allocated using new, thus the delete [] data in
  // operator+ got upset.
}

And define a destructor to clean up the memory you allocated.
This destructor gets called automatically when an instance of your
rbstring goes out of scope or you delete an rbstring that has been new'd:

rbstring::~rbstring () {

   delete [] data;

}

This should fix up your operator+ problems since the operator+ code
tries to delete the old "data" field which was not set up correctly in
your constructor.

---

### Post by lnostdal on 2007-02-11
if you want proper help you will have to post complete code with a running example

i speak for every guy with a potential  answer here when i say i want to be able to mark the code (which you have shortened as much as possible), paste it into my editor, then compile it and out spits an executable that crashes like above thus illustrating the problem properly

too many loose ends and possibilities to answer, but it seems you're just re-assigning what `data' _points to_ .. (you think you're copying the contents of `param' into it but you're really not) .. but as said you might have messed with other stuff here leading to totally different behavior in regards to the operators and whatnot   (gee; ain't C++ great .. oh, and if my assumption is right - you also have a memory leak)

---

### Post by Wybiral on 2007-02-11
> **lnostdal said:**
> if you want proper help you will have to post complete code with a running example

i speak for every guy with a potential  answer here when i say i want to be able to mark the code (which you have shortened as much as possible), paste it into my editor, then compile it and out spits an executable that crashes like above thus illustrating the problem properly

too many loose ends and possibilities to answer, but it seems you're just re-assigning what `data' _points to_ .. (you think you're copying the contents of `param' into it but you're really not) .. but as said you might have messed with other stuff here leading to totally different behavior in regards to the operators and whatnot   (gee; ain't C++ great .. oh, and if my assumption is right - you also have a memory leak)

As much as I hate to agree with Inostdal ( :) )... He's correct. I would be able to help find the error much quicker if I could see everything.

---

### Post by rbprogrammer on 2007-02-14
> **kfjethro said:**
> 
...
memcpy ((void *) data, (void *)param, strlen(param) + 1);
...


ok, i got the assignment issue working, now i will work on the possible memory leak.  i think i can handle it from here, but should i need help, i will definitely ask.

this forum ceases to amaze me with the help received.

---

### Post by po0f on 2007-02-15
rbprogrammer,

Don't you mean this forum *never* ceases to amaze you?  The other sounds like an insult.  ;)

---

### Post by rbprogrammer on 2007-02-16
> **po0f said:**
> rbprogrammer,

Don't you mean this forum *never* ceases to amaze you?  The other sounds like an insult.  ;)

whoops, your right.....
i mean to say this forum is most helpful.

---

