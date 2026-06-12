---
title: "[SOLVED] c++ - new objects always have the same address"
date: 2008-12-13
forum: Programming Talk
---

### Post by Despot Despondency on 2008-12-13
Hi, I've written a class called AnagramNode that is going to keep 26 pointers to other AnagramNodes in a map, one for each letter of the alphabet. Now I'm trying to test the code, and one test I'm doing is checking that the destructor is working correctly by correctly deleting local instances of AnagramNode. Anyway here is my code

```

#include "AnagramNode.h"

#include <string>
#include <iostream>

using namespace std;

static size_t size = 26;
static AnagramNode* null = 0;
static string letters = "abcdefghijklmnopqrstuvwxyz";

AnagramNode::AnagramNode(){

  create();

  createMap();
}

AnagramNode::AnagramNode(const AnagramNode& node){create(node);}

AnagramNode::~AnagramNode(){uncreate();}

AnagramNode& AnagramNode::operator=(const AnagramNode& rhs){

  if(&rhs != this){
  
    uncreate();

    create(rhs);
  }

  return *this;
}

void AnagramNode::create(){

  begin = alloc.allocate(size);

  end = begin + size;
  
  uninitialized_fill(begin, end, null);
}

void AnagramNode::create(const AnagramNode& n){

  begin = alloc.allocate(size);

  end = uninitialized_copy(n.getBegin(), n.getEnd(), begin);

  AnagramNode** point = begin;

  for(string::const_iterator i = letters.begin(); i != letters.end(); i++){

    children[*i] = *point;

    point++;
  }

}

void AnagramNode::uncreate(){

  for(AnagramNode** i = begin; i != end; i++){
    if(*i)
      alloc.destroy(i);
  }

  alloc.deallocate(begin, end - begin);

  begin = end = 0;
}

void AnagramNode::addChild(const char letter, AnagramNode& node){

  children[letter] = &node;

  updatePointer(letter,node);
}

bool AnagramNode::hasChild(const char letter){

  if(children[letter] != 0)
    return true;
  else 
    return false;
}

AnagramNode& AnagramNode::getChild(const char letter){

  return *children[letter];
}

void AnagramNode::createMap(){

  AnagramNode** point = begin;

  for(string::const_iterator i = letters.begin(); i != letters.end(); i++){

    children[*i] = *point;

    point++;
  }
}

void AnagramNode::updatePointer(const char letter, AnagramNode& node){

  AnagramNode** point = begin;

  for(string::iterator i = letters.begin(); i != letters.end(); i++){
    if(*i == letter)
      *point = &node;

    point++;
  }

}

```

with the header file

```

#ifndef ANAGRAM_NODE_H
#define ANAGRAM_NODE_H

#include <map>
#include <memory>

class AnagramNode{

 public:

  AnagramNode();

  AnagramNode(const AnagramNode&);

  AnagramNode& operator=(const AnagramNode&);

  ~AnagramNode();

  AnagramNode** getBegin() const {return begin;}
  AnagramNode** getEnd() const {return end;}

  void addChild(const char, AnagramNode&);

  bool hasChild(const char);

  AnagramNode& getChild(const char);

 private:

  std::map<const char, AnagramNode*> children;

  AnagramNode** begin;
  AnagramNode** end;

  std::allocator<AnagramNode*> alloc;

  void create();

  void create(const AnagramNode&);

  void uncreate();

  void createMap();

  void updatePointer(const char, AnagramNode&);

};
#endif


```

Now I've written a bit of code to check the destructor

```

#include "AnagramNode.h"

#include <iostream>

using namespace std;

int main(){

  for(int i = 0; i <5; i++){
    
    AnagramNode y;

    cout << &y << endl;
  }

  return 0;

}

```

and when I run it I get 

./test_AnagramNode
0xbfb74828
0xbfb74828
0xbfb74828
0xbfb74828
0xbfb74828

Is this the correct sort of behaviour, because it seems a bit weird. Thanks in advance.

---

### Post by arrancaru on 2008-12-13
You are printing, 5 times, the address of the same variable. This is correct for me.

---

### Post by CptPicard on 2008-12-13
If you printed something in the constructor of your variable, you'd see that indeed, you are constructing y 5 times, however... every time it is located in the same place on the stack, therefore, all of the 5 y's have the same address.

If you were new'ing them on the heap however, things would be different.

---

### Post by Despot Despondency on 2008-12-13
I thought that local variables are destroyed at the end of each iteration of the for-loop. Is this not right?

Hi CptPicard, thanks for your response. What do you mean by 'new'ing them on the heap'?

---

### Post by Despot Despondency on 2008-12-13
Sorted out my problem. cheers anyway.

---

