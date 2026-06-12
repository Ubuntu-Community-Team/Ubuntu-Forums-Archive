---
title: "Java Linked List Creation"
date: 2008-02-28
forum: Programming Talk
---

### Post by petzworld999 on 2008-02-28
I am trying to create a linked list in Java for a course. I am not allowed to use the LinkedList class built into Java. I understand that a linked list is made of objects with two nodes each: one with data and one with a pointer to the next. I just don't understand how to tack another one on without losing the old ones. This is the basic syntax I have, with Widget as my class. I know this is not actual code. flink is a class within the Widget class that stands for forward link.
```

main method

Widget f, n, p;
f=n;
p=n;

addWidget();

f.flink = p;

public static void addWidget()
{
  Widget n = new Widget(); 
  Widget p = new Widget(); 
 n.setName = ("George");
  //setName is a method in the Widget class
}


```


If anyone can understand what I am trying to say, any help would help greatly. I have written more code if anyone is interested in that.

---

### Post by Jessehk on 2008-02-28
**psuedocode**
```

function append(list, item) {
    set iterator to list-head;
    while ( iterator.next != end-of-list ) {
        iterator := iterator.next;
    }

    iterator.next := make_node( data );
}

```

Where make_node automatically sets the *next* pointer to the end of list (probably null, but I'm not entirely fluent in Java :)).

[this](http://www.eternallyconfuzzled.com/tuts/datastructures/jsw_tut_linklist.aspx) is a great reference for linked lists BTW, but you need to understand C.

---

### Post by Wybiral on 2008-02-28
> **Jessehk said:**
> **psuedocode**
```

function append(list, item) {
    set iterator to list-head;
    while ( iterator.next != end-of-list ) {
        iterator = iterator.next;
    }

    iterator.next = make_node( data );
}

```

Where make_node automatically sets the *next* pointer to the end of list (probably null, but I'm not entirely fluent in Java :)).

While this is a common "append" / "push_back" implementation, it's also O(n) when it could be O(1) just by having the LinkedList class store a pointer to both the front and back of the list (this also allows for O(1) "prepend" / "push_front" as well). Unless your course requires you to only store one node (or that one extra pointer sets you over your memory budget), I would suggest keeping both front and back pointers in the class.

---

### Post by Digitz on 2008-02-28
Ah, I  also had to build an own implementation of a linked list in Java. 

```

public class Node {

  Object element;
  Node next;

  public Node(Object o) {
   element = o;
  }
}

```

an addfirst and addlast method (u need to define a Node first,last in your class, and perhaps a variable to save the size of the list):

```

public void addFirst(Object o){

  Node newNode = new Node(o);
  newNode.next = first;
  first = newNode;
  size++;

  if(last == null) last = first;
}

public void addLast(Object o){
  if(last == null) {
     first = last = new Node(o);
   }
  else {
    last.next = new Node(o);
    last = last.next;
  }

  size++;
}

```

Hope u understand now (please dont just use this code without understanding it). If not, I can get you an illustration of how a linked list works, how the elements point to each other (teacher site is offline now though...).

---

### Post by petzworld999 on 2008-02-28
Okay, thank you. I understand better now.

---

