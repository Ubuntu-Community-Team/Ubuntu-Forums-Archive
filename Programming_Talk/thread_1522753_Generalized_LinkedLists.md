---
title: "Generalized LinkedLists"
date: 2010-07-02
forum: Programming Talk
---

### Post by hg_fs2002 on 2010-07-02
Hi, I'm trying to implement Generalized linked lists and now I've got stuck somehow.
I want to write a function in order to add nodes to the last of a Generalized linkedlist with such a class. Is someone could help me or at least give me some tips. 
 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Gnode {[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]:[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] tag;[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] flag;[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]char[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]* data;[/SIZE]
[SIZE=2]Gnode* link;[/SIZE]
[SIZE=2]Gnode* dlink;[/SIZE]
[SIZE=2]};[/SIZE]
 
Gnode* link points to the horizontal nodes and Gnode* dlink points to the vertical nodes.

---

### Post by schauerlich on 2010-07-02
I assume this is C++? You should look into templates for a truly generic class. As for adding to the end of a linked list, the easiest way is to have a class ListNode, and another class List that consists of a pointer to the first and last elements of the list, and possibly other things like the count of elements, etc. Your methods would reside in that class too.

---

### Post by hg_fs2002 on 2010-07-04
Thanks a lot. Now I don't know how to store the string I've gotton from a getline function in the LinkedList when I'm calling my Add2Last function in main.I've written this:
 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#000000] Gnode {[/COLOR][/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#000000]:[/COLOR][/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] tag;[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] flag;[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]char[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]* data;[/SIZE]
[SIZE=2]Gnode* link;[/SIZE]
[SIZE=2]Gnode* dlink;[/SIZE]
[SIZE=2]};[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#000000] Glist {[/COLOR][/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#000000]:[/COLOR][/SIZE]
[SIZE=2]Gnode* first1;[/SIZE]
[SIZE=2]Gnode* first2;[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#000000]:[/COLOR][/SIZE]
[SIZE=2]Glist () {[/SIZE]
[SIZE=2]first1=[/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Gnode;[/SIZE]
[SIZE=2]first2=[/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Gnode;[/SIZE]
[SIZE=2]first1->link=NULL;[/SIZE]
[SIZE=2]first1->dlink=NULL;[/SIZE]
[SIZE=2]first2->link=NULL;[/SIZE]
[SIZE=2]first2->dlink=NULL;[/SIZE]
[SIZE=2]}[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Add2Last ([/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]const[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] *d);[/SIZE]
[SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]};[/COLOR][/SIZE]
 
 
[SIZE=2][COLOR=#008000][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#000000] Glist::Add2Last ([/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]const[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#000000] *d){[/COLOR][/SIZE]
[SIZE=2][SIZE=2]Gnode* l;
l=[/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Gnode;
Gnode* t;
t=[/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Gnode;
l->link=NULL;
l->dlink=NULL;
l->data=[/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] [/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]char[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][strlen(([/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]char[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] *)d)];
t=first2;
t->dlink=l;
l->tag=1;
l->flag=0;
t=t->link;
[/SIZE][/SIZE][SIZE=2]}[/SIZE]
 
[SIZE=2][COLOR=black]Now I gonna call my function in main,but I don't know how to match the argument of Add2Last function in main with the one I've written.[/COLOR][/SIZE]
 
[SIZE=2][COLOR=black]main (){[/COLOR][/SIZE]
[SIZE=2][COLOR=black]string s;[/COLOR][/SIZE]
[SIZE=2][COLOR=black]...........[/COLOR][/SIZE]
[SIZE=2][COLOR=black].........[/COLOR][/SIZE]
[SIZE=2][COLOR=black]........[/COLOR][/SIZE]
[SIZE=2][SIZE=2][COLOR=black]getline (f,s,[/COLOR][/SIZE][SIZE=2][SIZE=2][COLOR=black]' '[/COLOR][/SIZE][/SIZE][SIZE=2][COLOR=black]);[/COLOR][/SIZE]
[SIZE=2][COLOR=black]D.Add2Last(s);[/COLOR][/SIZE]
[SIZE=2][COLOR=black]...........[/COLOR][/SIZE]
[SIZE=2][COLOR=black]...........[/COLOR][/SIZE]
[SIZE=2][COLOR=black]...........[/COLOR][/SIZE]
[SIZE=2][COLOR=black]}[/COLOR][/SIZE]
[/SIZE][/COLOR][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by schauerlich on 2010-07-04
You're handing in a std::string object to a class that stores a char *. You either need to use templates like I said, use s.c_str() in main, or change your GNode class to store std::string's.

Also, please put your code in [noparse][code][/noparse] tags.

---

### Post by dwhitney67 on 2010-07-05
If this is indeed C++, why not use the STL list?

For example:
```

#include <list>
#include <string>

struct NodeData
{
   int         tag;
   int         flag;
   std::string data;
};

struct Gnode
{
   std::list<NodeData*> link;
   std::list<NodeData*> dlink;
};

class Glist
{
public:
   Glist()  {}
   ~Glist() {  /* TODO */ }

   void add2Last(const std::string& data);

private:
   Gnode first1;
   Gnode first2;
};


void
Glist::add2Last(const std::string& data)
{
   NodeData* ndata = new NodeData;

   ndata->data = data;
   ndata->tag  = 1;
   ndata->flag = 0;

   first2.link.push_back(ndata);
}

```

P.S.  Some advice:  avoid mixing C and C++, and avoid passing void data to functions.

---

### Post by schauerlich on 2010-07-05
> **dwhitney67 said:**
> If this is indeed C++, why not use the STL list?

Because I'm 99% certain it's homework. :)

---

