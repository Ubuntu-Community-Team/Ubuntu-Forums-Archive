---
title: "returning a pointer to an element in a binary tree"
date: 2011-08-26
forum: Programming Talk
---

### Post by manish411 on 2011-08-26
```

struct node* rfind(struct node* current,int a)
{

    struct node* c = current;

    if(current->data!= a && current!=NULL)
    {
       current = rfind(current->leftchild,a);
       if(current == NULL)
       current = rfind(current->rightchild,a);
    }
    return current;
}
struct node *data = rfind(root,3);

```

initially for a tree inserted in the order 4 5 9 2 16 12 3 1 

I am able to find the node 4 , 1 , 2, i.e the left child of any node
but I am getting a segmentation fault if I try to find a node which is a rightchild
of any subtree

---

### Post by Bachstelze on 2011-08-26
if(**current == NULL**)
       current = rfind(**current->rightchild**,a);

Don't see a problem there? ;)

---

### Post by giowck on 2011-08-26
Did you try to change the following

```
if(current->data!= a && current!=NULL)
```

in

```

if(current!=NULL && (current->data!= a))

```

?

Because if current is NULL, the "current->data" operation is executed (if the compiler uses the evaluation order from left to right...)

With the new code, if current is NULL, the second expression will not be evaluated because the first already is false....

EDIT: ;P someone was faster than me

---

### Post by Arndt on 2011-08-26
> **manish411 said:**
> ```

struct node* rfind(struct node* current,int a)
{

    struct node* c = current;

    if(current->data!= a && current!=NULL)
    {
       current = rfind(current->leftchild,a);
       if(current == NULL)
       current = rfind(current->rightchild,a);
    }
    return current;
}
struct node *data = rfind(root,3);

```

initially for a tree inserted in the order 4 5 9 2 16 12 3 1 

I am able to find the node 4 , 1 , 2, i.e the left child of any node
but I am getting a segmentation fault if I try to find a node which is a rightchild
of any subtree

I recommend debugging with gdb.

---

### Post by Bachstelze on 2011-08-26
> **Arndt said:**
> I recommend debugging with gdb.

I don't. ;) To me, using gdb for this is like using a calculator to compute 6*15. Those are things you should be able to do on your own, otherwise you will waste massive amounts of time firing up gdb for the simplest things.

---

### Post by Arndt on 2011-08-26
> **Bachstelze said:**
> I don't. ;) To me, using gdb for this is like using a calculator to compute 6*15. Those are things you should be able to do on your own, otherwise you will waste massive amounts of time firing up gdb for the simplest things.

I recommend it if it solves his problem, which he apparently couldn't do on his own. And I recommend it when the source code is much larger than this, too.

If you can find the errors faster by visual inspection, of course you should do so.

That aside, I don't understand the "massive amounts of time" part. Firing up gdb takes exactly as long as typing the command that does so.

---

### Post by manish411 on 2011-08-27
> **Bachstelze said:**
> if(**current == NULL**)
       current = rfind(**current->rightchild**,a);

Don't see a problem there? ;)

No, I dont see the problem , please can you point it out to me!!!

---

### Post by giowck on 2011-08-27
> **manish411 said:**
> No, I dont see the problem , please can you point it out to me!!!

If current is NULL, you can't access to a non existent memory space. This causes a segmentation fault.

[http://en.wikipedia.org/wiki/Pointer_(computing)#Null_pointer](http://en.wikipedia.org/wiki/Pointer_(computing)#Null_pointer)

---

### Post by manish411 on 2011-08-27
> **giowck said:**
> If current is NULL, you can't access to a non existent memory space. This causes a segmentation fault.

[http://en.wikipedia.org/wiki/Pointer_(computing)#Null_pointer]("http://en.wikipedia.org/wiki/Pointer_%28computing%29#Null_pointer")

Thanks a lot 
by making a slight changes I am able to run the program

by making use of another pointer 
```


struct node* c;


```and using it to return the null pointer while at the same time 
storing the parent pointer in current pointer

```

struct node* rfind(struct node* current,int a)
{

    struct node* c = current;

    if(current!=NULL)
    {
        if(current->data!=a)
        {
        c = rfind(current->leftchild,a);
       if(c == NULL)
       c = rfind(current->rightchild,a);
        }
    }
    return c;
}

```

---

