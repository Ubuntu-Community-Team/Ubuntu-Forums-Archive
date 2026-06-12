---
title: "error: ISO C++ forbids declaration of ‘CreateNode’ with no type [-fpermissive]"
date: 2017-03-03
forum: Programming Talk
---

### Post by Rahul04789 on 2017-03-03
Hi,

I am compiling following file, and I am getting the error: ISO C++ forbids declaration of &#8216;CreateNode&#8217; with no type [-fpermissive]

1) BinaryTree.h
```
ifndef BINARY_TREE_H
#define BINARY_TREE_H
namespace MyProject
{
    namespace BinaryTree
    {
        class Node
        {
            Node * m_lnode;
            int    m_data;
            Node * m_rnode;
            public:
                Node();
                void CreateNode(const int & data);
        };

        class BinaryTree
        {
            Node * m_newNode;
            public:
                BinaryTree();
                void InsertNode(const Node *newNode);
        };
    }
}

#endif
```


2) BinaryTree.cpp
```
#include "BinaryTree.h"
#include <iostream>

namespace BinaryTree = MyProject::BinaryTree;

BinaryTree::Node::Node():m_lnode(NULL),
                         m_rnode(NULL)
{
}
BinaryTree::Node::CreateNode(const int & data)
{
    m_data = data;
}
BinaryTree::BinaryTree::BinaryTree():m_newNode(NULL)
{
}
int main()
{
    return 0;
}
```


After compiling from g++,
# g++ -g -o a BinaryTree.cpp

I am getting the following three errors:

```
BinaryTree.cpp:10:46: error: ISO C++ forbids declaration of &#8216;CreateNode&#8217; with no type [-fpermissive]
 BinaryTree::Node::CreateNode(const int & data)
                                              ^
BinaryTree.cpp:10:1: error: prototype for &#8216;int MyProject::BinaryTree::Node::CreateNode(const int&)&#8217; does not match any in class &#8216;MyProject::BinaryTree::Node&#8217;
 BinaryTree::Node::CreateNode(const int & data)
 ^
```
In file included from BinaryTree.cpp:1:0:
```
BinaryTree.h:14:8: error: candidate is: void MyProject::BinaryTree::Node::CreateNode(const int&)
   void CreateNode(const int & data);
        ^
```


Regards, 
Rahul Kumar

---

### Post by spjackson on 2017-03-04
As the error message tells you, you must include the return type when defining a function, i.e.
```

[COLOR=#ff0000]void[/COLOR] BinaryTree::Node::CreateNode(const int & data)
{
    m_data = data;
}

```

---

