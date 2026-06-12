---
title: "Looking for critique."
date: 2009-08-01
forum: Programming Talk
---

### Post by pepperphd on 2009-08-01
Hi there. Last night and this morning I wrote this binary search tree from nothing.  Each function has been tested, it works.  I'm looking for people willing to judge it and maybe tell me what other functions I should add to it.  Thanks.

Here is the node class:
[php]#ifndef TREENODE_H
#define TREENODE_H

#include <cstdlib>

class Tree_node
{
        long double         data;

        class Tree_node     *left,
                     *right;

    public:
    
        Tree_node(int data)
        {
            this->data = data;
            left = right = NULL;
        }

        const long double get_data(){ return data; }
        class Tree_node *get_left(){ return left; }
        class Tree_node *get_right(){ return right; }
        void set_left(class Tree_node* new_Tree_node){ left = new_Tree_node; }
        void set_right(class Tree_node* new_Tree_node){ right = new_Tree_node; }            
};

#endif
[/php]And here is the Tree class (two of its larger functions are in another file, posted below):
[php]#ifndef TREE_H
#define TREE_H

#include "treenode.h"
#include <iostream>

using namespace std;

class Tree
{
        class Tree_node        *root,
                    *current;

        void add_node(const long double data, class Tree_node *current);
        bool search(const long double search_term, class Tree_node *current);

        unsigned long long size(class Tree_node *current)
        {
             if(!current) return(0);
              else return(size(current->get_left()) + 1 + size(current->get_right())); 
        }

        void print_asc(class Tree_node *current)
        {
            if(current->get_left()) print_asc(current->get_left());
            cout << current->get_data() << endl;
            if(current->get_right()) print_asc(current->get_right());
        }

        void print_desc(class Tree_node *current)
        {
            if(current->get_right()) print_desc(current->get_right());
            cout << current->get_data() << endl;
            if(current->get_left()) print_desc(current->get_left());
        }

    public:
    
        Tree(const long double data)
        {
            root = new Tree_node(data);
            current = root;    
        }

        const long double get_min()
        {
            current = root;
            while(current->get_left())
                current = current->get_left();

            return current->get_data();        
        }

        const long double get_max()
        {
            current = root;
            while(current->get_right())
                current = current->get_right();
        
            return current->get_data();
        }

        class Tree_node *get_root(){ return root; }
        class Tree_node *get_current(){ return current; }
        void add_node(const long double data){ add_node(data, root); }
        bool search(const long double search_term){ return search(search_term, root); }
        unsigned long long size(){ return size(root); }
        void print_asc(){ print_asc(root); }
        void print_desc(){ print_desc(root); }
};

#endif[/php]Search and Add functions:
[php]#include "tree.h"

void Tree::add_node(const long double data, class Tree_node *current)
{
    if(data > current->get_data())
    {
        if(current->get_right())
            add_node(data, current->get_right());
        else    current->set_right(new Tree_node(data));
    }
    else if(data <= current->get_data())
    {
            if(current->get_left())
                add_node(data, current->get_left());
            else    current->set_left(new Tree_node(data));
    }
}

bool Tree::search(const long double search_term, class Tree_node *current)
{
    if(search_term > current->get_data())
    {
        if(current->get_right())
            return search(search_term, current->get_right());
        else    return false;
    }
    else if(search_term < current->get_data())
    {
        if(current->get_left())
            return search(search_term, current->get_left());
        else     return false;
    }
    else if(search_term == current->get_data())
        return true;
}[/php]

---

### Post by uljanow on 2009-08-01
1) Containers in C++ should be of generic type (Templates)
2) Containers in C++ should support the notion of iterators (STL is full of algorithms, etc) 
3) The tree is not balanced (worst case is O(n) ). Balanced trees like rb-trees have a worst case of  O(log n).

---

### Post by pepperphd on 2009-08-01
> **uljanow said:**
> 1) Containers in C++ should be of generic type (Templates)
2) Containers in C++ should support the notion of iterators (STL is full of algorithms, etc) 
3) The tree is not balanced (worst case is O(n) ). Balanced trees like rb-trees have a worst case of  O(log n).

Okay I made it generic.  Could you point me in the direction of an article on building an iterator for a container? As for your third point, it makes me wish I had done homework in high school.

---

### Post by scourge on 2009-08-01
> **pepperphd said:**
> Okay I made it generic.  Could you point me in the direction of an article on building an iterator for a container? As for your third point, it makes me wish I had done homework in high school.

There's already a balanced binary tree container class in STL - std::set. But if you want to reinvent it for learning purposes, that's fine.

Writing an iterator can be annoying, but shouldn't be difficult. Basically you need a class called "iterator" in your container's namespace, the container must have begin() and end() methods, and the iterator class should have the same interface as STL containers (operators ==, !=, *, ->, ++, --, etc.). It's just static polymorphism, which is what template classes and functions rely on.

Consult Wikipedia if you want to learn about balanced binary trees: [http://en.wikipedia.org/wiki/Self-balancing_binary_search_tree](http://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)

---

