---
title: "why am I getting an endless loop in this implementation of addlast to linkedlist"
date: 2012-06-18
forum: Programming Talk
---

### Post by Mia_tech on 2012-06-18
guys, I'm trying to implement an "addLast" method of a LinkedList; however, I'm getting an endless loop.... could anyone help 

```
public void addLast(int n)
    {
        Node p = new Node(n);
 
        if(first == null)
        {
            p.next = first;
            first = p;
        }
        else
        {
            Node current = first;
            while(current != null)
            {
                System.out.println("here!");
                if(current.next == null)
                {
                    current.next = p;
                }
                current = current.next;
            }
        }
    }
```

---

### Post by Bachstelze on 2012-06-18
You never exit your while loop because current can never be null. When current.next is null, you set current.next to p, and then you set current to current.next. So current will be p, not null as it should.

---

### Post by Mia_tech on 2012-06-18
> **Bachstelze said:**
> You never exit your while loop because current can never be null. When current.next is null, you set current.next to p, and then you set current to current.next. So current will be p, not null as it should.


got it!... thanks

---

### Post by dwhitney67 on 2012-06-19
> **Mia_tech said:**
> got it!... thanks

Please mark your thread as solved.

In case someone else should stumble upon this thread, here's a solution:
```

public void addLast(int n)
{
    Node p = new Node(n);
 
    if (first == null)
    {
        first = p;
    }
    else
    {
        Node current = first;

        while (current.next != null)
        {
            current = current.next;
        }

        current.next = p;
    }
}

```

---

### Post by Tony Flury on 2012-06-19
> **dwhitney67 said:**
> Please mark your thread as solved.

In case someone else should stumble upon this thread, here's a solution:
```

public void addLast(int n)
{
    Node p = new Node(n);
 
    if (first == null)
    {
        first = p;
    }
    else
    {
        Node current = first;

        while (current.next != null)
        {
            current = current.next;
        }

        current.next = p;
    }
}

```

Just a small comment - I would explicitly set
```

p.next = null ; 

```
As the very last line before the function returns.

---

### Post by dwhitney67 on 2012-06-19
> **Tony Flury said:**
> Just a small comment - I would explicitly set
```

p.next = null ; 

```
As the very last line before the function returns.

Why?  Java takes care of initializing the object to null, so adding that statement is superfluous.  But if the OP wants to initialize the 'next' field, it should be done within the Node constructor.

---

### Post by Tony Flury on 2012-06-20
> 
[QUOTE]
Originally Posted by Tony Flury  
Just a small comment - I would explicitly set

```

p.next = null ;As the very last line before the function returns. 

```

Why? Java takes care of initializing the object to null, so adding that statement is superfluous. But if the OP wants to initialize the 'next' field, it should be done within the Node constructor.
[/QUOTE]
Only suggested it as we don't have the code visible for the constructor, but I agree the constructor should do the equivalent of this for every new Node. Also I would never trust a language to initialise stuff for me implicitly (too much time working with C) :-)

---

