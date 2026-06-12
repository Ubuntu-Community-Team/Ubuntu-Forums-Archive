---
title: "Look at this code for a Priority Queue please.."
date: 2009-05-07
forum: Programming Talk
---

### Post by Jiraiya_sama on 2009-05-07
Is it hard to read? Do I need to slim it down somewhere?

[PHP]
#ifndef PRIORITY_QUEUE_H
#define PRIORITY_QUEUE_H
#include <string>
#include <algorithm>
#include <iostream>

using namespace std;

template <class type>
class PriorityQueue
{
  private:
    type* heap;
    size_t allocated, size;
    bool (*lessThan)(const type&, const type&);
    struct Empty
    { Empty(const string& error = "Class is empty.") { cout << error << endl; } };
    static bool less(const type& a ,const type& b) { return a < b; }  //takes two arguments and tells you if the first is less than the second.
    void reheapifyUp(type* heap, int root, int bottom);
    void reheapifyDown(type* heap, int root, int bottom);
    void reallocate();
    void buildHeap();

  public:
    /*******************************************Constructor*/
    PriorityQueue(bool _lessThan(const type&, const type&));
    
    /**********************************Copy Control Members*/
    PriorityQueue(const PriorityQueue& cpy);
    PriorityQueue& operator=(const PriorityQueue<type>& rhs);
    ~PriorityQueue();
    
    /**********************************************Mutator*/
    void setLessThan(bool _lessThan(const type&, const type&));
            
    /*********************************************Effectors*/
    void push(const type& data);
    type& pop();
    
};

/***********************************************************************Constructor*/
template <class type>
PriorityQueue<type>::PriorityQueue(bool _lessThan(const type&, const type&) = less ) : 
  heap(new type[1]), allocated(1), size(0), lessThan(_lessThan) {}

/**************************************************************Copy Control Members*/
template <class type>
PriorityQueue<type>::PriorityQueue(const PriorityQueue<type>& cpy) : 
  heap(new type[cpy.size]), allocated(cpy.allocated), size(cpy.size), lessThan(cpy.lessThan)
{ copy(cpy.heap, cpy.heap+size, heap); }

template <class type>
PriorityQueue<type>& PriorityQueue<type>::operator=(const PriorityQueue<type>& rhs)
{
  if(this != &rhs)
  {
    allocated = rhs.allocated;
    size = rhs.size;
    lessThan = rhs.lessThan;
    delete [] heap;
    heap = new type[allocated];
    copy(rhs.heap, rhs.heap+size, heap);
  }

  return *this;
}

template <class type>
PriorityQueue<type>::~PriorityQueue()
{ delete [] heap; }


/**************************************************************************Mutators*/
/*Allows us to resort the heap by redefining what makes one object less than the other*/
template <class type>
void PriorityQueue<type>::setLessThan(bool _lessThan(const type&, const type&))
{
  if(lessThan == _lessThan)
    return;
  
  lessThan = _lessThan;
  buildHeap();
  
  return;
}

template <class type>
void PriorityQueue<type>::reheapifyUp(type* heap, int root, int bottom)
{
  int parent;

  if(bottom >= root)
  {
    parent = (bottom-1)/2;
    if(lessThan(heap[parent], heap[bottom]))
    {
      type temp = heap[parent];
      heap[parent] = heap[bottom];
      heap[bottom] = temp;

      reheapifyUp(heap,root,parent);
    }
  }
  return;
}

template <class type>
void PriorityQueue<type>::reheapifyDown(type* heap, int root, int bottom)
{
  int maxChild, leftChild = (root*2)+1, rightChild=(root*2)+2;

  if(leftChild<=bottom)
  {
    if(leftChild == bottom)
      maxChild = leftChild;
    else
    {
      if(!lessThan(heap[rightChild], heap[leftChild]))
        maxChild = rightChild;
      else
        maxChild = leftChild;
    }
    if(lessThan(heap[root], heap[maxChild]))
    {
      type temp = heap[maxChild];
      heap[maxChild]=heap[root];
      heap[root] = temp;

      reheapifyDown(heap, maxChild, bottom);
    }
  }
  return;
}

template <class type>
void PriorityQueue<type>::reallocate()
{
  type* temp = new type[allocated*=2];
  copy(heap, heap+size, temp);
  delete [] heap;
  heap = temp;
  return;
}

template <class type>
void PriorityQueue<type>::buildHeap()
{
  for(int i = (size-1)/2; i >= 0; i--)
    reheapifyDown(heap, i, size-1);
  return;
}

/*************************************************************************Effectors*/
template <class type>
void PriorityQueue<type>::push(const type& data)
{
  if(size == allocated)
    reallocate();

  heap[size] = data;
  reheapifyUp(heap, 0, size++);
  return;
}

template <class type>
type& PriorityQueue<type>::pop()
{
  if(!size)
    throw Empty();
  else
  {
    type temp = heap[0];
    heap[0] = heap[size-1];
    heap[size-1] = temp;
  }
  
  --size;
  
  reheapifyDown(heap, 0, size-1);

  return heap[size];
}
#endif
[/php]

---

### Post by dwhitney67 on 2009-05-07
You could conceivably trim it down; I do not know your particular requirements.  But take a look [here]("http://www.cplusplus.com/reference/stl/priority_queue/").


P.S.  Wrt your code, I personally would not have bothered implementing the copy-constructor and the assignment operator method.  I would have declared these methods as private, but not implement them.

---

### Post by Jiraiya_sama on 2009-05-07
> **dwhitney67 said:**
> You could conceivably trim it down; I do not know your particular requirements.  But take a look [here]("http://www.cplusplus.com/reference/stl/priority_queue/").


P.S.  Wrt your code, I personally would not have bothered implementing the copy-constructor and the assignment operator method.  I would have declared these methods as private, but not implement them.

Is it bad form to have copy control for a Priority Queue?:confused:

---

### Post by dwhitney67 on 2009-05-07
> **Jiraiya_sama said:**
> Is it bad form to have copy control for a Priority Queue?:confused:

The question is, why would you want to copy a queue?  What benefit would this have?

---

### Post by Jiraiya_sama on 2009-05-08
> **dwhitney67 said:**
> The question is, why would you want to copy a queue?  What benefit would this have?

That's not for me to decide. All I know is that I can't think of a reason why it would be a bad idea to copy the object.

Also, something I forgot to mention earlier, but consider this code utilizing this Priority_Queue class.

[php]
#include "Priority_Queue.h"
#include <iostream>

using namespace std;

int main()
{
  Priority_Queue<int> my_queue;
  
  my_queue.push(11);
  my_queue.push(5);
  my_queue.push(55);

  cout << my_queue.pop() << " " << my_queue.pop() << endl;

  return 0;
}
[/php]

It should print "55 11", but instead it prints "11 55".

Changing the cout line to:

[php]
cout << my_queue.pop() << " ";
cout << my_queue.pop() << endl;
[/php]

makes it print in the proper order. I'm guessing that g++ evaluates the two calls to my_queue.pop() in right-to-left order?

---

