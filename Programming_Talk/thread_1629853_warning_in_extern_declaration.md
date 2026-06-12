---
title: "warning in extern declaration"
date: 2010-11-24
forum: Programming Talk
---

### Post by jamesbon on 2010-11-24
```
#include<stdio.h>
#include<stdlib.h>
#define GREY 1
#define BLACK 0
#define WHITE 2
typedef struct node * graph;
typedef struct stack * snode;

graph cnode(int data);          //cnode is to create a node for graph
void cgraph(void);
struct node {
        int data, color;
        struct node *LEFT, *RIGHT, *TOP, *DOWN;
};//this structure defines a node of the graph

struct stack {
struct stack *priv;
struct cgraph *graph_node;
};// this is to define a structure which should hold node of a structure

extern snode sroot;

```
I defined a header file (declaration.h) as above and following is a c program(stack.c)
 I am making which would be used in the library I am developing
```
#include<declarations.h>
void cstack (graph temp);
void stackpush(snode stemp);
extern int stack_counter = 0;
 
sroot=NULL;
void cstack (graph gtemp) //cstack is to create stack
{
   snode spriv,some;
  if (stack_counter==0)
  {
   sroot=stackpush(gtemp);
    spriv=sroot;
   stack_counter++;
   }
   else{
   some=cstacknode(gtemp);
    some->priv=spriv;
    spriv=some; 
  } 
 
}

//struct stack is representing a stack
//struct node is representing a node in graph

snode  cstacknode (graph gtemp) 
//this function should create a node of the stack which should be storing the graph node as a pointer
{
 snode an;
 an=(snode)malloc(sizeof(snode));
 an->graph_node=gtemp; 
 an->priv=NULL;
 return an;
}

void stackpush(snode stemp)
{

}
```

both the above files are in same directory.
I compiled the above file stack.c
```
cc -I ./ stack.c
```
I following  warnings
```

**stack.c:4: warning: ‘stack_counter’ initialized and declared ‘extern’**
stack.c:6: warning: data definition has no type or storage class
stack.c:6: error: conflicting types for ‘sroot’
./declarations.h:21: note: previous declaration of ‘sroot’ was here
stack.c:6: warning: initialization makes integer from pointer without a cast
stack.c: In function ‘cstack’:
stack.c:12: warning: passing argument 1 of ‘stackpush’ from incompatible pointer type
stack.c:3: note: expected ‘snode’ but argument is of type ‘graph’
stack.c:12: error: void value not ignored as it ought to be
stack.c:13: warning: assignment makes pointer from integer without a cast
stack.c:17: warning: assignment makes pointer from integer without a cast
stack.c: At top level:
stack.c:27: error: conflicting types for ‘cstacknode’
stack.c:17: note: previous implicit declaration of ‘cstacknode’ was here
stack.c: In function ‘cstacknode’:
stack.c:32: warning: assignment from incompatible pointer type

```

I want to know when I declared a variable as extern which I have marked bold why do I get that as a warning any thoughts on that and if some one wants to share any other thing on remaining errors then let me know.
My reason by this post is to understand the warning due to extern declaration.

---

### Post by Arndt on 2010-11-24
> **jamesbon said:**
> ```
#include<stdio.h>
#include<stdlib.h>
#define GREY 1
#define BLACK 0
#define WHITE 2
typedef struct node * graph;
typedef struct stack * snode;

graph cnode(int data);          //cnode is to create a node for graph
void cgraph(void);
struct node {
        int data, color;
        struct node *LEFT, *RIGHT, *TOP, *DOWN;
};//this structure defines a node of the graph

struct stack {
struct stack *priv;
struct cgraph *graph_node;
};// this is to define a structure which should hold node of a structure

extern snode sroot;

```
I defined a header file (declaration.h) as above and following is a c program(stack.c)
 I am making which would be used in the library I am developing
```
#include<declarations.h>
void cstack (graph temp);
void stackpush(snode stemp);
extern int stack_counter = 0;
 
sroot=NULL;
void cstack (graph gtemp) //cstack is to create stack
{
   snode spriv,some;
  if (stack_counter==0)
  {
   sroot=stackpush(gtemp);
    spriv=sroot;
   stack_counter++;
   }
   else{
   some=cstacknode(gtemp);
    some->priv=spriv;
    spriv=some; 
  } 
 
}

//struct stack is representing a stack
//struct node is representing a node in graph

snode  cstacknode (graph gtemp) 
//this function should create a node of the stack which should be storing the graph node as a pointer
{
 snode an;
 an=(snode)malloc(sizeof(snode));
 an->graph_node=gtemp; 
 an->priv=NULL;
 return an;
}

void stackpush(snode stemp)
{

}
```

both the above files are in same directory.
I compiled the above file stack.c
```
cc -I ./ stack.c
```
I following  warnings
```

**stack.c:4: warning: ‘stack_counter’ initialized and declared ‘extern’**
stack.c:6: warning: data definition has no type or storage class
stack.c:6: error: conflicting types for ‘sroot’
./declarations.h:21: note: previous declaration of ‘sroot’ was here
stack.c:6: warning: initialization makes integer from pointer without a cast
stack.c: In function ‘cstack’:
stack.c:12: warning: passing argument 1 of ‘stackpush’ from incompatible pointer type
stack.c:3: note: expected ‘snode’ but argument is of type ‘graph’
stack.c:12: error: void value not ignored as it ought to be
stack.c:13: warning: assignment makes pointer from integer without a cast
stack.c:17: warning: assignment makes pointer from integer without a cast
stack.c: At top level:
stack.c:27: error: conflicting types for ‘cstacknode’
stack.c:17: note: previous implicit declaration of ‘cstacknode’ was here
stack.c: In function ‘cstacknode’:
stack.c:32: warning: assignment from incompatible pointer type

```

I want to know when I declared a variable as extern which I have marked bold why do I get that as a warning any thoughts on that and if some one wants to share any other thing on remaining errors then let me know.
My reason by this post is to understand the warning due to extern declaration.

What does your book say?

---

### Post by spjackson on 2010-11-24
> **jamesbon said:**
> 
```
cc -I ./ stack.c
```I following  warnings
```

**stack.c:4: warning: ‘stack_counter’ initialized and declared ‘extern’**
stack.c:6: warning: data definition has no type or storage class
stack.c:6: error: conflicting types for ‘sroot’
./declarations.h:21: note: previous declaration of ‘sroot’ was here
stack.c:6: warning: initialization makes integer from pointer without a cast
stack.c: In function ‘cstack’:
stack.c:12: warning: passing argument 1 of ‘stackpush’ from incompatible pointer type
stack.c:3: note: expected ‘snode’ but argument is of type ‘graph’
stack.c:12: error: void value not ignored as it ought to be
stack.c:13: warning: assignment makes pointer from integer without a cast
stack.c:17: warning: assignment makes pointer from integer without a cast
stack.c: At top level:
stack.c:27: error: conflicting types for ‘cstacknode’
stack.c:17: note: previous implicit declaration of ‘cstacknode’ was here
stack.c: In function ‘cstacknode’:
stack.c:32: warning: assignment from incompatible pointer type

```I want to know when I declared a variable as extern which I have marked bold why do I get that as a warning any thoughts on that and if some one wants to share any other thing on remaining errors then let me know.
My reason by this post is to understand the warning due to extern declaration.
Broadly speaking, extern in a C declaration means "I am declaring it here so I can use it, but the definition is elsewhere." Assigning a value in a declaration means "I am defining it right here." So your declaration is contradictory.

Here are the corrections to your warnings and errors on lines 4 and 6.
```

#include<declarations.h>
void cstack (graph temp);
void stackpush(snode stemp);
int stack_counter = 0;

snode sroot=NULL;

```Global variables are not recommended, however.

---

### Post by jamesbon on 2010-11-24
> **spjackson said:**
> Broadly speaking, extern in a C declaration means "I am declaring it here so I can use it, but the definition is elsewhere." Assigning a value in a declaration means "I am defining it right here." So your declaration is contradictory.
.
Ok thanks for the great explanation.My purpose is to have a global variable that is how
I want to implement my logic.
I modified the program by the understanding based on your explanation.
So now I have declarations.h
```

#include<stdio.h>
#include<stdlib.h>
#define GREY 1
#define BLACK 0
#define WHITE 2
typedef struct node * graph;
typedef struct stack * snode;
extern int stack_counter;
graph cnode(int data);          //cnode is to create a node for graph
void cgraph(void);
struct node {
        int data, color;
        struct node *LEFT, *RIGHT, *TOP, *DOWN;
};//this structure defines a node of the graph

struct stack {
struct stack *priv;
struct cgraph *graph_node;
};// this is to define a structure which should hold node of a structure

extern snode sroot;


```
and the file stack.c is modified to following 
```

#include<declarations.h>
void cstack (graph temp);
void stackpush(snode stemp);
 stack_counter = 0;
 
sroot=NULL;
void cstack (graph gtemp) //cstack is to create stack
{
   snode spriv,some;
  if (stack_counter==0)
  {
   sroot=cstacknode(gtemp);
    spriv=sroot;
   stack_counter++;
   }
   else{
   some=cstacknode(gtemp);
    some->priv=spriv;
    spriv=some; 
  } 
 
}

//struct stack is representing a stack
//struct node is representing a node in graph

snode  cstacknode (graph gtemp) 
//this function should create a node of the stack which should be storing the graph node as a pointer
{
 snode an;
 an=(snode)malloc(sizeof(snode));
 an->graph_node=gtemp; 
 an->priv=NULL;
 return an;
}

void stackpush(snode stemp)
{

}

```

Now when I compile this I get a set of errors 
from that set I want to understand following warnings
```

stack.c:4: warning: data definition has no type or storage class
stack.c:6: warning: data definition has no type or storage class

```
The above warning is coming from file stack.c 
and line 4 and 6 in stack.c  have 
```

 stack_counter = 0;

sroot=NULL;

```
and both the above variables I have defined in declarations.h so why do I get the above warning now?

---

### Post by spjackson on 2010-11-24
> **jamesbon said:**
> 
```

stack.c:4: warning: data definition has no type or storage class
stack.c:6: warning: data definition has no type or storage class

```The above warning is coming from file stack.c 
and line 4 and 6 in stack.c  have 
```

 stack_counter = 0;

sroot=NULL;

```and both the above variables I have defined in declarations.h so why do I get the above warning now?
I already showed you how to write these two lines in my last posting.

You need to specify a type before the variable name in order for it to be a well-formed definition. What you have written looks like variable assignment, but you cannot have variable assignment outside a function, only initialization.

---

### Post by jamesbon on 2010-11-24
> **spjackson said:**
> I already showed you how to write these two lines in my last posting.

You need to specify a type before the variable name in order for it to be a well-formed definition. What you have written looks like variable assignment, but you cannot have 
variable assignment outside a function, only initialization.
Ohh sorry for my poor understanding now I understand what you wanted to say.

---

### Post by jamesbon on 2010-11-24
> **spjackson said:**
> Broadly speaking, extern in a C declaration  means "I am declaring it here so I can use it, but the definition is  elsewhere." Assigning a value in a declaration means "I am defining it  right here." So your declaration is contradictory.



I think now I have modified same as you said.Declared the variables in declarations.h and defined them stack.c ,so my understanding is I should not get this warning.

---

### Post by trent.josephsen on 2010-11-24
> **jamesbon said:**
> ```

typedef struct node * graph;
typedef struct stack * snode;
```


WHY?  WHY, WHY, WHY? ](*,)

I'm beginning to think **typedef** should have been left out of the language entirely.

---

### Post by jamesbon on 2010-11-24
> **trent.josephsen said:**
> WHY?  WHY, WHY, WHY? ](*,)

I'm beginning to think **typedef** should have been left out of the language entirely.


what is wrong with typedef

---

### Post by jamesbon on 2010-11-24
what is wrong with typedef

---

### Post by jamesbon on 2010-11-24
What is wrong with that typedef?

---

### Post by jamesbon on 2010-11-24
> **Arndt said:**
> What does your book say?
*K Ritchie Page 33* > 
"If the program is in several source files, and a variable is defined in file1 and used in file2 and file3, then extern declarations are needed in file2 and file3 to connect the occurrences of the variable."Checked Chapter 4 and appendinx B nothing useful.I don't think that I did any mistake in code after **spjakson** modifications.

---

### Post by jamesbon on 2010-11-24
I made another program **temp2.h**
```
extern i;
```
which contains just one above line
and made another file 
temp3.c
```
#include<stdio.h>
#include<temp2.h>
int main ()
{
extern i;
i=6;
printf("The i is %d",i);
}

```
When I compiled above as 
```
cc -I ./ temp3.c 
```I got following errors
```
/tmp/ccJcwZyy.o: In function `main':
temp3.c:(.text+0x6): undefined reference to `i'
temp3.c:(.text+0x10): undefined reference to `i'
collect2: ld returned 1 exit status

```
I had declared extern in temp3.c above as K R page 33 says as I mentioned in  above post.
I tried another way for temp3.c with same header file temp2.h
```
#include<stdio.h>
#include<temp2.h>
int main ()
{

i=6;
printf("The i is %d",i);
}

```
and compiled it ```
cc -I ./ temp3.c 
```
and got following error
```

/tmp/ccZZyGsL.o: In function `main':
temp3.c:(.text+0x6): undefined reference to `i'
temp3.c:(.text+0x10): undefined reference to `i'
collect2: ld returned 1 exit status


```
I also tried 
```
#include<stdio.h>
#include<temp2.h>
int main ()
{
extern i=6;
printf("The i is %d",i);
}
```
compiled this one
```
cc -I ./ temp3.c 

```got same error as in post 1```
temp3.c: In function ‘main’:
temp3.c:5: error: ‘i’ has both ‘extern’ and initializer

```
So I have tried at least 3 different ways to use extern but non of them worked.

---

### Post by Arndt on 2010-11-24
> **jamesbon said:**
> I made another program **temp2.h**
```
extern i;
```
which contains just one above line
and made another file 
temp3.c
```
#include<stdio.h>
#include<temp2.h>
int main ()
{
extern i;
i=6;
printf("The i is %d",i);
}

```
When I compiled above as 
```
cc -I ./ temp3.c 
```I got following errors
```
/tmp/ccJcwZyy.o: In function `main':
temp3.c:(.text+0x6): undefined reference to `i'
temp3.c:(.text+0x10): undefined reference to `i'
collect2: ld returned 1 exit status

```
I had declared extern in temp3.c above as K R page 33 says as I mentioned in  above post.
I tried another way for temp3.c with same header file temp2.h
```
#include<stdio.h>
#include<temp2.h>
int main ()
{

i=6;
printf("The i is %d",i);
}

```
and compiled it ```
cc -I ./ temp3.c 
```
and got following error
```

/tmp/ccZZyGsL.o: In function `main':
temp3.c:(.text+0x6): undefined reference to `i'
temp3.c:(.text+0x10): undefined reference to `i'
collect2: ld returned 1 exit status


```
I also tried 
```
#include<stdio.h>
#include<temp2.h>
int main ()
{
extern i=6;
printf("The i is %d",i);
}
```
compiled this one
```
cc -I ./ temp3.c 

```got same error as in post 1```
temp3.c: In function ‘main’:
temp3.c:5: error: ‘i’ has both ‘extern’ and initializer

```
So I have tried at least 3 different ways to use extern but non of them worked.

1) How recent is your book? Leaving out the type in "extern i;" is _very_ old style, even if it perhaps is still supported. If it covers C90, I think you're fine. C99, even better, but earlier than 90 will give you problems.

2) "extern" says that a variable exists, and that it is defined elsewhere. But in the end, you must define it somewhere. You haven't done so.

There have actually existed compilers/linkers which together helped the programmer by automatically adding a storage place for a variable which was only ever declared extern. But this interpretation was not dominating, and it may be the case that the standard (C90 or C99) forbids it now.

---

### Post by jamesbon on 2010-11-25
> **Arndt said:**
> 1) How recent is your book? Leaving out the type in "extern i;" is _very_ old style, even if it perhaps is still supported. If it covers C90, I think you're fine. C99, even better, but earlier than 90 will give you problems.

I have second edition of KR.
> **Arndt said:**
> 
2) "extern" says that a variable exists, and that it is defined elsewhere. But in the end, you must define it somewhere. You haven't done so.

I have done it.
See the file declarations.h
```

#include<stdio.h>
#include<stdlib.h>
#define GREY 1
#define BLACK 0
#define WHITE 2
typedef struct node * graph;
typedef struct stack * snode;
graph cnode(int data);          //cnode is to create a node for graph
void cgraph(void);
struct node {
        int data, color;
        struct node *LEFT, *RIGHT, *TOP, *DOWN;
};//this structure defines a node of the graph

struct stack {
struct stack *priv;
struct cgraph *graph_node;
};// this is to define a structure which should hold node of a structure

[B]extern snode sroot;
extern int stack_counter;
[/B]                             

```
In the last 2 lines above I have declared the variables and in stack.c I have defined them see this file stack.c
```
#include<declarations.h>
void cstack (graph temp);
void stackpush(snode stemp);
 stack_counter = 0;
 
sroot=NULL;
void cstack (graph gtemp) //cstack is to create stack
{
   snode spriv,some;
  if (stack_counter==0)
  {
   sroot=cstacknode(gtemp);
    spriv=sroot;
   stack_counter++;
   }
   else{
   some=cstacknode(gtemp);
    some->priv=spriv;
    spriv=some; 
  } 
 
}

//struct stack is representing a stack
//struct node is representing a node in graph

snode  cstacknode (graph gtemp) 
//this function should create a node of the stack which should be storing the graph node as a pointer
{
 snode an;
 an=(snode)malloc(sizeof(snode));
 an->graph_node=gtemp; 
 an->priv=NULL;
 return an;
}

void stackpush(snode stemp)
{

}
```
Is this some thing different than declaring and defining in separate files?
I have checked this article on[ wikipedia]("http://en.wikipedia.org/wiki/External_variable#Definition.2C_declaration_and_the_extern_keyword").
Have I done some mistake now in the above two files?
Because now when I compile stack.c
as ```
cc -I ./ stack.c
```
I get a warning 
```
[B]stack.c:4: warning: data definition has no type or storage class
stack.c:6: warning: data definition has no type or storage class[/B]
stack.c:6: error: conflicting types for ‘sroot’
./declarations.h:20: note: previous declaration of ‘sroot’ was here
stack.c:6: warning: initialization makes integer from pointer without a cast
stack.c: In function ‘cstack’:
stack.c:13: warning: assignment makes pointer from integer without a cast
stack.c:17: warning: assignment makes pointer from integer without a cast
stack.c: At top level:
stack.c:27: error: conflicting types for ‘cstacknode’
stack.c:12: note: previous implicit declaration of ‘cstacknode’ was here
stack.c: In function ‘cstacknode’:
stack.c:32: warning: assignment from incompatible pointer type

```
Where as **stack_counter** and **sroot** were declared in delcarations.h and defined in stack.c so why is this error coming now?

---

### Post by jamesbon on 2010-11-25
> **trent.josephsen said:**
> WHY?  WHY, WHY, WHY? ](*,)

I'm beginning to think **typedef** should have been left out of the language entirely.
To verify your typedef reply I made another set of files here it is
temp1.h
```
#include<stdlib.h>
typedef struct node * bond;

```and temp2.c
```
#include<stdio.h>
#include<temp1.h>
struct node {
int data;
};
int main ()
{
bond t1;
t1=(bond)malloc(sizeof(bond));
t1->data=23;
printf("the data is %d\n",t1->data);
}

```I compiled it ```

cc -I ./ -g temp2.c 
bond@bond:~/$ ./a.out 
the data is 23

```So  I do not see any thing wrong with typedef the only problem is coming is with extern.

---

### Post by jamesbon on 2010-11-25
> **spjackson said:**
> Broadly speaking, extern in a C declaration means "I am declaring it here so I can use it, but the definition is elsewhere." Assigning a value in a declaration means "I am defining it right here." So your declaration is contradictory.

My understanding says
```
extern int x;  // Declares x
 int x;  // Declares x and defines x
 int x=0;  // Declares x and defines x and initializes x to 0
 x=0;  // Sets x to 0.
```
> **spjackson said:**
> 
#include<declarations.h>
void cstack (graph temp);
void stackpush(snode stemp);
int stack_counter = 0;

snode sroot=NULL;

Is this way declaration or definition of stack_counter ?
Do declarations.h has a line 

```
extern int stack_counter 
```along with your above said change in stack.c?

---

### Post by Arndt on 2010-11-25
> **jamesbon said:**
> I have second edition of KR.

I have done it.
See the file declarations.h
```

#include<stdio.h>
#include<stdlib.h>
#define GREY 1
#define BLACK 0
#define WHITE 2
typedef struct node * graph;
typedef struct stack * snode;
graph cnode(int data);          //cnode is to create a node for graph
void cgraph(void);
struct node {
        int data, color;
        struct node *LEFT, *RIGHT, *TOP, *DOWN;
};//this structure defines a node of the graph

struct stack {
struct stack *priv;
struct cgraph *graph_node;
};// this is to define a structure which should hold node of a structure

[B]extern snode sroot;
extern int stack_counter;
[/B]                             

```
In the last 2 lines above I have declared the variables and in stack.c I have defined them see this file stack.c
```
#include<declarations.h>
void cstack (graph temp);
void stackpush(snode stemp);
 stack_counter = 0;
 
sroot=NULL;
void cstack (graph gtemp) //cstack is to create stack
{
   snode spriv,some;
  if (stack_counter==0)
  {
   sroot=cstacknode(gtemp);
    spriv=sroot;
   stack_counter++;
   }
   else{
   some=cstacknode(gtemp);
    some->priv=spriv;
    spriv=some; 
  } 
 
}

//struct stack is representing a stack
//struct node is representing a node in graph

snode  cstacknode (graph gtemp) 
//this function should create a node of the stack which should be storing the graph node as a pointer
{
 snode an;
 an=(snode)malloc(sizeof(snode));
 an->graph_node=gtemp; 
 an->priv=NULL;
 return an;
}

void stackpush(snode stemp)
{

}
```
Is this some thing different than declaring and defining in separate files?
I have checked this article on[ wikipedia]("http://en.wikipedia.org/wiki/External_variable#Definition.2C_declaration_and_the_extern_keyword").
Have I done some mistake now in the above two files?
Because now when I compile stack.c
as ```
cc -I ./ stack.c
```
I get a warning 
```
[B]stack.c:4: warning: data definition has no type or storage class
stack.c:6: warning: data definition has no type or storage class[/B]
stack.c:6: error: conflicting types for ‘sroot’
./declarations.h:20: note: previous declaration of ‘sroot’ was here
stack.c:6: warning: initialization makes integer from pointer without a cast
stack.c: In function ‘cstack’:
stack.c:13: warning: assignment makes pointer from integer without a cast
stack.c:17: warning: assignment makes pointer from integer without a cast
stack.c: At top level:
stack.c:27: error: conflicting types for ‘cstacknode’
stack.c:12: note: previous implicit declaration of ‘cstacknode’ was here
stack.c: In function ‘cstacknode’:
stack.c:32: warning: assignment from incompatible pointer type

```
Where as **stack_counter** and **sroot** were declared in delcarations.h and defined in stack.c so why is this error coming now?

The issue here was with the variable 'i'. You're mixing up your different programs.

---

### Post by jamesbon on 2010-11-25
> **Arndt said:**
> The issue here was with the variable 'i'. You're mixing up your different programs.
I was giving an example for extern thing.I am now clear with extern based on another [discussion.]("http://ubuntuforums.org/showthread.php?p=10160815#post10160815")
and this[ article]("http://en.wikipedia.org/wiki/External_variable#Definition.2C_declaration_and_the_extern_keyword")

---

### Post by Zugzwang on 2010-11-25
> **jamesbon said:**
> To verify your typedef reply I made another set of files here it is
temp1.h
```
#include<stdlib.h>
typedef struct node * bond;

```and temp2.c
```
#include<stdio.h>
#include<temp1.h>
struct node {
int data;
};
int main ()
{
bond t1;
t1=(bond)malloc(sizeof(bond));
t1->data=23;
printf("the data is %d\n",t1->data);
}

```I compiled it ```

cc -I ./ -g temp2.c 
bond@bond:~/$ ./a.out 
the data is 23

```So  I do not see any thing wrong with typedef the only problem is coming is with extern.

I think the criticism came from the fact that you did a typedef to a pointer type. This is very dangerous as it hides the information that you are actually dealing with a pointer. Such a thing will certainly cause problems if you are working with several people on the same project as people will, for example, forget to free() stuff as they don't realise that they are actually dealing with pointers. 

Note that you also fell into the trap of forgetting that you are dealing with a pointer in your program even though you are the only one working on it: the line "t1=(bond)malloc(sizeof(bond));" is incorrect - it allocates a memory region of 4 or 8 bytes, depending on your platform, even though the structure "node" might be larger. So it is better to write "t1=(bond)malloc(sizeof(node));" instead. Also, you forgot to free "t1" in your main program.

---

### Post by Arndt on 2010-11-25
> **jamesbon said:**
> I was giving an example for extern thing.I am now clear with extern based on another [discussion.]("http://ubuntuforums.org/showthread.php?p=10160815#post10160815")
and this[ article]("http://en.wikipedia.org/wiki/External_variable#Definition.2C_declaration_and_the_extern_keyword")

Yes, you started a new thread with the same question, after I had already answered it here, and you had read the answer.

---

### Post by spjackson on 2010-11-25
> **jamesbon said:**
> I was giving an example for extern thing.I am now clear with extern based on another [discussion.]("http://ubuntuforums.org/showthread.php?p=10160815#post10160815")
and this[ article]("http://en.wikipedia.org/wiki/External_variable#Definition.2C_declaration_and_the_extern_keyword")
Good. Now that you have learned what extern does, hopefully you will rarely, if ever, use extern variables.

---

### Post by jamesbon on 2010-11-25
> **spjackson said:**
> Good. Now that you have learned what extern does, hopefully you will rarely, if ever, use extern variables.

My programming logic is like that I am using extern.
All the errors got resolved.
Here are the correct programs.
declarations.h
```
#include<stdio.h>
#include<stdlib.h>
#define GREY 1
#define BLACK 0
#define WHITE 2

struct node {
        int data, color;
        struct node *LEFT, *RIGHT, *TOP, *DOWN;
};//this structure defines a node of the graph

struct stack {
struct stack *priv;
struct node *graph_node;
};// this is to define a structure which should hold node of a structure

typedef struct node * graph;
typedef struct stack * snode;
graph cnode(int data);          //cnode is to create a node for graph
void cgraph(void);
extern snode sroot;
extern int stack_counter;
~
```
and stack.c is
```

#include<declarations.h>
void cstack(graph temp);
void stackpush(snode stemp);
snode cstacknode(graph gtemp);
int stack_counter = 0;

snode sroot = NULL;
void cstack(graph gtemp)	//cstack is to create stack
{
	snode spriv, some;
	if (stack_counter == 0) {
		sroot = cstacknode(gtemp);
		spriv = sroot;
		stack_counter++;
	} else {
		some = cstacknode(gtemp);
		some->priv = spriv;
		spriv = some;
	}

}

//struct stack is representing a stack
//struct node is representing a node in graph

snode cstacknode(graph gtemp)
//this function should create a node of the stack which should be storing the graph node as a pointer
{
	snode an;
	an = (snode) malloc(sizeof(snode));
	an->graph_node = gtemp;
	an->priv = NULL;
	return an;
}

void stackpush(snode stemp)
{

}

```

---

### Post by spjackson on 2010-11-25
> **jamesbon said:**
> [QUOTE=spjackson]Good. Now that you have learned what extern does, hopefully you will rarely, if ever, use extern variables.My programming logic is like that I am using extern.
All the errors got resolved.
[/QUOTE]
My mistake, I thought you were just using extern variables in order to learn how they work. Please be warned against a style that favours global variables over encapsulation.

There are perhaps some corner cases where the advantages of using extern variables outweigh the disadvantages, but in the general case they are best avoided. K&R chapter 1, Tutorial Introduction 1.10 External Variables and Scope. "By the way, there is a tendency to make everything in sight an extern variable because it appears to simplify communications - argument lists are short and variables are always there when you want them. But external variables are always there even when you don't want them. Relying too heavily on external variables is fraught with peril since it leads to programs whose data connections are not at all obvious - variables can be changed in unexpected and even inadvertent ways, and the program is hard to modify." But you know that already, because you've read it.

---

### Post by nvteighen on 2010-11-25
Global variables are there for stuff that's only relevant at global scope... usually, stuff related to execution diagnosis. The most well-known case is errno, which is just a place to save the last known error code in order to do error diagnosis and handling. As you see, it's not a variable that affects the program's task but affects the program's execution in exceptional cases.

I really tend to think errno is the only senseful use of global variables, though there might be some other cases involving const variables. Anyway, global stuff, if needed, should always refer to global conditions and never to local ones.

---

