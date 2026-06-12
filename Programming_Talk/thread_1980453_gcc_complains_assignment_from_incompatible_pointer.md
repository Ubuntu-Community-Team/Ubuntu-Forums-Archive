---
title: "gcc complains: assignment from incompatible pointer type"
date: 2012-05-15
forum: Programming Talk
---

### Post by Chiel92 on 2012-05-15
Hi all,

I am a c noob and I'm experiencing problems with my program.
I have the following code:
```
typedef struct
{
    char ***state;
    struct Node *parent;
} Node;

Node* NodeInit(Node *node, char ***state, Node *parent)
{
    (*node).state = state;
    (*node).parent = parent;
    return node;
}
```But it gives the following error:```

40:17: warning: assignment from incompatible pointer type [enabled by default]
```where line 40 is the line which states:  "(*node).parent = parent;"

What am I doing wrong?
Any help is appreciated.

Regards

---

### Post by dwhitney67 on 2012-05-15
> **Chiel92 said:**
> 
What am I doing wrong?


The problem lies with how you have your struct defined; try something like this:
```

typedef struct **Node**   <-- Add Node label here
{
    char ***state;
    struct Node *parent;
} Node;

```
I wish I had a good answer as to why the compiler doesn't complain at the structure, but instead complains at the code (as you found out).

Btw, out of curiosity, what are your plans for 'state'.  Is it going to be an two-dim array of strings?

---

### Post by trent.josephsen on 2012-05-15
Better yet, eliminate the typedef altogether. typedef should be used to make code clearer, not to avoid typing 'struct' when the code in question needs to know that node is, in fact, a struct.

I regret that propriety and the forum rules do not permit me to use more forceful terms in admonishing this practice, which I revile with a burning passion. No offense to OP, because I'm sure you innocently copied it from someone else (who should know better), but it's something I see frequently and it irks me every single time.

---

### Post by Chiel92 on 2012-05-15
Thanks for your quick replies!
dwhitney67: Your suggestion solves the problem, though I do not understand exactly why it works.
trent.josephsen: I didn't know how to get recusive structs in C, so I indeed googled somewhat and copied the suggestions. They happened to use typedef, so I concluded that typedef was necessary in order to obtain a correct recursive struct.

I now have the following code which also works fine. I do not really mind typing the 'struct' statement every time I declare a Node, so following the suggestion of trent.josephsen I removed it and it works :)
```

struct Node
{
    char **state;
    struct Node *parent;
};

struct Node* NodeInit(struct Node *node, char **state, struct Node *parent)
{
    (*node).state = state;
    (*node).parent = parent;
    return node;
}
```dwhitney67: state is a pointer to a 2d array of chars. But I realized that the pointer to the first element of the 2d array can also be used for passing by reference, so I removed one of the asterisks.

Many thanks for your help!

---

### Post by trent.josephsen on 2012-05-15
Thanks for seeing the light :)

Hiding "struct" with a typedef is a common practice, and I don't have a problem with it when it's used reasonably -- but it hides information that can be important to readability. I use the guideline that if you are just passing it around as a black box and don't care what's in it, it's fair game for a typedef (like FILE, which is an example from the Standard); but if you plan to access its members in any way you should declare it with 'struct'. Same goes for pointers, if you're going to dereference it you should be able to tell it's a pointer by looking at its declaration.

---

### Post by 11jmb on 2012-05-15
> **trent.josephsen said:**
>  I use the guideline that if you are just passing it around as a black box and don't care what's in it, it's fair game for a typedef 

That's an excellent way to put it. A more general guideline would be that a typedef is supposed to provide more information, never to remove useful information.

Just to expand a bit, you used the example of FILE, which is passed along like a black box, and therefore the "struct" identifier is not terribly useful. An example of where the struct identifier should be kept might be tm or timespec in time.h, since the members will almost definitely be accessed. Therefore, in this case using typedef to hide the struct identifier would make the code less readable.

---

