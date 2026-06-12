---
title: "a quick linked list question"
date: 2010-01-08
forum: Programming Talk
---

### Post by infestor on 2010-01-08
is there a difference between:
```
tmp.next=new WordListNode(word,url);
```

and

```
tmp=tmp.next;
tmp=new WordListNode(word,url);
```

---

### Post by PmDematagoda on 2010-01-08
In the first example you are assigning the address of the new variable to the next pointer in tmp. In the second, you are copying the address in the next pointer to tmp and then copying the address of the new variable to tmp, there is a difference because you are not changing the value of tmp.next in the process.

A little more clearly:-
First example:
tmp.next = new_var;

Second example:
tmp = tmp.next
tmp = new_var

the essential thing to note is that only tmp is pointing to the allocated area of memory and not tmp.next.

I hope I was able to explain it clearly, if not, you could always write a small example program on that with one program where everything works great and another where there would be issues concerning the usage of memory. :)

---

### Post by dwhitney67 on 2010-01-08
> **infestor said:**
> is there a difference between:
```
tmp.next=new WordListNode(word,url);
```

and

```
tmp=tmp.next;
tmp=new WordListNode(word,url);
```

There's a world of difference.

The first statement looks like a legitimate attempt at assigning tmp.next.

As for the second set of statements, you are assigning tmp.next to tmp, and then reassigning tmp to point to new allocated memory, which obviates the need for the first assignment.

Btw, I can only assume that you are programming in Java.  If you are programming in C++, then it would appear that you also have syntax errors wrt dereferencing the pointer.

---

### Post by infestor on 2010-01-08
> **PmDematagoda said:**
> In the first example you are assigning the address of the new variable to the next pointer in tmp. In the second, you are copying the address in the next pointer to tmp and then copying the address of the new variable to tmp, there is a difference because you are not changing the value of tmp.next in the process.

A little more clearly:-
First example:
tmp.next = new_var;

Second example:
tmp = tmp.next
tmp = new_var

the essential thing to note is that only tmp is pointing to the allocated area of memory and not tmp.next.

I hope I was able to explain it clearly, if not, you could always write a small example program on that with one program where everything works great and another where there would be issues concerning the usage of memory. :)

first statement *doesn't work*, it causes a out of memory error. The second one works.

> **dwhitney67 said:**
> There's a world of difference.

The first statement looks like a legitimate attempt at assigning tmp.next.

As for the second set of statements, you are assigning tmp.next to tmp, and then reassigning tmp to point to new allocated memory, which obviates the need for the first assignment.

Btw, I can only assume that you are programming in Java.  If you are programming in C++, then it would appear that you also have syntax errors wrt dereferencing the pointer.

yes it is written in java.

thanks for the explanations guys. i am *obviously* having hard time understanding linked lists. they are being hard to conceptualize in my mind. for example consider this assignment:
tmp=tmp.next;

is it correct to say: tmp points to tmp.next ?

---

### Post by PmDematagoda on 2010-01-08
> **infestor said:**
> thanks for the explanations guys. i am *obviously* having hard time understanding linked lists. they are being hard to conceptualize in my mind. for example consider this assignment:
tmp=tmp.next;

is it correct to say: tmp points to tmp.next ?

No, tmp points to what tmp.next points to, not to the next pointer.

---

### Post by dwhitney67 on 2010-01-08
> **infestor said:**
> i am *obviously* having hard time understanding linked lists. they are being hard to conceptualize in my mind.
Try to visualize in your mind a chain, or easier yet, a train consisting of 2 or more box-cars.


```

+----------+          +----------+
|          |   next   |          |   next
|   Data1  |--------->|   Data2  |---------> NULL
|          |          |          |
+----------+          +----------+

```

Here's a sample bit of code that defines a linked list:
```

class Node
{
   public String name;
   public int    age;
   public Node   next;

   public Node(String name, int age)
   {
      this.name = name;
      this.age  = age;
      this.next = null;
   }
}

public class LinkedList
{
   private Node list = null;
   private Node tail = null;  // only needed if using Option 2... see below

   Linked()
   {
   }

   public void insert(String name, int age)
   {
      Node tmp = new Node(name, age);


      // Option 1... insert new Nodes in front of the LL; this obviates
      // the need to maintain a tail reference.
      tmp.next = list;


      // Option 2... insert new Nodes at the end of the LL; for speed,
      // this requires the use of a tail reference.  Without, one would need
      // to search to the end of an existing list to insert the new Node.
      if (list == null)
      {
         list = tmp;
         tail = list;
      }
      else
      {
         tail.next = tmp;
      }
   }
}

```
When you are more advanced in your Java studies, you could consider making the LinkedList class a template.

---

