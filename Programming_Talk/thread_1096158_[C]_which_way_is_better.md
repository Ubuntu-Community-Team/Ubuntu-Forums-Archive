---
title: "[C] which way is better?"
date: 2009-03-14
forum: Programming Talk
---

### Post by hanniph on 2009-03-14
Hi all, I was writing my HW assignment and ran into some design problem :D
So I have a struct:
```

struct poly {
    int deg;
    int *ptr; 
}

```
and I want to create function that fills my poly struct variables with some data. I can do this in two ways:
1. Pass a struct to a function
```

void getPoly(struct poly *X)
{
   //get some number from a user
   X->deg = some number
   //get some memory
   X->ptr = some memory address
}

```

2. Create another poly instance inside a function, fill it with data and return that instance:
```

poly getPoly()
{
    struct poly X;
    //get some num
    X.deg = some num
    //get some mem
    X.ptr = some address
   return X;
}

```

and then do:
```

 struct poly A;
 //first variant:
 getPoly(&A); 
 //second variant:
 A = getPoly();

```
imo both are fine, but which one would you prefer/choose? :D I know this is not a serious question but still :)

---

### Post by Sinkingships7 on 2009-03-14
I'd say that as long as the struct(s) you create based off of poly are properly named so that it's easy to tell what it is (poly_A1 and so forth), then the second one would appear easier to read to me. But that's just preference. :p

However, I feel like the first one is more "C like" for some reason... anyone else?

---

### Post by ZuLuuuuuu on 2009-03-14
Considering the appropriate changes are made to the second case, I would prefer that way which is creating the instance inside the function. That way looks more abstracted which is generally a good thing in programming. For example, if you need to change something about the creation phase, you will only need to change that function.

---

### Post by jimi_hendrix on 2009-03-14
i would use the latter but as mentioned above you will need to return a malloced pointer

---

### Post by hanniph on 2009-03-14
I think I'm safe with 
```

struct poly A = getPoly();

```
mallocated pointer is copied to A.ptr

---

### Post by Can+~ on 2009-03-14
I feel the better approach is to isolate the function that creates and returns structs and break it appart from asking user input, for example:

[PHP]poly newPoly(int some_num, int* some_ptr)
{
    struct poly x;
    X.deg = some_num;
    X.ptr = some_ptr;
    return x;
}[/PHP]

And another function that wraps this one

[PHP]poly userPoly()
{
    // ask for input
    return newPoly(user_num, user_ptr)
}[/PHP]

The reason I put it this way, is to separate user functions from element-creation functions, let's say that your program grows, and now you want to do

```
poly x = newPoly(5, ptr_to_somewhere);
```

if you use my approach, you'll have no problem, but if you wanted to use your method, you'd have to write yet another function to handle in case where you just want to create a newPoly without asking the user.

(btw, the code isn't exactly functional, it's just to show the idea, malloc if needed).

---

### Post by houbysoft.xf.cz on 2009-03-14
I would choose the first one. By the way the second one looks a little wrong, you would rather want to create a pointer, then malloc it, and then return it.

---

### Post by hanniph on 2009-03-14
> **Can+~ said:**
> 
(btw, the code isn't exactly functional, it's just to show the idea, malloc if needed).
Yeah, I got it. Separating user input from creating struct seems like a very good idea

---

### Post by Can+~ on 2009-03-14
> **houbysoft.xf.cz said:**
> I would choose the first one. By the way the second one looks a little wrong, you would rather want to create a pointer, then malloc it, and then return it.

If you just return it, it will return as a value and copy it to the other struct outside.

But it's true that it must be malloced if the OP wants to use it in other scopes later.

---

### Post by slavik on 2009-03-14
in C, a struct is like an int ... it doesn't have to be allocated in the heap in order for the value to be returned. you can also put a struct around an array and presto, you can use assignment to assign arrays to each other. :)

---

