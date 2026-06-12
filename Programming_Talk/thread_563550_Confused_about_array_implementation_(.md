---
title: "Confused about array implementation :("
date: 2007-09-30
forum: Programming Talk
---

### Post by DesertRose on 2007-09-30
Hi there!

Does anyone know what is "implementation of array in a linked list"? what is the maybe idea of it? Please, maybe someone could show an example of how does it look like? :( in c++, if possible :( 
Please help me :(

---

### Post by CptPicard on 2007-09-30
My guess is that it means a linked list that holds both an index and value in the list's node. This way you can create arrays that are "sparse", that is, have just some of the values filled in, but don't spend memory for all values. The downside is that you lose the ability for constant-time random access, but have to traverse the list linearly to find some value.

Suppose you've got an array [1,null,null,2,null,3] and you're just interested in non-null values... your linked list would be like this:

```

[0 | 1]--[3 | 2]--[5 | 3]--||

```

Where the node is [index | value].

EDIT: And of course you're still implicitly saving the nulls as well, just return null when there's no requested index in the list...

---

### Post by Compyx on 2007-09-30
> **DesertRose said:**
> Hi there!

Does anyone know what is "implementation of array in a linked list"? what is the maybe idea of it? Please, maybe someone could show an example of how does it look like? :( in c++, if possible :( 
Please help me :(

Hmm, you're asking a lot.

Usually one would create a linked list to simulate a dynamic array. Insertion of an element in an array is expensive in terms of processing-time: you would have to reallocate memory to account for the extra element and then shift all elements after the inserted one to the 'right'.
Using a linked list, you would allocate memory for the new element and then update the pointer of the elements before and after the inserted element (assuming a doubly linked list) to point to the new element, and have the new element's pointers point to it's neighboring elements to keep the list intact.

Linked list are also great to implement queues and stacks. The downside of linked list is that insertion, lookup and deletion by index can become quite expensive since you have to traverse the list to get to the element at the index.

There's plenty of material on the internet about linked lists and arrays, I suggest looking at Wikipedia: [http://en.wikipedia.org/wiki/Linked_list]("http://en.wikipedia.org/wiki/Linked_list"), they will probably do a much better job at explaining things than I do.

By the way, although I'm not a C++ expert, I think in C++ you'd use a vector rather than a linked list.

HTH

---

### Post by DesertRose on 2007-09-30
CptPicard,
thank you very much for your explanation! It really helped me to understand what I have to do! :) O:)

---

### Post by DesertRose on 2007-09-30
Compyx,
thank you for your reply! I have an exercise where I have to implement array in a linked list, so I can't use vectors or something else :(

---

### Post by Blue Sky on 2007-09-30
Linked Lists in C++ are usually implemented by having Node objects - each one contatining a value and a pointer to the next Node. A List object will contain a pointer to the first node as well as the implementation of some methods such as for lookup, insertion and deletion.

You can use array indices instead of pointers, which is what they're getting at, it's basically the same thing. I hope that helps.

---

### Post by DesertRose on 2007-09-30
Blue sky, thank you very much for your reply!

Now I found another problem related to linked list :(
What did I do wrong in this code? It tells me that 'new types may not be defined in a return type' and that 'main must return int'. I have defined a class named LVS, so I can use it as a type in a main part of the program, can't I? Besides this doesn't my main program return int? Maybe there's something wrong with my compiler :(:( Please tell me where my mistake is :(

---

### Post by Arwen on 2007-09-30
cout << curr->data;
                        curr=curr->next;}}
                        }; (<--you missed a greek question mark,it's right after the last } of a class definition

---

### Post by Arwen on 2007-09-30
struct elem{
       char data;
       elem *next;}; (<--and another one here)

---

### Post by DesertRose on 2007-09-30
Arwen, thanks a lot!  it works now!  :)  :) :)

---

### Post by Compyx on 2007-09-30
Looks like Arwen beat me to it (btw: it's called a 'semi-colon').

Also note that using 'system("pause");' is unportable, for example Gnu/Linux doesn't know about 'pause'. I'm guessing you're using Fisher-Price OS.

C++ experts will probably point out that 'using namespace std' is discouraged (see: [http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5]("http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5")).

---

### Post by aks44 on 2007-09-30
As a side note, your placement of closing braces make your code very hard to read... (and I'd bet quite difficult to maintain too)

---

### Post by Compyx on 2007-09-30
> **aks44 said:**
> As a side note, your placement of closing braces make your code very hard to read... (and I'd bet quite difficult to maintain too)

Agreed. And using some whitespace now and then wouldn't hurt either, whitespace is pretty cheap these days. 6-space tabs are also a bit unusual, but you should go what you feel comfortable with.

Here's how I would indent this code (I've only corrected the missing semi-colons, not any other mistakes):
```

#include <iostream>
using namespace std;

struct elem{
    char data;
    elem *next;
};

class LVS
{
    elem *start;
    elem *curr;
    
    public:
        
        LVS()
        {
            start = NULL;
        }
        
        ~LVS()
        {
            while (start != NULL) {
                curr = start->next;
                delete start;
                start=curr;
            }
        }
        
        void add(char a)
        {
            elem* q = new elem;
            q->data = a;
            q->next = start;
            start = q;
        }
        
        void print()
        {
            curr = start;
            while (curr != NULL) {
                cout << curr->data;
                curr = curr->next;
            }
        }
};


int main()
{
    LVS list;
    char w;
    
    cin >> w;
    while (w != '.') {
       list.add(w);
       cin >> w;
    }
    list.print();
    system("pause");
    
    return 0;
}

```

---

### Post by Arwen on 2007-09-30
@Compyx: Yep I tried to run the program and when I gave "." 
I got "sh: pause: not found"

thanx,I knew it was semi-sth but I missed that sth(=colon) :-P

---

