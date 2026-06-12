---
title: "C pointers"
date: 2010-06-04
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-06-04
I have this problem pushing me crazy ! 
```
int delete_(BT t,int d){
    BT * B=BelongR(t,d);
	printf("\naddress %p value at adress %d",B,(*B)->data);
	printf("\naddress %p value at adress %d",B,(*B)->data);
    return delete_root(B);
}
```
I got this when running 
```
address 0031FB40 value at address 5
address 0031FB40 value at address 3276320
```

---

### Post by jobix on 2010-06-04
Not sure what the problem is. Are you referring to the fact that the last numbers are different, i.e., 5 vs 3276320? This could be because that seems to be the value of "data". Can't tell by looking at the code snippet you provided, but I'm guessing that this value is getting changed somewhere. Maybe in the BelongR() function?

---

### Post by trent.josephsen on 2010-06-04
What is the definition of BT?  How about BelongR?  delete_root?  How are you calling this function?  What did you expect to happen?  For what it's worth, this appears to be perfectly valid C code.

---

### Post by cap10Ibraim on 2010-06-04
> **jobix said:**
> Not sure what the problem is. Are you referring to the fact that the last numbers are different, i.e., 5 vs 3276320? This could be because that seems to be the value of "data". 
yes that's my problem 
both printf are called after BelongR() 
I was expecting 5 after calling BelongR()
it appears in the first printf
but in the second line value is changed without calling anything :confused:

---

### Post by John Bean on 2010-06-04
The run results you posted didn't come from that code snippet - unless someone hid a spellchecker inside printf ;-)

Clue: "adress" (snippet) -> "address" (output)

---

### Post by ibuclaw on 2010-06-04
> **John Bean said:**
> The run results you posted didn't come from that code snippet - unless someone hid a spellchecker inside printf ;-)

Clue: "adress" (snippet) -> "address" (output)

Also, I don't believe that:
```
(*B)->data
```
is valid as an argument for "%d" in your printf example... It should be:
```
(*B).data
```
Unless your compiler is special. :3

---

### Post by cap10Ibraim on 2010-06-04
> **ibuclaw said:**
> Also, I don't believe that:
```
(*B)->data
```
is valid as an argument for "%d" in your printf example... It should be:
```
(*B).data
```
Unless your compiler is special. :3
it's a pointer to a pointer 
here is the data structure for BT 
```
typedef struct node {
	element data;
	node *left,*right;
}*BT;
```
here is BelongR
```
BT * BelongR(BT t,int d){
    if(t==NULL)return 0;
    if(t->data==d)return &t;
    if(t->data>d) BelongR(t->left,d);
    else BelongR(t->right,d);
}
```

---

### Post by cap10Ibraim on 2010-06-04
maybe windows 7 doesn't respect my variables and heap 
i'll try it later with NetBeans on Ubuntu

---

### Post by jobix on 2010-06-04
Never mind, #7 and #8 got posted while I was composing my reply.

---

### Post by John Bean on 2010-06-04
> **cap10Ibraim said:**
> it's a pointer to a pointer 
here is the data structure for BT 
```
typedef struct node {
    element data;
    node *left,*right;
}*BT;
```here is BelongR
```
BT * BelongR(BT t,int d){
    if(t==NULL)return 0;
    if(t->data==d)return &t;
    if(t->data>d) BelongR(t->left,d);
    else BelongR(t->right,d);
}
```

This is hopeless, you keep posting snippets that contain undefined data types. What's the definition of a "element" for example?

---

### Post by ibuclaw on 2010-06-04
> **John Bean said:**
> This is hopeless, you keep posting snippets that contain undefined data types. What's the definition of a "element" for example?

I presume it's a "typedef int".

---

### Post by ibuclaw on 2010-06-04
> **cap10Ibraim said:**
> 
here is BelongR
```
BT * BelongR(BT t,int d){
    if(t==NULL)return 0;
    if(t->data==d)return &t;
    if(t->data>d) BelongR(t->left,d);
    else BelongR(t->right,d);
}
```

Looks like you trying to return the address of local variable ...


If you compiled with -Wall -Werror, you can prevent such mistakes. ;)

---

### Post by John Bean on 2010-06-04
> **ibuclaw said:**
> I presume it's a "typedef int".

I suspect it isn't... :-(

I worked for many years with a programmer who wrote code like this, it drove the rest of us nuts when we had to review his code. 

I come from the KISS school of programming; complexity in programming is often a fact of life but there's no need to make it worse by adding gratuitous extra levels of it just because you can.

---

### Post by trent.josephsen on 2010-06-04
> **cap10Ibraim said:**
> it's a pointer to a pointer 
here is the data structure for BT 
```
typedef struct node {
	element data;
	node *left,*right;
```
That's C++, not C.  C requires the use of the 'struct' keyword here.  Probably not related to your problem, but it's just one indication that you're still not being totally honest with us.
> ```
}*BT;
```
here is BelongR
```
BT * BelongR(BT t,int d){
    if(t==NULL)return 0;
    if(t->data==d)return &t;
    if(t->data>d) BelongR(t->left,d);
    else BelongR(t->right,d);
}
```

Why the typedef in the first place?  Use 'struct node'.

Also, you're passing printf a value of type 'element' (whatever that is), giving it a "%d" format specifier, and calling it an address.  What is it?

---

### Post by dwhitney67 on 2010-06-04
> **cap10Ibraim said:**
> 
here is BelongR
```
BT * BelongR(BT t,int d){
    if(t==NULL)return 0;
    if(t->data==d)return &t;
    if(t->data>d) BelongR(t->left,d);
    else BelongR(t->right,d);
}
```
EDIT:  Nevermind.  It's highly probably that you also have issues with copying/pasting code.  Otherwise the code above would never have compiled.

----------------------------

That's screwed up; if 't->data' does indeed equal the value of 'd', then you are returning the address of a local variable 't'.  That's an error.

To fix the problem, pass the address of the BT object to the function.  For example:
```

BT* BelongR(BT* t, int data)
{
   ...
}

```

---

### Post by cap10Ibraim on 2010-06-04
> **John Bean said:**
>  What's the definition of a "element" for example?

:P element is int 
I expected that maybe someone had experienced something similar 
the main question is why printing the same thing directly after each other showed different results

---

### Post by cap10Ibraim on 2010-06-04
> **ibuclaw said:**
> Looks like you trying to return the address of local variable ...


If you compiled with -Wall -Werror, you can prevent such mistakes. ;)

[COLOR="Red"][SIZE="5"]the variables are allocated in the heap and it's a run time error the code did compile[/SIZE] [/COLOR]
the first printf() managed to access it successfully

---

### Post by dwhitney67 on 2010-06-04
> **cap10Ibraim said:**
> :P element is int 
I expected that maybe someone had experienced something similar 
the main question is why printing the same thing directly after each other showed different results

Would the world come to an end if you were to post ALL of your code?

If you were to post ALL of your code, then maybe someone else can try to duplicate the problem you are seeing.

---

### Post by cap10Ibraim on 2010-06-04
> **dwhitney67 said:**
> Would the world come to an end if you were to post ALL of your code?

If you were to post ALL of your code, then maybe someone else can try to duplicate the problem you are seeing.

It's  2 cpp files and 2 headers

---

### Post by dwhitney67 on 2010-06-04
> **cap10Ibraim said:**
> It's  2 cpp files and 2 headers

And the problem is...???

Open each of your files using gedit or whatever editor, select all, copy and then paste into your next post here on Ubuntu Forums.  Don't forget to surround your code with the CODE tags.

P.S.  Your thread title indicates you are coding in C, yet your files have a .cpp extension?  Typically that extension is used for C++ projects.

---

### Post by dwhitney67 on 2010-06-04
Before posting your code, please fix the basics.  Try something like this:
```

typedef int element;    // this is dumb

typedef struct Node
{
   element      data;
   struct Node* left;
   struct Node* right;
} Node, BT;


BT* belongR(BT* tree, int data)
{
   if (tree)
   {
      if (tree->data > data) belongR(tree->left, data);

      if (tree->data < data) belongR(tree->right, data);
   }

   return tree;
}


int main()
{
   BT* tree = 0;

   // ...

   return 0;
}

```
Note the typedef for BT has changed, as has the interface for belongR().

---

### Post by cap10Ibraim on 2010-06-04
EDIT : solved

---

### Post by cap10Ibraim on 2010-06-04
> **dwhitney67 said:**
> Before posting your code, please fix the basics.  Try something like this:
```

typedef int element;    // this is dumb

```
.
why dumb? 
if I want to change from int to char , this can reduce the correction

---

### Post by cap10Ibraim on 2010-06-04
WoW ! it worked in Ubuntu , I don't know what the hell was happening in windows check the image in Ubuntu (2 last lines in the picture)

```
address 0x7fffae7d7be8 value at adress 5
address 0x7fffae7d7be8 value at adress 5
```

---

### Post by trent.josephsen on 2010-06-04
If you have to change something later from int to char, your program is already broken.  But that's another topic...

After I fixed the bare "node" declaration I already mentioned, both in the header file and on line 117 of the BTdynamic.c you posted, "gcc -W -Wall --std=c99" had this to say about your program:

```
BTdynamic.c: In function "isEmpty":
BTdynamic.c:13: warning: control reaches end of non-void function
BTdynamic.c: In function "BelongR":
BTdynamic.c:107: warning: function returns address of local variable
BTdynamic.c:112: warning: control reaches end of non-void function
BTdynamic.c: In function "insert":
BTdynamic.c:129: warning: control reaches end of non-void function
```

(I tried compiling with --std=c89 too, but gave up upon realizing that you use C++ style comments.)

Also, from removing #include <conio.h> (that file doesn't exist on my system), I found that you use getch(), which is a non-standard implementation extension.  I didn't bother trying to link it into an executable because the other issues need to be addressed first.

The bottom line is, (1) you are not using C, (2) you are not enabling your compiler's warnings (or are ignoring same) which could tell you this, (3) you are using an archaic I/O library, and (4) even if you were using C, you would be invoking undefined behavior.  Doing anything with the address of an automatic variable that has gone out of scope, even returning it from a function, has undefined behavior.  Similarly, returning nothing from a non-void function has undefined behavior (even if you didn't use it -- which you do).  Your code has a number of other issues, stylistic and otherwise, but those are topics for another day.

So, in effect, you got lucky.  I don't know what you did to make it "work" in Ubuntu, but unless you fixed all of the errors above, you are still relying on undefined behavior.  In this case, the effect of the undefined behavior is to do what you expect.  However, the behavior *is still undefined*.  Just because it behaved as you expected the first time does not mean it necessarily will do so if you recompile it with different options, on a different kernel, or with a different compiler; it could even work differently running the same executable under different load conditions.  Fix the undefined behavior, and then you can say it "works".

---

### Post by dwhitney67 on 2010-06-04
> **trent.josephsen said:**
> 
also, from removing #include <conio.h> (that file doesn't exist on my system), i found that you use getch(), which is a non-standard implementation extension.  I didn't bother trying to link it into an executable because the other issues need to be addressed first.

The bottom line is, (1) you are not using c, (2) you are not enabling your compiler's warnings (or are ignoring same) which could tell you this, (3) you are using an archaic i/o library, and (4) even if you were using c, you would be invoking undefined behavior.  Doing anything with the address of an automatic variable that has gone out of scope, even returning it from a function, has undefined behavior.  Similarly, returning nothing from a non-void function has undefined behavior (even if you didn't use it -- which you do).  Your code has a number of other issues, stylistic and otherwise, but those are topics for another day.

So, in effect, you got lucky.  I don't know what you did to make it "work" in ubuntu, but unless you fixed all of the errors above, you are still relying on undefined behavior.  In this case, the effect of the undefined behavior is to do what you expect.  However, the behavior *is still undefined*.  Just because it behaved as you expected the first time does not mean it necessarily will do so if you recompile it with different options, on a different kernel, or with a different compiler; it could even work differently running the same executable under different load conditions.  Fix the undefined behavior, and then you can say it "works".

+10

---

### Post by dwhitney67 on 2010-06-04
> **cap10Ibraim said:**
> WoW ! it worked in Ubuntu , I don't know what the hell was happening in windows check the image in Ubuntu (2 last lines in the picture)

```
address 0x7fffae7d7be8 value at adress 5
address 0x7fffae7d7be8 value at adress 5
```

Thanks for the pic; perhaps I will copy it an post it in the shite-house.

---

### Post by cap10Ibraim on 2010-06-05
> **trent.josephsen said:**
> If you have to change something later from int to char, your program is already broken.  But that's another topic...

After I fixed the bare "node" declaration I already mentioned, both in the header file and on line 117 of the BTdynamic.c you posted, "gcc -W -Wall --std=c99" had this to say about your program:

```
BTdynamic.c: In function "isEmpty":
BTdynamic.c:13: warning: control reaches end of non-void function
BTdynamic.c: In function "BelongR":
BTdynamic.c:107: warning: function returns address of local variable
BTdynamic.c:112: warning: control reaches end of non-void function
BTdynamic.c: In function "insert":
BTdynamic.c:129: warning: control reaches end of non-void function
```

(I tried compiling with --std=c89 too, but gave up upon realizing that you use C++ style comments.)

Also, from removing #include <conio.h> (that file doesn't exist on my system), I found that you use getch(), which is a non-standard implementation extension.  I didn't bother trying to link it into an executable because the other issues need to be addressed first.

The bottom line is, (1) you are not using C, (2) you are not enabling your compiler's warnings (or are ignoring same) which could tell you this, (3) you are using an archaic I/O library, and (4) even if you were using C, you would be invoking undefined behavior.  Doing anything with the address of an automatic variable that has gone out of scope, even returning it from a function, has undefined behavior.  Similarly, returning nothing from a non-void function has undefined behavior (even if you didn't use it -- which you do).  Your code has a number of other issues, stylistic and otherwise, but those are topics for another day.

So, in effect, you got lucky.  I don't know what you did to make it "work" in Ubuntu, but unless you fixed all of the errors above, you are still relying on undefined behavior.  In this case, the effect of the undefined behavior is to do what you expect.  However, the behavior *is still undefined*.  Just because it behaved as you expected the first time does not mean it necessarily will do so if you recompile it with different options, on a different kernel, or with a different compiler; it could even work differently running the same executable under different load conditions.  Fix the undefined behavior, and then you can say it "works".

Yes you are right , I had always ignored the warnings i do not even read them , starting from now I will try to understand the warnings messages

---

### Post by ibuclaw on 2010-06-05
> **cap10Ibraim said:**
> why dumb? 
if I want to change from int to char , this can reduce the correction

A char is just an unsigned 8 bit type... So the question is still 'Why the typedef?'

```

int a = 65;
printf("'%c' = '%d'\n", a, a);

```

---

### Post by dwhitney67 on 2010-06-05
> **ibuclaw said:**
> A char is just an unsigned 8 bit type... So the question is still 'Why the typedef?'

Typically, a 'char' is signed, however this differs by architecture.  If you are using an Intel or AMD processor, it is signed.  On a PowerPC, IIRC, it is treated as unsigned.

The GCC compiler provides options which a developer can use to force 'char' declarations to be either signed or unsigned.

---

### Post by John Bean on 2010-06-05
> **dwhitney67 said:**
> Typically, a 'char' is signed, however this differs by architecture.  If you are using an Intel or AMD processor, it is signed.  On a PowerPC, IIRC, it is treated as unsigned.

Indeed. It's always good practice to declare a char as unsigned if code relies on that representation. In any case not all architectures use 8-bit chars so in general it's unwise to rely on either the signing or width of a char if C code is intended to be portable.

---

