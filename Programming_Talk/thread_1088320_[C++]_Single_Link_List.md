---
title: "[C++] Single Link List"
date: 2009-03-05
forum: Programming Talk
---

### Post by detorresrc on 2009-03-05
Hi,
  Anyone can give me some advice or correct my code, Im starting to study the single link list and pointer. Below is my code.

TNx



[PHP]
#include<iostream>                                                                                                                            
#include<stdio.h>                                                                                                                             
#include<stdlib.h>                                                                                                                            
#include<string.h>                                                                                                                            
#include<vector>                                                                                                                              

using namespace std;

typedef struct link {
   int  id;          
   char c;           
   link *next;       
} mylink;            

mylink *first = NULL;
mylink *current = NULL;
mylink *ptr = NULL;    
mylink *last = NULL;   
const int total_loop = 2;

int countChar(){
        int ctr = 0;
        ptr = first;
        while(ptr != NULL){
                ctr++;     
                ptr = ptr->next;
        }                       
        return ctr;             
}                               

void freePtr(){
        ptr = first;
        mylink *tmp;
        cout << "Free start" << endl;
        while(ptr != NULL){          
                tmp = ptr->next;     
                cout << "trying to free pointer ID:" << ptr->id << endl;
                free(ptr);ptr=NULL;                                     
                if( ptr == NULL ){                                      
                        cout << "OK" << endl;                           
                }else{                                                  
                        cout << "FAILED" << endl;                       
                        cout << "Value of ID:" << ptr->id << ptr->c << endl;
                }                                                           
                ptr = tmp;                                                  
        }                                                                   
        last =NULL;                                                         
        first =NULL;                                                        
}                                                                           

int getLastID(){
        if( last == NULL ){
                return 1;  
        }                  
        return last->id+1; 
}                          

void printValue(){
        mylink *pTmp;
        pTmp = first;
        while(pTmp != NULL){
                cout << "ID: " << pTmp->id << " Value: "  << pTmp->c << endl;
                pTmp = pTmp->next;                                           
        }                                                                    
}                                                                            

char * getValue(){
        int total_char = countChar();
        char *pVal = NULL;           
        pVal = new char[ total_char+1 ];
        mylink *tmp = first;            
        int ctr=0;                      
        while(tmp != NULL){             
                pVal[ctr] = tmp->c;     
                tmp = tmp->next;        
                ctr++;                  
        }                               
        *(pVal+total_char)=NULL;        
        cout << "lenght : "  << strlen(pVal) << " total_char : "  << total_char  << " ctr : "  << ctr << endl;
        return pVal;                                                                                          
}                                                                                                             

void printValue(vector<char*> name){
        for(int a=0; a<name.size(); a++){
                cout << "name[" << a  <<  "] = \"" << name.at(a) << "\"" << endl;
        }
}

int main(){
        char c;
        vector<char*> name(total_loop);
        for(int a=0; a<total_loop; a++){
                cout << "Counter : " << a << endl << endl;
                for(;;) {
                        c = cin.get();
                        if( c == '\n' ) break;
                                ptr = new mylink;
                                if (ptr == NULL) {
                                        cout << " Insufficient memory\n";
                                        exit(1);
                                }
                                ptr->c = c;
                                ptr->id = getLastID();
                                ptr->next = NULL;
                                if (first == NULL)
                                        first = current = ptr;
                                else
                                        current->next = ptr;
                                current = ptr;
                                last = current;
                }
                cout << "Total Characters : " << countChar() << endl;
                printValue();
                cout << endl;
                name.at(a) = NULL;
                name.at(a) = getValue();
                freePtr();
                cout << endl;
        }
        cout << endl << endl;
        printValue(name);
        return 0;
}


[/PHP]

---

### Post by dwhitney67 on 2009-03-06
The title of your thread indicates C++, but I believe you are using C.  Oh wait, I see that you are using 'new' and 'vector'.

What threw me off was that you are using free(), you have global variables, no encapsulation of data/methods into a List class, and you typedef'ed a struct, when that is not needed.

The STL provides a list container, however I can see the benefits of learning the basics of putting together a list.  There are certain C++ applications where using the STL is not warranted/desirable.

Typically a list supports the following operations:
[LIST]
[*]insert item
[*]delete item
[*]retrieve item(s)
[/LIST]

You can take the first operation, insert item, and expand this to allow insertion at the front of the list, the back of the list, or some place in the middle.  The same applies to deleting an item:  from the front, the back, or somewhere in the middle.

For retrieving items, this may include deleting an item and returning it to the callee, or merely providing a read-only iterator for one to use to examine the list's contents.

If you want to augment the list with more features, then consider adding an operation that allows one to sort the list.

So with all this in mind, consider the following, which mind you, is very basic:
```

class MyList
{
  public:
    MyList();
    virtual ~MyList();

    void    insert(int value);
    void    remove(int value);
    int     getValue(int index) const;
    size_t  size() const;

  private:
    struct Node
    {
      int   value;
      Node* next;
    };

    Node*  m_list;
    size_t m_size;
};

...

int main()
{
  MyList ml;

  ml.insert(20);
  ml.insert(30);
  ml.insert(10);

  for (size_t i = 0; i < ml.size(); ++i)
  {
    std::cout << ml.getValue(i) << " ";
  }
  std::endl;
}

```
A single-linked list should, at a minimum, be this simple and very easy to use.  The details of the list (i.e. node allocation and management, node deletion, etc.) should be completely hidden from the application developer whenever a MyList is used.

Anyhow, if you have any questions, let me know.

---

### Post by detorresrc on 2009-03-06
Ok tnx, can you paste the complete codes? tnx

---

### Post by dwhitney67 on 2009-03-06
The code I presented earlier was just something I pieced together in my head.

Here's something that's more complicated, and in fact so complicated that it would just be easier to use the STL list:
```

#ifndef NONSTD_LIST_H
#define NONSTD_LIST_H

#include <unistd.h>
#include <cassert>


namespace nonstd
{

template <class T>
class List
{
  private:
    class ListIterator;

  public:
    typedef ListIterator       iterator;
    typedef const ListIterator const_iterator;
    typedef T                  value_type;

    // constructor
    List()
      : m_head(0),
        m_tail(0),
        m_size(0)
    {
    }

    List(const List<T>& other)
      : m_head(0),
        m_tail(0),
        m_size(0)
    {
      for (iterator it = other.begin(); it != other.end(); ++it)
      {
        push_back(*it);
      }
    }

    // destructor
    ~List()
    {
      clear();
      m_head = m_tail = 0;
    }

    // push_front()
    void push_front(T elem)   // inserts at the beginning
    {
      if (m_head == 0)
      {
        m_head = new Node(elem, 0, 0);
        m_tail = m_head;
      }
      else
      {
        m_head = new Node(elem, 0, m_head);
      }
      ++m_size;
    }

    // pop_front()
    void pop_front()         // deletes the first element
    {
      Node* tmp = m_head->m_next;
      delete m_head;
      m_head = tmp;
      m_head->m_prev = 0;
      --m_size;
    }

    void push_back(T elem)   // inserts at the end
    {
      if (m_head == 0)
      {
        m_head = new Node(elem, 0, 0);
        m_tail = m_head;
      }
      else
      {
        m_tail->m_next = new Node(elem, m_tail, 0);
        m_tail = m_tail->m_next;
      }
      ++m_size;
    }

    void pop_back()         // deletes the last element
    {
      Node* tmp = m_tail;
      m_tail = tmp->m_prev;
      delete tmp;
      --m_size;
    }

    iterator insert(iterator& position, const T& elem)
    {
      iterator it = begin();

      for (; it != position; ++it);

      it.m_node->m_prev->m_next = new Node(elem, it.m_node->m_prev, it.m_node);
      ++m_size;

      return it.m_node->m_prev->m_next;
    }

    iterator erase(iterator position)
    {
      iterator it = begin();

      for (; it != position; ++it);

      it.m_node->m_prev->m_next = it.m_node->m_next;
      it.m_node->m_next->m_prev = it.m_node->m_prev;

      iterator next = it.m_node->m_next;

      delete it.m_node;

      --m_size;

      return next;
    }

    void clear()
    {
      iterator it = begin();

      while (it != 0)
      {
        Node* node = it.m_node;
        ++it;
        delete node;
      }
      m_size = 0;
    }

    size_t size() const
    {
      return m_size;
    }

    iterator begin()
    {
      return m_head;
    }

    const_iterator begin() const
    {
      return m_head;
    }

    iterator end()
    {
      return 0;
    }

    const_iterator end() const
    {
      return 0;
    }

    iterator last()
    {
      return m_tail;
    }

    const_iterator last() const
    {
      return m_tail;
    }

    void sort()
    {
      // we always number elements in linked list as 1, 2, ..., n
      // instead of 0, 1, ..., n-1; hence start index is 1.
      m_head = quicksort(m_head, 1, m_size);

      // restore previous-element pointers
      Node* node  = m_head;
      Node* pnode = 0;

      while (node != 0)
      {
        node->m_prev = pnode;
        pnode = node;
        node  = node->m_next;
      }
      m_tail = pnode;
    }

    typedef bool (*Sorter)(const T& first, const T& second);

    void sort(Sorter s)
    {
    }

  private:
    struct Node
    {
      Node(T elem, Node* prev, Node* next) : m_elem(elem), m_prev(prev), m_next(next) {}
      bool operator>(const Node& other)  { return m_elem > other.m_elem;  }
      bool operator<(const Node& other)  { return m_elem < other.m_elem;  }
      bool operator==(const Node& other) { return m_elem == other.m_elem; }

      T     m_elem;
      Node* m_prev;
      Node* m_next;
    };

    class ListIterator
    {
      public:
        typedef T iterator_category;

        ListIterator(Node* head) : m_node(head) {}

        ListIterator(const ListIterator& it) : m_node(it.m_node) {}

        bool operator==(const ListIterator& other) const { return m_node == other.m_node; }
        bool operator!=(const ListIterator& other) const { return m_node != other.m_node; }

        void operator++()   // goto the next element
        {
          assert(m_node != 0);
          m_node = m_node->m_next;
        }

        void operator--()   // goto the previous element
        {
          assert(m_node != 0);
          m_node = m_node->m_prev;
        }

        T& operator*()      // access the current element
        {
          assert(m_node != 0);
          return m_node->m_elem;
        }

    private:
        friend class List<T>;
        Node* m_node;
    };


    // quicksort()
    //
    Node* quicksort(Node* list, unsigned int listStart, unsigned int listEnd)
    {
      if (listStart >= listEnd)
        return list;

      unsigned int i = listStart;
      unsigned int j = listEnd - 1;

      Node* right = getNthNode(list, listEnd);
      Node* left  = getNthNode(list, listStart);
      Node* pivot = selectPivot(left, right);
      right       = findPrev(left, pivot);

      for (;;)
      {
        // now start partitioning the list
        for (; left->m_elem < pivot->m_elem; ++i)
        {
          left = left->m_next;
        }

        for (; (right->m_elem > pivot->m_elem) && (j > 1); --j)
        {
          right = findPrev(list, right);
        }

        if (i < j)
        {
          list = swapNodes(list, left, right);

          // left, right ptrs got swapped, to continue traversing we need them
          // back at the same positions.
          Node* tmp = left;
          left  = right;
          right = tmp;
        }
        else
        {
          break;
        }
      }

      // restore pivot
      list = swapNodes(list, left, pivot);

      // now sort on smaller linked lists
      list = quicksort(list, listStart, i-1);
      list = quicksort(list, i+1, listEnd);

      return list;
    }

    // getNthNode()
    //
    Node* getNthNode(Node* list, unsigned int n)
    {
      for (unsigned int i = 1; list != 0 && i < n; ++i)
      {
        list = list->m_next;
      }

      return list;
    }

    // selectPivot()
    //
    Node* selectPivot(Node* list, Node* end)
    {
      unsigned int n = numNodes(list, end);
      Node* noden = getNthNode(list, (unsigned int)((float)n/2 + 0.5));
      Node* right = findPrev(list, end);

      if (noden != right)
      {
        // swap the pivot and right most element in the list
        // later pivot will be restored.
        swapNodes(list, noden, right->m_next);
        return noden;
      }
      else
      {
        return noden->m_next;
      }
    }

    // numNodes()
    //
    unsigned int numNodes(Node* list, Node* end)
    {
      unsigned int i = 1;

      for (; list && (list != end); ++i, list = list->m_next);

      return (list == end ? i : 0);
    }

    // findPrev()
    //
    Node* findPrev(Node* list, Node* curr)
    {
      for (; list && list->m_next; list = list->m_next)
      {
        if (list->m_next == curr)
          break;
      }

      if (list->m_next != curr)
      {
        // we did not find any element; probably indicates what
        // we are searching for is the beginning node.
        return curr;
      }

      return list;
    }

    // swapNodes()
    //
    // A complete swap algorithm which cares of several scenarios while swapping
    // two nodes in a linked list which doesn't have any special nodes.
    // Scenarios considered while swapping:
    // 1) two nodes which are far away
    // 2) two nodes which are far away, one is node at the beginning of the list
    // 3) two nodes which are neighbors
    // 4) two nodes which are neighbors, one node is at the beginning of the list
    Node* swapNodes(Node* list, Node* node1, Node* node2)
    {
      Node* node1prev = findPrev(list, node1);
      Node* node2prev = findPrev(list, node2);
      Node* tmp       = node2->m_next;

      // check whether node to be swapped is in beginning (i.e. header node)
      if (node1 != list)
      {
        node1prev->m_next = node2;
      }
      else
      {
        // as we do not have special header node, if the first node and some
        // other node, need to be swapped, then update the list (makes new min
        // node as logical header)
        list = node2;
      }

      // are nodes to be swapped neighboring nodes?
      if (node1->m_next == node2)
      {
        node2->m_next = node1;
        node1->m_next = tmp;
      }
      else
      {
        // nodes to be swapped are not neighbor nodes, they are apart;
        // so condiser all scenarios
        node2->m_next = node1->m_next;
        node1->m_next = tmp;
        node2prev->m_next = node1;
      }

      return list;
    }

    // Data Members
    Node*  m_head;
    Node*  m_tail;
    size_t m_size;
};

} // end namespace nonstd

#endif

```
Here's the test program:
```

#include "List.h"

#include <algorithm>
#include <iostream>
#include <cassert>


template <typename T> void displayValue(T& value);


int main(int argc, char** argv)
{
  nonstd::List<int> list1;

  list1.push_back(2);
  list1.push_back(5);
  list1.push_back(3);
  list1.push_back(0);
  list1.push_back(4);
  list1.push_back(8);
  list1.push_back(9);
  list1.push_back(7);
  list1.push_back(6);
  list1.push_back(1);

  std::cout << "Before sorting:\n";
  std::for_each(list1.begin(), list1.end(), displayValue<int>);
  std::cout << "nil" << std::endl;

  list1.sort();
  std::cout << "After sorting:\n";
  std::for_each(list1.begin(), list1.end(), displayValue<int>);
  std::cout << "nil" << std::endl;

  list1.push_front(13);
  list1.push_front(14);
  list1.push_back(11);
  list1.push_back(10);
  list1.push_back(12);
  std::cout << "After inserting 13, 14, 11, 10, 12:\n";
  std::for_each(list1.begin(), list1.end(), displayValue<int>);
  std::cout << "nil" << std::endl;

  list1.sort();
  std::cout << "After sorting:\n";
  std::for_each(list1.begin(), list1.end(), displayValue<int>);
  std::cout << "nil" << std::endl;

  std::cout << "Iterating backwards:\nnil";
  for (nonstd::List<int>::iterator it = list1.last(); it != 0; --it)
  {
    std::cout << " <- " << *it;
  }
  std::cout << std::endl;

  return 0;
}


template <typename T> void displayValue(T& node)
{
  std::cout << node << " -> ";
}

```

---

