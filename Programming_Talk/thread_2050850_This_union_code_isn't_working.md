---
title: "This union code isn't working"
date: 2012-08-31
forum: Programming Talk
---

### Post by trilobite on 2012-08-31
Hi all - 
I've done this bit of code (to play around with eventually making a "tuple" in C). 
```
 

#include <string.h>   
#include <stdio.h> 
#include <stdlib.h>  


/* ints */ 
typedef struct  { 
     int type ; 
     int val; 
}  myint; 


/* Strings */ 
typedef struct  { 
     int type ; 
     char *val; 
}  mystr; 


/* Chars */ 
typedef struct  { 
     int type ; 
     char val; 
}  mychar; 


/* Floats */ 
typedef struct { 
     int type ; 
     float val; 
}  myfloat; 


/* Combine them into a union. */ 
typedef union {  
	     myint    *i; 
         mystr    *s; 
         mychar   *c; 
         myfloat  *f; 
}  mytype ; 


void myfunc(mytype *mt) 
{ 
       if (mt->i->type == 1)  puts("m is an integer \n");           
  else if (mt->s->type == 2)  puts("m is an array \n"); 
  else if (mt->c->type == 3)  puts("m is a char \n"); 
  else if (mt->f->type == 4)  puts("m is a float \n");  
  
} 


int main(void) 
{ 
	
myint foo;
foo.type = 1; 
foo.val = 123; 

mystr bar; 
bar.type = 2; 
bar.val = "Testing..." ; 

mychar baz; 
baz.type = 3; 
baz.val = '@' ;

myfloat abc; 
abc.type = 4; 
abc.val = 42.42 ; 

/* Create the unions */ 
mytype *test1; 
test1.i.type = foo.type;
test1.i.val  = foo.val;   
 
mytype *test2;  
test2.s.type = bar.type;
test2.s.val = bar.val; 

mytype *test3;  
test3.c.type = baz.type;
test3.c.val = baz.val; 

mytype *test4;  
test4.f.type = abc.type;
test4.f.val = abc.val; 
 			
return 0; 	
	
} 	

``` 

However, when compiled, these messages appear - 
** start of messages **
gcc -Wall -o  "pseudo_typeof2" "pseudo_typeof2.c"  (in directory: /home/andy/pd_pseudo_typeof)
Compilation failed.
pseudo_typeof2.c: In function ‘main’:
pseudo_typeof2.c:84:6: error: request for member ‘i’ in something not a structure or union
pseudo_typeof2.c:85:6: error: request for member ‘i’ in something not a structure or union
pseudo_typeof2.c:88:6: error: request for member ‘s’ in something not a structure or union
pseudo_typeof2.c:89:6: error: request for member ‘s’ in something not a structure or union
pseudo_typeof2.c:92:6: error: request for member ‘c’ in something not a structure or union
pseudo_typeof2.c:93:6: error: request for member ‘c’ in something not a structure or union
pseudo_typeof2.c:96:6: error: request for member ‘f’ in something not a structure or union
pseudo_typeof2.c:97:6: error: request for member ‘f’ in something not a structure or union
pseudo_typeof2.c:95:9: warning: variable ‘test4’ set but not used [-Wunused-but-set-variable]
pseudo_typeof2.c:91:9: warning: variable ‘test3’ set but not used [-Wunused-but-set-variable]
pseudo_typeof2.c:87:9: warning: variable ‘test2’ set but not used [-Wunused-but-set-variable]
pseudo_typeof2.c:83:9: warning: variable ‘test1’ set but not used [-Wunused-but-set-variable]
** end of messages **	

I usually have no problem with structs, but unions always seem to be a problem. 
So - what is going on here, and how can it be fixed.....?  
Many thanks in advance - 
- t

---

### Post by Bachstelze on 2012-08-31
Read about the difference between . and ->.

*EDIT:* And you have another big problem but I will let you figure it out by yourself...

---

### Post by trilobite on 2012-08-31
> **Bachstelze said:**
> Read about the difference between . and ->.

*EDIT:* And you have another big problem but I will let you figure it out by yourself...

Hi Bachstelze, thanks for your reply -   
I've made some changes and have got the code compiling without errors or warnings now. I do get a segfault when running the executable though, so I'll keep at it...

I apologise for my denseness.... :) 
- t

---

### Post by steeldriver on 2012-08-31
HINT: what does

```
mytype *test1;
```

actually create?

---

