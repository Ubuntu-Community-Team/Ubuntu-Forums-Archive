---
title: "Question about Using C++ Static Variables in Classes"
date: 2007-08-25
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-08-25
I have a class like this:

class Node 
{
  protected:
    yyltype *location;
    Node *parent;
	treeNodeScope *thisnode;
	static treeNodeScope *globalscope;

  public:
    Node(yyltype loc);
    Node();
...
}

I will be generating a bunch of instances of this node class above and I want the treeNodeScope pointer called globalscope to point to the same treeNodeScope for all instances of Node, but yet be able to set this variable from any instance of Node.  One Node will declare a treeNodeScope that will be the global scope and I want the globalscope variable of all nodes to point to that treeNodeScope.  The above compiles, but I get linking errors.  If I take out the static variable, it all compiles, but does not do as I want because there is no linking of the globalscope variable among instances of this Node class.  What should I do?

---

### Post by ryno519 on 2007-08-25
Perhaps you could post the errors you are getting?

---

