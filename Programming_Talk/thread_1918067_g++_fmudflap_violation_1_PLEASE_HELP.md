---
title: "g++ fmudflap violation 1 PLEASE HELP"
date: 2012-01-31
forum: Programming Talk
---

### Post by ldkz2524 on 2012-01-31
My program compiles perfectly fine on Visual Studio, but keeps on getting fmudflap violation in g++ tell me what's wrongT_T
```

#ifndef MAP_INCLUDED
#define MAP_INCLUDED
#include <string>
typedef std::string KeyType;
typedef double ValueType;
class Map
{
  public:
    Map();
	Map(const Map& other);
	~Map();
    bool empty() const;
    int  size() const;
    bool insert(const KeyType& key, const ValueType& value);
    bool update(const KeyType& key, const ValueType& value);
    bool insertOrUpdate(const KeyType& key, const ValueType& value);
    bool erase(const KeyType& key);
    bool contains(const KeyType& key) const;
    bool get(const KeyType& key, ValueType& value) const;
    bool get(int i, KeyType& key, ValueType& value) const;
    void swap(Map& other);
	void dump() const;
    Map& operator=(const Map& rhs);
private:
	struct Node
	{
		KeyType m_key;
		ValueType m_value;
		Node* next;
		Node* prev;
	};
	Node* head;
	Node* end;
	int m_size;
};
bool combine(const Map& m1, const Map& m2, Map& result);
void subtract(const Map& m1, const Map& m2, Map& result);
#endif
```
```
#include "Map.h"
#include <iostream>
Map::Map() : m_size (0)
{
	head = new Node;
	end = new Node;
	head ->prev = NULL;
	head -> next = end;
	end -> prev = head;
	end -> next = NULL;
}
Map::Map(const Map& other)
{
	if (other.m_size == 0)
	{
		head = new Node;
		end = new Node;
		head ->prev = NULL;
		head -> next = end;
		end -> prev = head;
		end -> next = NULL;
		m_size =0;
	}
	else
	{
		head = new Node;
		Node* current2 = head;
		for (Node* current1 = other.head-> next;current1 -> next != NULL;current1 = current1 -> next)
		{
			Node* temp = new Node;
			temp -> m_key = current1 -> m_key;
			temp -> m_value = current1 -> m_value;
			current2 -> next = temp;
			temp -> prev = current2;
			current2 = current2 -> next;
		}
		end = new Node;
		current2 -> next = end;
		end -> prev = current2;
		end -> next = NULL;
		m_size = other.m_size;
	}
}
Map::~Map()
{
	ValueType v;
	KeyType k;
	while (!empty())
	{
		get(0,k,v);
		erase(k);
	}
	delete head;
	delete end;
}
Map& Map::operator=(const Map& rhs)
{
    if (this != &rhs)
    {
		ValueType v;
		KeyType k;
		while (!empty())
		{	
			get(0,k,v);
			erase(k);
		}
        Map temp(rhs);
		Node* current = rhs.end -> prev;
		int q=rhs.size()-1;
		while (q >= 0)
		{
			rhs.get(q,k,v);
			q--;
			insert(k,v);
			current = current -> prev;
		}
    }
    return *this;
}
bool Map::empty() const
{
	if (m_size ==0)
		return true;
	return false;
}
int Map::size() const
{
	return m_size;
}
bool Map::insert(const KeyType& key, const ValueType& value)
{
	Node *current = head-> next;
	while (current -> next != NULL)
	{
		if (current -> m_key == key)
			return false;
		current = current -> next;
	}
	Node* temp = new Node;
	temp -> next = head -> next;
	head -> next = temp;
	temp -> m_key = key;
	temp -> m_value = value;
	temp -> next -> prev = temp;
	temp -> prev = head;
	m_size++;
	return true;
}
bool Map::update(const KeyType& key, const ValueType& value)
{
	Node *current = head-> next;
	while (current -> next != NULL)
	{
		if (current -> m_key == key)
		{
			current -> m_value = value;
			return true;
		}
		current = current -> next;
	}
	return false;
}
bool Map::insertOrUpdate(const KeyType& key, const ValueType& value)
{
	Node *current = head-> next;
	while (current -> next != NULL)
	{
		if (current -> m_key == key)
		{
			current -> m_value = value;
			return true;
		}
		current = current -> next;
	}
	Node* temp = new Node;
	temp -> next = head -> next;
	head -> next = temp;
	temp -> m_key = key;
	temp -> m_value = value;
	temp -> next -> prev = temp;
	temp -> prev = head;
	m_size++;
	return true;
}
bool Map::erase(const KeyType& key)
{
	Node *current = head-> next;
	while (current -> next != NULL)
	{
		if (current -> m_key == key)
		{
			Node* before = current -> prev;
			before -> next = current -> next;
			Node* temp = before -> next;
			temp -> prev = before;
			m_size--;
			return true;
		}
		current = current -> next;
	}
	return false;
}
bool Map::contains(const KeyType& key) const
{
	Node *current = head-> next;
	while (current -> next != NULL)
	{
		if (current -> m_key == key)
		{
			return true;
		}
		current = current -> next;
	}
	return false;
}
bool Map::get(const KeyType& key, ValueType& value) const
{
	Node *current = head-> next;
	while (current -> next != NULL)
	{
		if (current -> m_key == key)
		{
			value = current -> m_value;
			return true;
		}
		current = current -> next;
	}
	return false;
}
bool Map::get(int i, KeyType& key, ValueType& value) const
{
	Node* current = head -> next;
	if (i >= m_size)
		return false;
	for (int k=0;k<i;k++)
		current = current -> next;
	key = current -> m_key;
	value = current -> m_value;
	return true;
}
void Map::swap(Map& other)
{
	Node* temp;
	temp = other.head;
	other.head = head;
	head = temp;
	int tempSize = m_size;
	m_size = other.m_size;
	other.m_size = tempSize;
}
void Map::dump () const
{
	for (Node* current = head -> next;current -> next != NULL; current = current -> next)
	{
		std::cerr << current -> m_key<<std::endl;
		std::cerr << current -> m_value<<std::endl;
	}
}
bool combine(const Map& m1, const Map& m2, Map& result)
{
	Map temp;
	KeyType keyTemp;
	ValueType valueTemp;
	ValueType valueTemp2;
	bool check;
	bool final = true;
	for (int k=0;k<m1.size();k++)
	{
		m1.get(k,keyTemp,valueTemp);
		temp.insert(keyTemp,valueTemp);
	}
	for (int z=0;z<m2.size();z++)
	{
		m2.get(z,keyTemp,valueTemp);
		check = temp.insert(keyTemp,valueTemp);
		if (check == false)
		{
			temp.get(keyTemp,valueTemp2);
			if (valueTemp2 != valueTemp)
			{
				temp.erase(keyTemp);
				final = false;
			}
		}
	}
	for (int p=0;p<temp.size();p++)
	{
		temp.get(p,keyTemp,valueTemp);
		result.insertOrUpdate(keyTemp,valueTemp);
	}
	return final;
}
void subtract(const Map& m1, const Map& m2, Map& result)
{
	Map temp;
	KeyType keyTemp;
	ValueType valueTemp;
	for (int k=0;k<m1.size();k++)
	{
		m1.get(k,keyTemp,valueTemp);
		temp.insert(keyTemp,valueTemp);
	}
	for (int z=0;z<m2.size();z++)
	{
		m2.get(z,keyTemp,valueTemp);
		if (temp.contains(keyTemp))
			temp.erase(keyTemp);
	}
	while (result.size() != 0)
	{
		result.get(0,keyTemp,valueTemp);
		result.erase(keyTemp);
	}
	for (int u=0;u<temp.size();u++)
	{
		temp.get(u,keyTemp,valueTemp);
		result.insertOrUpdate(keyTemp,valueTemp);
	}
}
```
And this is how i tested my program
```
#include "Map.h"
#include <cassert>
#include <iostream>
int main()
{
	Map h;
	assert(h.empty());	
	assert(h.insert("David",3.54));
	assert(!h.empty());
	assert(h.erase("David"));
	assert(h.empty());
	assert(h.insert("Ortiz",0.034));
	assert(h.insert("Danny",4.35));
	assert(!h.insert("Danny",2.23));
	assert(h.update("Danny",5.33));
	assert(!h.update("Jake",1.45));
	assert(h.size() == 2);
	assert(h.insertOrUpdate("Sebastian",6.54));
	assert(h.insertOrUpdate("David", 7.65));
	assert(h.erase("Sebastian"));
	assert(!h.erase("No one"));
	assert(h.contains("Ortiz"));
	assert(!h.contains("Zheng"));
	ValueType value;
	KeyType key;
	assert(h.get("David", value) && value == 7.65);
	assert(!h.get("Martinez", value));
	assert(h.get(0,key,value) && (key == "David" || key == "Danny" || key == "Ortiz"));
	assert(!h.get(100,key,value));
	assert(h.get(2,key,value) && (value == 7.65 || value == 0.034 || value == 5.33));
	Map s;
	assert(s.insert("David",7.65));
	assert(s.insert("Hello",9.54));
	h.swap(s);
	Map z;
	Map t;
	assert(z.insert("David",543));
	assert(z.insert("re",32));
	assert(combine(h,s,z));
	assert(combine(h,t,s));
	Map r (z);
	r.dump();
	Map y (t);
	Map u;
	u=r;
	subtract(h,r,z);
}
```

---

### Post by Zugzwang on 2012-01-31
Please copy and paste the precise error message and the command used for compilation here.

---

### Post by ldkz2524 on 2012-01-31
[dongkeun@lnxsrv04 ~/Project2.CS32]$ g++ -o main *.cpp
[dongkeun@lnxsrv04 ~/Project2.CS32]$ ./main
Hello
9.54
Danny
5.33
Ortiz
0.034
re
32
David
7.65
*******
mudflap violation 1 (check/write): time=1328012021.522124 ptr=0x12a9e1f0 size=32
pc=0x2aad4495ac71 location=`Map.cpp:155:25 (Map::erase)'
      /usr/local/cs/lib64/libmudflap.so.0(__mf_check+0x41) [0x2aad4495ac71]
      ./main(_ZN3Map5eraseERKSs+0x342) [0x404bd8]
      ./main(_ZN3MapD2Ev+0x8f) [0x402ea9]
Nearby object 1: checked region begins 672B before and ends 641B before
mudflap object 0x12a9e4e0: name=`malloc region'
bounds=[0x12a9e490,0x12a9e4ad] size=30 area=heap check=0r/0w liveness=0
alloc time=1328012021.517365 pc=0x2aad4495a101
      /usr/local/cs/lib64/libmudflap.so.0(__mf_register+0x41) [0x2aad4495a101]
      /usr/local/cs/lib64/libmudflap.so.0(__wrap_malloc+0xe2) [0x2aad4495b0a2]
      /usr/local/cs/lib64/libstdc++.so.6(_Znwm+0x1d) [0x2aad44db4c9d]
      /usr/local/cs/lib64/libstdc++.so.6(_ZNSs4_Rep9_S_createEmmRKSaIcE+0x59) [0x2aad44d9d869]
Nearby object 2: checked region begins 0B into and ends 31B into
mudflap dead object 0x12a9e240: name=`malloc region'
bounds=[0x12a9e1f0,0x12a9e20f] size=32 area=heap check=0r/1w liveness=1
alloc time=1328012021.517294 pc=0x2aad4495a101
      /usr/local/cs/lib64/libmudflap.so.0(__mf_register+0x41) [0x2aad4495a101]
      /usr/local/cs/lib64/libmudflap.so.0(__wrap_malloc+0xe2) [0x2aad4495b0a2]
      /usr/local/cs/lib64/libstdc++.so.6(_Znwm+0x1d) [0x2aad44db4c9d]
      ./main(_ZN3MapC2Ev+0x120) [0x401944]
dealloc time=1328012021.522094 pc=0x2aad44959cb6
      /usr/local/cs/lib64/libmudflap.so.0(__mf_unregister+0x36) [0x2aad44959cb6]
      /usr/local/cs/lib64/libmudflap.so.0(__wrap_free+0x98) [0x2aad4495b668]
      ./main(_ZN3MapD2Ev+0x19b) [0x402fb5]
      ./main(main+0x155d) [0x4078e5]
number of nearby objects: 2

This is the error message i got after compiling as shown on the first line  and executing as shown on the second line

---

### Post by Zugzwang on 2012-01-31
Ok, first of all one thing: you wrote that you are getting a mudflap violation in g++, but you actually get it when running the program - avoid mixing the compilation/linking and running phases, as people will guess the cause of compilation errors rather than runtime errors here, giving you meaningless answers.

Having said that, you should try to debug your program and simply let it run until it crashes. Then, you can inspect the cause of the crash.

Another possibility is to run valgrind on your program. Install the valgrind package in Ubuntu. Then, you can run "valgrind --tool=memcheck ./main" to track illegal memory usages in your program. This often gives you a good idea of what went wrong.

In both cases, re-compile your program with debug symbols. For this, run "g++ -g -o main *.cpp".

Finally, I've noted that the "mudflap" libraries are installed into "/usr/local" - What happens if you run your program without these getting loaded?

---

