---
title: "How to make a struct with global scope?"
date: 2007-04-02
forum: Programming Talk
---

### Post by elb on 2007-04-02
C language question: How do I properly do something like this?

struct program_build_info {
  char* version_string;
} foo;

foo.version_string = "x.y.z";

int main(void){
   printf("version is %s\n", foo.version_string);
   return 0;
}

I guess my intentions here are obvious (I plan to keep the stuff above main in its own file and have the build script substitute information, e.g. x.y.z).  I need static data in a header file, and to avoid naming conflicts in C, I'd like to keep that data within a weirdly-named instance of a struct.  

Unfortunately the code above does not compile.  See error message below.  I think perhaps a well-placed "static" or "extern" might solve my problem, but I can't seem to figure it out.

main.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘.’ token

---

### Post by rplantz on 2007-04-02
You cannot have executable code outside a function. The syntax is (note that I've added another field to illustrate how to initialize more than one):
```

#include <stdio.h>

struct program_build_info {
   char* version_string;
   int x;
} foo = {"x.y.z", 123};

int main(void){
   printf("version is %s\n", foo.version_string);
   printf("and x = %i\n", foo.x);
   return 0;
}

```

---

