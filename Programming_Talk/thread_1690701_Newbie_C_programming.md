---
title: "Newbie C programming"
date: 2011-02-18
forum: Programming Talk
---

### Post by AlexanderPike on 2011-02-18
Hi I wanted to see, for no real reason other than to do it, if I could emulate object orientated methods with a C struct that has a function. Maybe my non-working code can work to explain what I mean :)
```
#include <stdio.h>

struct person{
        char name[10];
        void (*setname)();
}

int main(){
        struct person test;
        test.setname=&setname;
        *(test.setname)(&test,"John");
        printf("name: %s",test.name);
        return 0;
}
void setname(struct person *self, char name[]){
        self->name=name;
}

```
[http://pastebin.com/0v1ziYnc](http://pastebin.com/0v1ziYnc)


This yields:
```

gcc -o struc oo.c
oo.c:8: error: two or more data types in declaration specifiers
oo.c: In function âmainâ:
oo.c:10: error: âsetnameâ undeclared (first use in this function)
oo.c:10: error: (Each undeclared identifier is reported only once
oo.c:10: error: for each function it appears in.)
oo.c:11: error: void value not ignored as it ought to be
oo.c:13: error: incompatible types in return
oo.c:8: warning: return type of âmainâ is not âintâ
oo.c: In function âsetnameâ:
oo.c:16: error: incompatible types in assignment


```
I don't know what the funny characters are about maybe it's a putty thing?

---

### Post by MadCow108 on 2011-02-18
there are a few issues:
- a semicolon is missing after the closing bracket of the struct

- a forward declaration for setname is missing as it is defined below main
place this or the whole function before main:
```
void setname(struct person *self, char *name);
```
note I changed  char name[]. I find this makes it clearer, see next point

- character arrays decay into pointers on stack changes, this includes function pointers. So char name[] is **exactly** same as char * name in a function declaration.
This makes clear that setname does not work. you have to do this:
```

#include <string.h>
void setname(struct person *self, char * name){
  strncpy(self->name,name,sizeof(self->name));
  // or safer version
  strncpy(self->name,name,sizeof(self->name) - 1);
  self->name[sizeof(self->name) - 1] = 0;
}
```

- the function pointer calling syntax is wrong. You are calling the function and dereferencing the result (which is void).
either this:
```
(*test.setname)(&test,"John")
//or
(test.setname)(&test,"John")
```
or a bit clearer:
```
(*(test.setname))(&test,"John")
```

---

### Post by cgroza on 2011-02-18
In this line(9), you do not need to specify struct again:
```
struct person test;
``` 
Should be:```

person test;
```

---

### Post by AlexanderPike on 2011-02-18
Thanks MadCow108! It works perfectly now. Here's the completed code if anyone is interested.

```

#include <stdio.h>
#include <string.h>

struct person{
        char name[10];
        void (*setname)();
};
void setname(struct person *self, char *name);

int main(){
        struct person test;
        test.setname = &setname;
        (*test.setname)(&test,"John");
        printf("name: %s",test.name);
        return 0;
}
void setname(struct person *self, char * name){
  strncpy(self->name,name,sizeof(self->name));
}

```

---

### Post by MadCow108 on 2011-02-18
> **cgroza said:**
> In this line(9), you do not need to specify struct again:
```
struct person test;
``` 
Should be:```

person test;
```


in C you do need the struct. This is different in C++

you can only skip it if you do a typedef:
```
typedef struct mystruct {
...
} mystruct;
// or 
struct mystruct_s {
...
};
typedef mystruct_s mystruct_t;
```

---

### Post by cgroza on 2011-02-18
> **MadCow108 said:**
> in C you do need the struct. This is different in C++

you can only skip it if you do a typedef:
typedef struct mystruct {
...
} mystruct;
// or 
struct mystruct_s {
...
};
typedef mystruct_s mystruct_t;

I know that in C++ that is not necessary, and people say that they try to maintain compatibility.
Anyway, sorry for misleading information.

---

### Post by worksofcraft on 2011-02-18
> **AlexanderPike said:**
> Thanks MadCow108! It works perfectly now. Here's the completed code if anyone is interested.
...


Yes that is an excellent bit of research into how Object orientedness might be done :)

Just incase you want to know more accurately what a C++ compiler would be generating... well it would be closer to this:
[php]
// gcc Cvtable.c ... this is straight C code for an OOP paradigm
#include <stdio.h>
#include <string.h>

// these just to make it more intelligible
typedef void (*fptr)();
typedef char * (*cptr)();

// all instances of person class must have a vtable pointer
struct person{
	fptr *vtable;
	char name[10];
};

// the methods of person class are setname and getname
void setname(struct person *self, char * name){
  strncpy(self->name,name,sizeof(self->name));
}

char * getname(struct person *self){
	return self->name;
}

// this is person class vtable
fptr person_vtable[] = {
	(fptr) &setname,
	(fptr) &getname
};

int main(){
	// construct a person class instance
	struct person test;
	// which implies setting it's vtable pointer
	test.vtable = person_vtable;

	// call the setname method on this instance "test" of class person
	(*test.vtable[0])(&test,"John");

	// call the getname method on that instance
	return !printf("name: %s\n", ((cptr) *test.vtable[1])(&test));
}
[/php]

so now you also know what a vtable does cuz it means just setting ONE pointer in the object for ALL the virtual methods of said class :)

---

### Post by AlexanderPike on 2011-02-19
That is pretty interesting. Would you say that was idomatic? I can imagine with alot of methods that works much better.

I just found this PDF which looks pretty interesting [http://www.planetpdf.com/codecuts/pdfs/ooc.pdf](http://www.planetpdf.com/codecuts/pdfs/ooc.pdf) discussing oo using ansi c, but it looks to be a pretty hefty read.

---

### Post by trent.josephsen on 2011-02-19
Idiomatic C doesn't try to emulate C++.

---

### Post by worksofcraft on 2011-02-19
> **AlexanderPike said:**
> That is pretty interesting. Would you say that was idomatic? I can imagine with alot of methods that works much better.

I just found this PDF which looks pretty interesting [http://www.planetpdf.com/codecuts/pdfs/ooc.pdf](http://www.planetpdf.com/codecuts/pdfs/ooc.pdf) discussing oo using ansi c, but it looks to be a pretty hefty read.

Soz IDK what idomatic means, but I do know that originally C++ was just done as preprocessor for standard C and then you could see it was producing that kind of thing for the compiler to compile.

---

