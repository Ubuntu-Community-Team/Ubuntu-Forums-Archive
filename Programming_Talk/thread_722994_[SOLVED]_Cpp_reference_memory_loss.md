---
title: "[SOLVED] Cpp reference memory loss"
date: 2008-03-13
forum: Programming Talk
---

### Post by henchman on 2008-03-13
Hi :-)

Iam a Cpp beginner and trying to write a XML-Parser. Several days ago, i found a tool in these forums to find memory leaks in a program...


```
class XMLNode
{
   XMLNode &getNextNode( )
  {
    // finding next node...
    // ...
   
   XMLNode* newNode = new XMLNode(/*params*/); // line of the memory leak according to valgrind
   return *node; 
  }

   char* xml;
   char* startingPosition;
   char* currentPosition;
   char* endingPosition;
};
```


I had to copy the code by hand, so if there are typos, sorr.. the code runs...

My question is how can I return a reference/pointer of XMLNode in this function without memory loss... or do I have to return a normal (eg. non-pointer) XMLNode... I want to enable the user of this class to use it like this:

myNode.getNextNode().getNextNode()

There are exactly 16 Bytes lost according to valgrind... The pointers are filled with a value within the constructor and all point to the same char-array containing the xml-code, but the values behind these pointers are delete[]'d in another destructor...

Thanks for reading :)

---

### Post by PaulFr on 2008-03-13
1. Your **new XMLNode** call creates a XMLNode object on the heap.

2. Once your program is finished working with the returned reference, does it delete the actual object created on the heap ? Something like ```
delete (XMLNode*)&myNode;
```

---

### Post by henchman on 2008-03-13
Yes :(

---

### Post by PaulFr on 2008-03-13
**myNode.getNextNode().getNextNode()** in your example will leak, because the two calls to getNextNode() will result in two extra objects on the heap in addition to myNode. So you need to delete all **three** objects. Are you doing that ?

---

### Post by henchman on 2008-03-13
Ah, now it works, i forgot an '&'

```

XMLNode myNode(); // basenode
XMLNode &my2ndNode = myNode.getNextNode();
delete (XMLNode*)&my2ndNode;

```

But i wont be able to delete the 2nd Node when i use the class like myNode.getNextNode().getNextNode();, right?

Do you think it would be senseful to register (e.g. in a vector) each created node in the 'base node' and delete them, when the base node is being destructed?

---

### Post by PaulFr on 2008-03-13
Either maintain a registry of all allocations or use smart pointers (for example shared_ptr in **[http://www.boost.org/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/libs/smart_ptr/smart_ptr.htm)**).

---

