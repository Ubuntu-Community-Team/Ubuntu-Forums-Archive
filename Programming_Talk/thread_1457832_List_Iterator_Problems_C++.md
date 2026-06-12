---
title: "List Iterator Problems C++"
date: 2010-04-19
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-04-19
Ey guys, I am getting some strange compiler errors when I am pretty sure I am doing everything correctly. Here is what I have:
```

#ifndef stack_h
#define stack_h

#include <iostream>
#include <list>
#include <string>
#include "stackNode.h"

using namespace std;

template <class T>
class stack{
private:
	list< stackNode<T> > stackList;
public:
	stack();
	void addVar(string var, T val);
	T getVal(string var);
	//void print();
}; //class filePos

template <class T>
stack<T>::stack(){
	
}

template <class T>
void stack<T>::addVar(string var, T val){
	stackNode<T> *tempStackNode = new stackNode<T>(var, val);
	stackList.push_front(*tempStackNode);
}//addVar()

template <class T>
T stack<T>::getVal(string var){
	typename list<T>::iterator itr;
	for (itr = stackList.begin() ; itr != stackList.end(); itr++){ //problems here!

        }
}//getVal()

```
And these are the errors I am getting:
```

.../stack.h:47: error: no match for 'operator=' in 'itr = __gnu_debug_def::list<_Tp, _Allocator>::begin() [with _Tp = stackNode<universalType>, _Allocator = std::allocator<stackNode<universalType> >]()'

.../stack.h:47: error: no match for 'operator!=' in 'itr != __gnu_debug_def::list<_Tp, _Allocator>::end() [with _Tp = stackNode<universalType>, _Allocator = std::allocator<stackNode<universalType> >]()'

```
And I am following this: [http://www.cplusplus.com/reference/stl/list/begin/](http://www.cplusplus.com/reference/stl/list/begin/) but still I get errors and I have no idea why its complaining about overloaded operators. Any help would be greatly appreciated. Thanks!

---

### Post by scourge on 2010-04-19
I think you have to replace this:
```
typename list<T>::iterator itr;
```
with this:
```
typename list<stackNode<T> >::iterator itr;
```

Also, this is a bit weird:
```

stackNode<T> *tempStackNode = new stackNode<T>(var, val);
stackList.push_front(*tempStackNode);

```

Why not just do:
```
stackList.push_front(stackNode<T>(var, val));
```

---

### Post by MadCow108 on 2010-04-19
edit: misinterpreted the code
scourge's solution should work
but if you want to do a string <-> value lookup a map (or boost::unordered_map) is the far better solution than a list
also there is a stack built in c++ already

---

### Post by StunnerAlpha on 2010-04-19
> **scourge said:**
> I think you have to replace this:
```
typename list<T>::iterator itr;
```
with this:
```
typename list<stackNode<T> >::iterator itr;
```

Also, this is a bit weird:
```

stackNode<T> *tempStackNode = new stackNode<T>(var, val);
stackList.push_front(*tempStackNode);

```

Why not just do:
```
stackList.push_front(stackNode<T>(var, val));
```

Oh thanks, made both of those changes and they work fine. Thanks!

---

### Post by StunnerAlpha on 2010-04-19
> **MadCow108 said:**
> edit: misinterpreted the code
scourge's solution should work
but if you want to do a string <-> value lookup a map (or boost::unordered_map) is the far better solution than a list
also there is a stack built in c++ already

I'm not trying to replicate a stack's datatype's function per-say. I just call it a "Stack" since it holds the variables and their values in my programming language. I need to have a way of looking through all variable names and finding the one I want to retrieve, or set, the value to. I believe Craucer was trying to convince me to implement a hash table instead of a linked list but I opted not to at least for the time being as it is supposed to be relatively small-scale. Thanks for your input I will consider it if I am looking to revamping it.

---

