---
title: "Mysterious c++ pointer issues"
date: 2010-12-20
forum: Programming Talk
---

### Post by antman8969 on 2010-12-20
I recently decided I wanted to start Qt development, which meant I had to learn c++ first. When I learn a new language, I usually start with hello world, then move onto a linked list (just habbit). I got my linked list working but on the way encounted tons of weird things that I didn't expect. I narrowed the code down to one line that breaks it. Ill post the system here:



Node.h File:
```
#ifndef NODE_H_
#define NODE_H_

class Node {
	private:
		Node* prev;
		Node* next;
		int element;
	public:
		Node(int value);
		virtual ~Node(){};
		void setNext(Node* node);
		void setNext(Node node);
		void setPrev(Node* node);
		void setPrev(Node node);
		Node* getNext(){
			return next;
		};
		Node* getPrev(){
			return prev;
		};
		int get();

};

inline Node::Node(int value) {
	next = 0;
	prev = 0;
	element = value;

};


#endif /* NODE_H_ */
```

Node.cpp File:
```
#include "Node.h"


void Node::setNext(Node* node){
	next = node;
}

void Node::setNext(Node node){
	Node* n = &node;
	next = n;
}

void Node::setPrev(Node* node){
	prev = node;
}

void Node::setPrev(Node node){
	prev = &node;
}

int Node::get(){
	return element;
}
```


LinkedList.h File:
```
#ifndef LINKEDLIST_H_
#define LINKEDLIST_H_
#include "Node.h"

class LinkedList {
	private:
		Node* first;
		Node* last;
		int length;

	public:
		LinkedList();
		virtual ~LinkedList();
		void append(int value);
		void display();
		void remove(int index);
		int get(int index);
		int sum();
};

//Inline definitions
inline LinkedList::LinkedList(){
	first = 0;
	last = 0;
	length = 0;
};

inline LinkedList::~LinkedList(){
	Node* node = first;
	for(int i = 0; i < length; i++){
		Node* tmp = node->getNext();
		delete node;
		node = tmp;
	}
};

#endif /* LINKEDLIST_H_ */
```



LinkedList.cpp File:
```
#include "LinkedList.h"
#include <iostream>
using namespace std;


void LinkedList::append(int value){

	if(length == 0){
		first = new Node(value);
		last = first;
		length++;
	}else{
		Node* node = new Node(value);
		last->setNext(node); //comment this line out
//		last->setNext(*node); //uncomment this line, it breaks
		node->setPrev(last);
		last = last->getNext();
		length++;

	}
}


int LinkedList::get(int index){
	Node* node = first;
	for(int i = 0; i < index; i++){
		node = node->getNext();
	}
	return node->get();
}

int LinkedList::sum(){
	Node* node = first;
	int sum = node->get();
	for(int i = 0; i < length-1; i++){
		node = node->getNext();
		sum += node->get();
	}
	return sum;
}


void LinkedList::display(){;
	Node* node = first;
	cout << "[";
	for(int i = 0; i < length-1; i++){
		cout << node->get() << ", ";
		node = node->getNext();
	}
	cout << node->get() << "]" << endl;
}


void LinkedList::remove(int index){
	Node* node = first;

	if(index == 0){ //Case for deleting the root node
		first = node->getNext();
		delete node;
		length--;

	}else if(index == length-1){ //case for deleting the last node
		for(int i = 0; i < index; i++){
			node = node->getNext();
		}

		Node* tmp = node->getNext();
		node->setNext(NULL);
		last = node;

		delete tmp;
		length--;

	}else if(index >= length){ //index out of bounds
//		throw index;
		cout << "index out of bounds" << endl;

	}else{ //deleting a regular node
		for(int i = 0; i < index-1; i++){
			node = node->getNext();
		}

		Node* tmp = node->getNext();
		node->setNext(tmp->getNext());

		delete tmp;
		length--;
	}


}
```

In my LinkedList::append definition, if you comment out 
    last->setNext(node); 

and uncomment 
last->setNext(*node);

the program can't execute the LinkedList::get or remove anymore. Now I was of the mind set that I made it do the exact same thing in my Node.cpp file whether it was passed a node or a pointer...but I guess not, and I don't understand why.

---

### Post by Zugzwang on 2010-12-20
```

void Node::setNext(Node node){
	Node* n = &node;
	next = n;
}

```

Here is your problem - this is not proper memory management. The object named "node" is located on the stack, as it is passed as a parameter. The space for this object is reused once the function is left. In C++, you would rather make something like:

```

void Node::setNext(Node const &node){
	Node* n = new Node(node);
	next = n;
}

```

... and implement a copy constructor for "node". But I guess that doesn't make too much sense in your case. Having two "setNext" functions, one accepting Node pointers and one accepting Nodes as parameter looks like an odd design, which is probably the root for your problem.

---

### Post by PaulM1985 on 2010-12-20
I think when you do setNode(Node node) the node object is a copy rather than a reference.  If you changed it to:

void setNode(Node &node)
{
...
}

I think it will work.  Your calling code does not need to change, just your declaration lines on the method.

Other people please feel free to correct me if I am wrong, I am more of a java/c# developer than c++

Paul

---

### Post by antman8969 on 2010-12-20
> **Zugzwang said:**
> ```

void Node::setNext(Node node){
	Node* n = &node;
	next = n;
}

```

Here is your problem - this is not proper memory management. The object named "node" is located on the stack, as it is passed as a parameter. The space for this object is reused once the function is left. In C++, you would rather....

I thought about doing that, but in my LinkedList::append I create a new node with new, so should I be making and allocating memory for two nodes? once inside of append and once inside of Node::setNext()? It seems like wasted memory, but then again I still don't understand how c++ thinks...

---

### Post by antman8969 on 2010-12-20
> **PaulM1985 said:**
> I think when you do setNode(Node node) the node object is a copy rather than a reference.  If you changed it to:

void setNode(Node &node)
{
...
}

I think it will work.  Your calling code does not need to change, just your declaration lines on the method.

Other people please feel free to correct me if I am wrong, I am more of a java/c# developer than c++

Paul

Well your suggestion worked... does that mean that I can never pass objects in as parameters?? Will I always need to pass addresses and pointers because Ill have no idea how my program will react?

---

### Post by dwhitney67 on 2010-12-20
Avoid passing by value, and making unnecessary copies of the Node(s).  Also, consider templatizing your classes so that they can be adapted to other objects (other than int).

For example:
```

template <typename T>
struct Node
{
   Node(T data) : data(data), prev(0), next(0) {}

   inline void setNext(Node<T>*& n) { next = n; }
   inline void setPrev(Node<T>*& p) { prev = p; }

   inline Node<T>* getNext() const { return next; }
   inline Node<T>* getPrev() const { return prev; }

   T        data;
   Node<T>* prev;
   Node<T>* next;

private:
   // declared, but not implemented.
   Node(const Node<T>& other);
   Node<T>& operator=(const Node<T>& other);
};


template <typename T>
class LinkedList
{
public:
   LinkedList()
      : first(0), last(0), length(0)
   {
   }

   ~LinkedList()
   {
      Node<T>* node = first;

      while (node != 0)
      {
         Node<T>* tmp = node;
         node = node->getNext();
         delete tmp;
      }

      first  = 0;
      last   = 0;
      length = 0;
   }

   void append(T value)
   {
      Node<T>* node = new Node<T>(value);

      ++length;

      if (first == 0)
      {
         first = node;
         last  = first;
      }
      else
      {
         node->setPrev(last);
         last->setNext(node);
         last = node;
      }
   }

   inline size_t getLength() const { return length; }

   template <typename TT>
   friend std::ostream& operator<<(std::ostream& os, const LinkedList<TT>& ll)
   {
      for (Node<TT>* node = ll.first; node != 0; node = node->getNext())
      {
         os << node->data << " ";
      }
      return os;
   }

private:
   Node<T>* first;
   Node<T>* last;
   size_t   length;
};


int main()
{
   LinkedList<int> ll;

   ll.append(10);
   ll.append(20);
   ll.append(30);

   std::cout << ll.getLength() << " elements: " << ll << std::endl;
}

```

---

### Post by antman8969 on 2010-12-20
> **dwhitney67 said:**
> Avoid passing by value, and making unnecessary copies of the Node(s).  Also, consider templatizing your classes so that they can be adapted to other objects (other than i...

Is there any reason in particular that you are supposed to avoid passing by value? Is this the official c++ view?

I guess templates are the c++ equivalent of java generics? If so then yea I planned on doing that too, I just wanted to get the general language syntax down before hand, but thanks for your example, that makes things a lot easier for me

---

### Post by worksofcraft on 2010-12-20
> **antman8969 said:**
> Is there any reason in particular that you are supposed to avoid passing by value? Is this the official c++ view?

I guess templates are the c++ equivalent of java generics? If so then yea I planned on doing that too, I just wanted to get the general language syntax down before hand, but thanks for your example, that makes things a lot easier for me

Passing by value creates a local copy of your data. So it is wasteful of processing time and memory when you pass a large item by value. Evidently also if you take the address of this local copy then you don't get a pointer to the original so when the local copy is destroyed you are left with an invalid pointer!

There are times when pass by value is exactly what you want but it is often a mistake. Your private copy constructors should at compile time be preventing it from happening.

---

### Post by antman8969 on 2010-12-20
> **worksofcraft said:**
> Passing by value creates a local copy of your data. So it is wasteful of processing time and memory when you pass a large item by value. Evidently also if you take the address of this local copy then you don't get a pointer to the original so when the local copy is destroyed you are left with an invalid pointer!

There are times when pass by value is exactly what you want but it is often a mistake. Your private copy constructors should at compile time be preventing it from happening.

Aah, very interesting. Also, I took the previous posters advice and converted the node and linkedlist into templates, discoving that the definition apparently has to be in the header file for templates. 

Is there ever a reason that you should avoid putting the entire class definition in the header file and define it in a .cpp file instead?

---

### Post by worksofcraft on 2010-12-20
> **antman8969 said:**
> Aah, very interesting. Also, I took the previous posters advice and converted the node and linkedlist into templates, discoving that the definition apparently has to be in the header file for templates. 

Is there ever a reason that you should avoid putting the entire class definition in the header file and define it in a .cpp file instead?

If you are using Qt you have to put all definitions in header files because it processes and generates some extra files that need to include them.

However personally for complicated modules and classes I like my header files to contain nothing but the public interface of a module.

So any classes that are used exclusively within that module I do not expose to the rest of the application.

In extreme cases I will define a pure virtual base class in the header with virtual functions and then derive "opaque" classes inside the module:

 e.g this is part of a non trivial module interface.
[php]
struct cs_numform: cs_unistring {
	// convert numeric value to Unicode "wide" string
	virtual void form(
		long iNum, // the value to format
		int iPrecision = 0, // number of digits behind decimal point
		unsigned iBase = 10, // conversion base
		charptr pOverrideTemplate = NULL
	) = 0;

	// these are created first use and then reused on subsequent calls
	// not deleted till program exits.
	static cs_numform *get_numform();
	static cs_numform *get_altform();

	virtual ~cs_numform() {}

protected:
	cs_numform() {} // only derived classes can

private:
	// preclude copy
	cs_numform(const cs_numform &);
	cs_numform & operator= (const cs_numform &);
};
[/php]

Then in the module itself I derive an "opaque" data structure
[php]
struct form_lookup: cs_numform {
protected:
... lots of internal implementation details
... for the lookup aspects of the interface (not shown)
};
...
struct tpl_state: cs_state, form_lookup {
...
public: // the actual API implementation
	void form(
		long iNum, // the value to format
		int iPrecision = 0, // number of digits behind decimal point
		unsigned iBase = 10,
		charptr pOverrideTemplate = NULL
	);

	~tpl_state(); // virtual destructor
}
[/php]

note: you can find more details of this particular class in [cs_lib-0.0.0.tar]("http://code.google.com/p/speaknumber/downloads/list") but this technique would not be necessary, or advisable for your linked list class.

The point is simply that the implementation is totally divorced from it's interface.
Thus in this shared library I can completely re-implement the way thing work and as long as the interface is unchanged, none of the programs that link to it will be affected!

---

### Post by dwhitney67 on 2010-12-20
> **antman8969 said:**
> Aah, very interesting. Also, I took the previous posters advice and converted the node and linkedlist into templates, discoving that the definition apparently has to be in the header file for templates. 

Is there ever a reason that you should avoid putting the entire class definition in the header file and define it in a .cpp file instead?

When you deal with templates, the implementation must be included within the header file.  Whether you do this within the class declaration (such as I did in my previous example), or after the class declaration is up to you.

In some development circles, the developers implement the templated class functions in a separate file, that bears a unique filename extension (ie not cpp or h), and include this file within the header file.  For example:

Node.h
```

#ifndef NODE_H
#define NODE_H

template <typename T>
class Node
{
public:
   Node(T data);
   ...
};

#include "Node.impl"

#endif

```
Node.impl:
```

// No need to include "Node.h" here!

Node<T>::Node()
   ...
{
   ...
}

```
At any rate, template code needs to be provided within the header file so that the compiler can formulate the correct function signatures for the types it comes across (e.g. Node<int>).

---

### Post by antman8969 on 2010-12-22
> **worksofcraft said:**
> If you are using Qt you have to put all definitions in header files because it processes and generates some extra files that need to include them.

However personally for complicated modules and classes I like my header files to...

Very complete explanation, thanks so much!

---

