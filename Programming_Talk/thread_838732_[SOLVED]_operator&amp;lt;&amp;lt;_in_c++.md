---
title: "[SOLVED] operator&amp;lt;&amp;lt; in c++"
date: 2008-06-23
forum: Programming Talk
---

### Post by jspolen on 2008-06-23
I'm writing a set class in form of a sorted linked list, in the proccess of making it sort the content of the list. So a good idea would be to print the list on the screen using cout << list << endl;

I have a header file named *setLinkedSorted.h* and this is included in *main.cpp* whereas the functionality of the list is in *setLinkedSorted.cpp*

I've written a print function in the *setLinkedSorted.cpp* file and included it in the header. 

```

void setLinkedSorted::print( ostream & out) const
{
    Node *tmp = first;
    while( tmp != 0 ) {
      out <<  tmp->value << endl;
      tmp = tmp->next;
    }


}

```

This function outputs what I want, but it would be nice to use the *operator<<*

In the same file I wrote

```

ostream & setLinkedSorted::operator<< ( const setLinkedSorted & s )
{
    s.print();
    return cout;

}

```

but my output is not what I wanted, it gives me the memory adress 0x804f008 when i use cout << list << endl;

Anybody got any ideas?

---

### Post by tornado89 on 2008-06-23
why are you sending ostream& out to print
it should take no parameters and instead of using
    out <<  tmp->value << endl;
use
    cout <<  tmp->value << endl;

now to overload <<

use this
ostream& operator<< ( ostream& out, const setLinkedSorted & s )
{
    s.print();
    return out;

}

---

### Post by dwhitney67 on 2008-06-23
Yeah, you have a missing parameter in your method...

[PHP]friend std::ostream& operator<< ( std::ostream &os, const setLinkedSorted & s );[/PHP]

Then implemented it:
[PHP]std::ostream& operator<<( std::ostream &os, const setLinkedSorted &s )
{
  Node *tmp = s.first;
  while( tmp != 0 ) {
    os <<  tmp->value << std::endl;
    tmp = tmp->next;
  }
  return os;
}[/PHP]

Note that this is a friend method; you do not need to add the scope operator ("setLinkedSort::") when implementing the method.

---

### Post by dwhitney67 on 2008-06-23
> **tornado89 said:**
> why are you sending ostream& out to print
it should take no parameters and instead of using
    out <<  tmp->value << endl;
use
    cout <<  tmp->value << endl;

now to overload <<

use this
ostream& operator<< ( ostream& out, const setLinkedSorted & s )
{
    s.print();
    return out;

}
Not a very good implementation if you ask me.  What if the user wants to output to a file stream?  At a minimum, the print() method should take the ostream parameter, not disregard it.

Personally, what is the point of having the print() method if the operator<<() method is present?

---

### Post by jspolen on 2008-06-23
Sorry guys, lots of typos.

Was trying alot of different approaches, and found that I got it to work without the ostream parameter (at least I thought I did)

The reason for the print method was so that I could skip the friend declaration. Read so in a book, but unfortunatly i did not work.

Well I got it to work now so thank you guys!

---

### Post by tornado89 on 2008-06-24
Hey dwhitney67
I Was Wondering The Same...
But I Just Wanted To Keep The Code As Close As It Was
You're Right

---

