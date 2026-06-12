---
title: "C structure pointers"
date: 2013-06-20
forum: Programming Talk
---

### Post by vintisp on 2013-06-20
I am implementing linked list in C. Here is the code for new list and insert
```

struct node{
        int key;
        struct node *next;
        };


        struct node *head;
        struct node *tail;
        int size;
        S_List(int k){
            head = NULL;
            tail = NULL;
            size = 1;
                        struct node temp;
            temp.key = k;
            temp.next = NULL;
            head = &temp;
            tail = &temp;


        }
        
        void insert(int k){
                        struct node temp;
            temp.key = k;
            if(size ==1)
                head->next = &temp;
            tail->next = &temp;
            temp.next = NULL;
            tail = &temp;
            size++;
        }
    
}

```

the problem is if I use a structure object** struct node temp**, the whole implementation fails and doesn't work. When I debugged it in gdb I found that when I pointing the tail to the new nodes added, **the head pointer is also pointing to those new nodes along with the tail node.**

Instead when I use a pointer
 ```
struct node *temp= (struct node *)malloc(sizeof(struct node));
``` in place of ```
struct node temp
```.
Then the code just works fine.( head = tail = temp)

Whats wrong in the first approach??

---

### Post by dwhitney67 on 2013-06-20
> **vintisp said:**
> 
Whats wrong in the first approach??

In your first approach, you are taking the address of a local variable within the function.  When that variable goes out of scope, so does any reference (pointer) to such.

---

### Post by vintisp on 2013-06-20
In the first approach, why do head and tail pointer point to the same address, all the time. Like for eg, when I insert 1 then 2 and then 3, the head->key contains 3 same as tail->key and head->next becomes NULL.

---

### Post by trent.josephsen on 2013-06-20
First point: Don't cast the return value of malloc(). I suggest using the alternate form of sizeof here as well.
```
struct node *temp = malloc(sizeof *temp);
```

Second point: Your indentation is rather wonky and you appear to have two extra }'s at the end of the listing. I'm not sure if you're doing the indentation intentionally because that's how it would be done in a language like Java -- if so, that's weird and the other C programmers will laugh at you, but you can do it if you want.

Point the third: S_List needs to declare a return type (or return an int, if you're using C89).

All that aside, when you write "struct node temp;" you are defining an object of type "struct node", which has its own value and address. In S_List(), you define such an object with what is called *automatic storage duration*, which means that after the enclosing scope (in this case, the S_List function) ends, the object disappears -- its value is no longer valid and you may not access the memory at (what was formerly) its address. The problem arises because you assign the **permanent** variables "head" and "tail" to the address of this **temporary** object -- an address which you are not allowed to use after the function returns. Since this is C, you may shoot yourself in the foot by attempting to do so, but the language makes no guarantees about what may happen afterwards. This explains why you see the same value recur, but technically anything could happen, like getting the value 42 or installing MS-DOS.

Memory obtained by malloc() and friends does not go out of scope and continues to be useful until you release it by a call to free().

If you're using gcc, I recommend compiling with at least the following options to catch many simple mistakes. It's a lot to type so you may want to give it a short alias in your .bashrc, like "cc".

```
gcc -std=c11 -Wall -Wextra -pedantic
```

See the gcc manpage for more information on those and many other flags.

---

### Post by vintisp on 2013-06-20
Thanks for such an informative reply. I got all your points except the **third point**, which says S_List should declare a return type.
Btw should the indentation be like
```
void foo
{
   ...
   ...
}
```
instead of
```
void foo{
   ...
   ...
}
```

---

### Post by trent.josephsen on 2013-06-20
That's not such an issue, although the former is more common for C -- I was referring to the fact that you indented the function definitions an additional level beyond the structure definition.

I prefer OTBS, i.e. the One True Brace Style (it's an actual thing, look it up) but really as long as you're consistent you can use whatever you like. Except GNU style, which is demonstrably evil.

The definition of S_List() doesn't have a return type, which means it's as if you'd used "int":
```
int S_List(int k) {
    ...
}
```
But you don't return anything from it, so the behavior is undefined. You probably meant to use "void", like you correctly did for insert().

The rule that says functions declared without a return type are automatically int is an old one, and newer versions of the language don't permit it (although gcc will let it slide after warning you). That's why I suggested compiling with -std=c11; C11 is just the most recent version of the language standard, C89 being the first and oldest.

Note that gcc by default does not compile according to any particular standard, but its own "gnu89" dialect, which is more permissive than standard C and produces fewer useful warnings.

---

