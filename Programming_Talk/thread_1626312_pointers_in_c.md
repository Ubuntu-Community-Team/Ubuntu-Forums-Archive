---
title: "pointers in c"
date: 2010-11-20
forum: Programming Talk
---

### Post by parmeshwor on 2010-11-20
please help its very necessary for me . the output is "true"  HOW?

#include<stdio.h>
#include<conio.h>
#include<stdlib.h>

struct bnode
    {
    struct bnode *left;
     int info;
    struct bnode *right;
    };

struct bnode *root;
void main()
    {
    int choice,data;

    clrscr();
    root=NULL;


    root=(struct bnode *)malloc(sizeof(struct bnode));
    root->info=10;
      root->right=root->left=NULL;
    
     if(root->left->left->left->left== NULL)
    printf("true\n");
      
getch();
    }
//output is ''true''  HOW??

---

### Post by Arndt on 2010-11-20
> **parmeshwor said:**
> please help its very necessary for me . the output is "true"  HOW?

#include<stdio.h>
#include<conio.h>
#include<stdlib.h>

struct bnode
    {
    struct bnode *left;
     int info;
    struct bnode *right;
    };

struct bnode *root;
void main()
    {
    int choice,data;

    clrscr();
    root=NULL;


    root=(struct bnode *)malloc(sizeof(struct bnode));
    root->info=10;
      root->right=root->left=NULL;
    
     if(root->left->left->left->left== NULL)
    printf("true\n");
      
getch();
    }
//output is ''true''  HOW??

1) Put your code inside CODE tags, that way the indentation is kept and it's easier to read.
2) You set root->left to NULL, so what do you then expect root->left->left to be? If you follow a NULL pointer, anything may happen.

---

### Post by matt_symes on 2010-11-20
Hi

      root->right=**root->left=NULL**;
    
     if(**root->left->left**->left->left== NULL)
         printf("true\n");

Your dereferencing a NULL pointer here. That is bad practice and a cause of a large number of bugs.

Kind regards

---

### Post by trent.josephsen on 2010-11-20
I was wondering how you managed to get "true" when you should get a segmentation fault, but then trying to compile it tipped me off:

```
% gcc parmeshwor.c
parmeshwor.c:2:18: fatal error: conio.h: No such file or directory
compilation terminated.
```

You're obviously using a compiler with DOS-specific extensions.  Nuke <conio.h>; it's been deprecated for nearly two decades.  getchar() is standard and there's no reason to use an ancient, outmoded and unportable library just to clear the screen.

---

### Post by trent.josephsen on 2010-11-20
oops

---

### Post by trent.josephsen on 2010-11-20
What the heck, triple post?  Seriously ubuntuforums?

---

