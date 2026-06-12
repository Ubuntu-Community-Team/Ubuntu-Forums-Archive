---
title: "Simple C Question - typedef"
date: 2011-10-23
forum: Programming Talk
---

### Post by AlGorism on 2011-10-23
Hi all.
I'm trying to build a tree, so in my header file I coded a struct for that. I have a little problem:

```

typedef struct tree_t *treeptr;
typedef struct {
     ...
     treeptr right;
     treeptr left;
}harbor_t;

```

If a use like this, when I try to define a variable like 
```
treeptr a;
```
compiler goes crazy, says:
"warning:initialization from incompatible pointer type"
and
error: dereferencing pointer to incomplete type" on the next line, when I try to reach an element of struct. (after malloc of course)

On the other hand, when I try to use like this:
```
typedef struct tree_t *treeptr;
typedef struct treeptr{
.
.
};
```
I can't define any variable for struct tree_t. Also, there is another warning in header file like:
"warning: useless storage class specifier in empty declaration"

Any suggestion?

---

### Post by Arndt on 2011-10-23
> **AlGorism said:**
> Hi all.
I'm trying to build a tree, so in my header file I coded a struct for that. I have a little problem:

```

typedef struct tree_t *treeptr;
typedef struct {
     ...
     treeptr right;
     treeptr left;
}harbor_t;

```

If a use like this, when I try to define a variable like 
```
treeptr a;
```
compiler goes crazy, says:
"warning:initialization from incompatible pointer type"
and
error: dereferencing pointer to incomplete type" on the next line, when I try to reach an element of struct. (after malloc of course)

On the other hand, when I try to use like this:
```
typedef struct tree_t *treeptr;
typedef struct treeptr{
.
.
};
```
I can't define any variable for struct tree_t. Also, there is another warning in header file like:
"warning: useless storage class specifier in empty declaration"

Any suggestion?

What is the definition of struct tree_t?

---

### Post by trent.josephsen on 2011-10-23
In my opinion, typedef is way overused, especially in rookie code.  The eight keystrokes you save typing 'treeptr' instead of 'struct tree_t *' are really negligible, and the second one is more clear by an order of magnitude.  typedef should be used to make truly nasty declarations easier to read, not to make simple ones more obscure.

In any case, you don't appear to have ever defined 'struct tree_t'.  You should do that.

Also, I might be misremembering, but I think the conventional reason for the _t suffix is to indicate that the name is a typedef.  Your usage is backward.  Of course, you're free to defy convention, but you'll only be confusing other people (and your future self) by doing so.

---

### Post by AlGorism on 2011-10-23
I solved it.
I typed these in header file:
```
typedef struct tree_t tree_t;
typedef struct tree_t* treeptr
```

Then I defined my struct in c file. Something like this:
```
struct tree_t {
   .
   .
   treeptr left;
   treeptr right;

```
It's working :)

---

