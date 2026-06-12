---
title: "How to implement comparators for C++ set?"
date: 2010-11-10
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-11-10
I am using a C++ STL set.  When I insert an object into the set, linking fails.  When I remove the insert line, it compiles and links fine.  If I am putting an object into a set, what operators do I have to implement and how?  Can someone show me an example of what operator(s) would need to be implemented to store this class in a set:

class Node
{
	private:
		string name;
	
	public:
		Node(string name)
		{
			this->name = name;
		}		
};

---

### Post by dwhitney67 on 2010-11-10
Here's one way:
```

#include <set>
#include <string>
#include <iostream>
#include <iterator>

class Node
{
public:
   Node(const std::string& name)
      : myName(name)
   {
   }

   bool operator<(const Node& other) const
   {
      return myName < other.myName;
   }

   friend std::ostream& operator<<(std::ostream& os, const Node& node)
   {
      os << node.myName;
      return os;
   }

   std::string name() const { return myName; }

private:
   std::string myName;
};

bool compareNode(const Node& lhs, const Node& rhs)
{
   return lhs < rhs;
}


int main()
{
   std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(compareNode);

   nodeSet.insert(Node("node 1"));
   nodeSet.insert(Node("node 3"));
   nodeSet.insert(Node("node 2"));

   std::copy(nodeSet.begin(), nodeSet.end(), std::ostream_iterator<Node>(std::cout, "\n"));
}

```

For a description on another technique, read here: [http://www.cplusplus.com/reference/stl/set/set/](http://www.cplusplus.com/reference/stl/set/set/)


P.S.  In the future, _please_ present a program that is compilable.

---

### Post by SNYP40A1 on 2010-11-15
> **dwhitney67 said:**
> Here's one way:
```

#include <set>
#include <string>
#include <iostream>
#include <iterator>

class Node
{
public:
   Node(const std::string& name)
      : myName(name)
   {
   }

   bool operator<(const Node& other) const
   {
      return myName < other.myName;
   }

   friend std::ostream& operator<<(std::ostream& os, const Node& node)
   {
      os << node.myName;
      return os;
   }

   std::string name() const { return myName; }

private:
   std::string myName;
};

bool compareNode(const Node& lhs, const Node& rhs)
{
   return lhs < rhs;
}


int main()
{
   std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(compareNode);

   nodeSet.insert(Node("node 1"));
   nodeSet.insert(Node("node 3"));
   nodeSet.insert(Node("node 2"));

   std::copy(nodeSet.begin(), nodeSet.end(), std::ostream_iterator<Node>(std::cout, "\n"));
}

```

For a description on another technique, read here: [http://www.cplusplus.com/reference/stl/set/set/](http://www.cplusplus.com/reference/stl/set/set/)


P.S.  In the future, _please_ present a program that is compilable.

Thanks dwhitney67.  Below is the full code that I am trying to compile following your example.  I'm having a bit of difficulty and this is the error message:

$ make
g++ -c -Wall -Wno-unknown-pragmas -Wno-format -O3 -DTIXML_USE_STL  sramxml.cpp -
o sramxml.o
sramxml.cpp:46: error: `compareNode' is not a type
sramxml.cpp:46: error: ISO C++ forbids declaration of `parameter' with no type
sramxml.cpp: In function `int main()':
sramxml.cpp:72: error: `compareNode' undeclared (first use this function)
sramxml.cpp:72: error: (Each undeclared identifier is reported only once for eac
h function it appears in.)
make: *** [sramxml.o] Error 1 

It's complaining about this line:

	std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(compareNode);

Do you know what the problem is?  I think it's expecting a function pointer.  However, since I am trying to declare the set on the stack, not sure how to set it up.  Note, I would have posted my code earlier, but I'm using tinyxml project.  If you want to compile, simply comment those lines out for now.

[PHP]
/*
Test program for TinyXML.
*/

#include <iostream>
#include <sstream>
#include <map>
#include <set>
using namespace std;


#include "tinyxml.h"

//
// This file demonstrates some basic functionality of TinyXml.
// Note that the example is very contrived. It presumes you know
// what is in the XML file. But it does test the basic operations,
// and show how to add and remove nodes.
//

class Node
{
private:
	string name;
	map<string, string> attributes;
	Node* outputnode;
	
public:
	Node(string name)
	{
		this->name = name;
	}	
	virtual ~Node() { }		
	void AddAttribute(string name, string value) { attributes[name] = value; }
	virtual void setupNode();
	bool operator<(const Node& other) const { return name < other.name; }
	bool compareNode(const Node& lhs, const Node& rhs)
	{
		return lhs < rhs;
	}
};

class Process : public Node
{
private:
	std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(compareNode);

public: 
	Process(string name) : Node(name) { }
	void addNode(string name);
};

void Process::addNode(string name)
{
	Node node(name);
	//nodes.insert(node);
}


class TestInstance : public Node
{
public:
	TestInstance(string name) : Node(name) { }
};

int main()
{
	cout << "Hello world" << endl;
	TiXmlDocument tixml("TestFlow");
	tixml.LoadFile("example.xml");
	TiXmlElement* root = tixml.RootElement();
	std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(compareNode);
	
	for(TiXmlAttribute* attribute = root->FirstAttribute(); attribute != NULL; attribute = attribute->Next())
	{
		cout << "Name: " << attribute->Name() << " Value: " << attribute->Value() << endl;
	}	
	return 0;
}
[/PHP]

---

### Post by GeneralZod on 2010-11-15
Note that in dwhitney67's post, compareNode is a free function, not a member of Node.

---

### Post by SNYP40A1 on 2010-11-15
> **GeneralZod said:**
> Note that in dwhitney67's post, compareNode is a free function, not a member of Node.

I tried it as a free function and also got compile errors...it could be a free function, no reason not to do it that way.  The problem is that I need to pass a function pointer to the set constructor.  However, since I want to declare the set as a class member variable, I don't know how to cast the compare function into a function pointers...I tried:

std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(&compareNode);

but no go.

---

### Post by GeneralZod on 2010-11-15
The 

```

    std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(compareNode); 

```

inside class Process won't work: you can't initialise a class member like that.

---

### Post by SNYP40A1 on 2010-11-15
> **GeneralZod said:**
> The 

```

    std::set<Node, bool (*)(const Node&, const Node&)> nodeSet(compareNode); 

```

inside class Process won't work: you can't initialise a class member like that.

Yes, the compiler tells me that as well.  So how do I provide a function pointer comparator for a set initialized as a class member?

---

### Post by dwhitney67 on 2010-11-15
A common misconception with newbie C++ programmers is that the initialization of a class transpires within the body of the class constructor.  This is not true!  It occurs before the body of the constructor is ever reached.

For example:
```

class Foo
{
public:
   Foo();

   ...

private:
   int val1;
   int val2;
};

Foo::Foo()
   // initialization takes place here!!!
   : val1(10),
     val2(20)
{
   // not in here!
}

```

To answer your question concerning how to initialize the std::set, here's how:
```

...

class Foo
{
public:
   Foo()
      : myNodeSet(compareNode)   // Initialize class data member(s) here!
   {
      // nothing to do here; class is already constructed.
   }

   void addNode(const Node& node)
   {
      myNodeSet.insert(node);
   }

   friend std::ostream& operator<<(std::ostream& os, const Foo& foo)
   {
      std::copy(foo.myNodeSet.begin(), foo.myNodeSet.end(), std::ostream_iterator<Node>(os, "\n"));
      return os;
   }

private:
   static bool compareNode(const Node& lhs, const Node& rhs)
   {
      return lhs < rhs;
   }

   std::set<Node, bool (*)(const Node&, const Node&)> myNodeSet;
};


int main()
{
   Foo foo;

   foo.addNode(Node("node 1"));
   foo.addNode(Node("node 3"));
   foo.addNode(Node("node 2"));

   std::cout << foo << std::endl;
}

```

---

### Post by SNYP40A1 on 2010-11-19
Thanks, that works!  It turns out though that you don't actually need to implement the set comparator for storing objects.  In fact, I'm not sure what the comparator is used for, I thought it was needed to order the elements in a binary tree for storing, but maybe it's using a hash map.

---

