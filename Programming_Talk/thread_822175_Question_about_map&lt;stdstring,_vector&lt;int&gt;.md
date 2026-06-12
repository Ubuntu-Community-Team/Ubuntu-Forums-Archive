---
title: "Question about map&lt;std::string, vector&lt;int&gt; &gt;"
date: 2008-06-08
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-06-08
I want to have a map which maps strings of vector<int>.  Is there anything wrong with the code below?  In other words, am I correct in assuming that when elements are stored in a map, both the key and the valued are copied as opposed to just having the pointers copied?

[PHP]
#include <iostream>
#include <map>
#include <vector>
#include <iostream>
using namespace std;

map<std::string, vector<int> > amap;
vector<int> intvector;
map<std::string, vector<int> >::iterator it;

void find(std::string str)
{
	it = amap.find(str);
	vector<int> intvec = it->second;
	for(int i = 0; i < intvec.size(); i++)
	{
    	cout << intvec[i] << "\t";
    }
    cout << endl;
}

void insert(std::string str, int number)
{
	vector<int> numvector;
	numvector.push_back(number);
	amap[str] = numvector;
}

int main ()
{
	insert("one", 1);
	insert("two", 2);
	insert("three", 3);
	amap["three"].push_back(3);
	amap["three"].push_back(3);
	
	find("one");
	find("two");
	find("three");
	
	return 0;
}
[/PHP]

OUTPUT:
[PHP]
1
2
3       3       3
[/PHP]

---

### Post by JupiterV2 on 2008-06-08
It doesn't look too bad but at quick glance I've noticed the following things:

1) You've included <iostream> twice.

2) Drop 'using namespace std' and just use 'std::map' etc. It makes it clearer for others using your work that the functions or data types you're using belong to the std namespace. It's never a good idea to mix both usages together.

3) This is a personal thing with me but I hate poluting the global space with variables and function when I don't have to. Instead, I think its better to take advantage of C++'s ability to polymorph classes. Example:

[PHP]#include <iostream>
#include <map>
#include <vector>

class MyMap: public std::map<std::string, std::vector<int> >
{
  public:
  	MyMap() {}
  	~MyMap() {};
  	
	void find(std::string str)
	{
		std::map<std::string, std::vector<int> >::iterator it;
		
    	it = std::map<std::string, std::vector<int> >::find(str);
    	std::vector<int> intvec = it->second;
    	
    	    for(int i = 0; i < intvec.size(); i++)
    	    {
    	        std::cout << intvec[i] << "\t";
    	    }
    	    std::cout << std::endl;
	}

	void insert(std::string str, int number)
	{
    	std::vector<int> numvector;
    	numvector.push_back(number);
    	std::map<std::string, std::vector<int> >::insert( 
    		std::make_pair(str, numvector) );
	}
};

int main ()
{
	MyMap amap;
    amap.insert("one", 1);
    amap.insert("two", 2);
    amap.insert("three", 3);
    amap["three"].push_back(3);
    amap["three"].push_back(3);
    
    amap.find("one");
    amap.find("two");
    amap.find("three");
    
    return 0;
}[/PHP]

This isn't exactly how I would do this myself but I wanted to take the code you wrote and modify it to work in the way I described.

Irregardless if just the pointers (I assume you mean memory addresses?) of the variables or the values themselves are retained the data is all 'local' in scope. So, in the above example the data won't get lost because the local variables have been reclaimed. [PHP][/PHP]However, if you are wanting the mapping to have global scope, either use new/delete and assign a pointer to the data or pass by reference:

[PHP]
void somefun(std::map<int, int>& map)
{
/* do some stuff with the map */
...
}

int main()
{
  map<int, int> mymap;

  somefun(mymap);

  return 0;
}[/PHP]

---

### Post by SNYP40A1 on 2008-06-08
> **JupiterV2 said:**
> It doesn't look too bad but at quick glance I've noticed the following things:

1) You've included <iostream> twice.

2) Drop 'using namespace std' and just use 'std::map' etc. It makes it clearer for others using your work that the functions or data types you're using belong to the std namespace. It's never a good idea to mix both usages together.

3) This is a personal thing with me but I hate poluting the global space with variables and function when I don't have to. Instead, I think its better to take advantage of C++'s ability to polymorph classes. Example:

[PHP]#include <iostream>
#include <map>
#include <vector>

class MyMap: public std::map<std::string, std::vector<int> >
{
  public:
  	MyMap() {}
  	~MyMap() {};
  	
	void find(std::string str)
	{
		std::map<std::string, std::vector<int> >::iterator it;
		
    	it = std::map<std::string, std::vector<int> >::find(str);
    	std::vector<int> intvec = it->second;
    	
    	    for(int i = 0; i < intvec.size(); i++)
    	    {
    	        std::cout << intvec[i] << "\t";
    	    }
    	    std::cout << std::endl;
	}

	void insert(std::string str, int number)
	{
    	std::vector<int> numvector;
    	numvector.push_back(number);
    	std::map<std::string, std::vector<int> >::insert( 
    		std::make_pair(str, numvector) );
	}
};

int main ()
{
	MyMap amap;
    amap.insert("one", 1);
    amap.insert("two", 2);
    amap.insert("three", 3);
    amap["three"].push_back(3);
    amap["three"].push_back(3);
    
    amap.find("one");
    amap.find("two");
    amap.find("three");
    
    return 0;
}[/PHP]

This isn't exactly how I would do this myself but I wanted to take the code you wrote and modify it to work in the way I described.

Irregardless if just the pointers (I assume you mean memory addresses?) of the variables or the values themselves are retained the data is all 'local' in scope. So, in the above example the data won't get lost because the local variables have been reclaimed. [PHP][/PHP]However, if you are wanting the mapping to have global scope, either use new/delete and assign a pointer to the data or pass by reference:

[PHP]
void somefun(std::map<int, int>& map)
{
/* do some stuff with the map */
...
}

int main()
{
  map<int, int> mymap;

  somefun(mymap);

  return 0;
}[/PHP]

I appreciate your response and I agree that global variables should be avoided.  I only used them in the example above because they were quicker than passing variables around.  Anyway, I was confusing C++ and Java.  In C++, I can declare a vector (compile time - on the stack, not the heap) and then put things in it.  Then I can throw it in a map, like this:

map<string, vector<int> > mymap;
vector<int> myintvec;

myintvec.push_back(3);
myintvec.push_back(2);
mymap["tree"] = myintvec;

Then a copy of myintvec is placed in the map -- the map does not just store a pointer to myintvec as would be the case in Java where everything is declared on the heap (outside the primitive types).  What happens is that C++ creates an empty vector and then calls the copy constructor on myintvec to copy the contents of myintvec into the copy which is the placed in the map.  In other words, although myintvec will be popped off the stack once the function exits, the copy in mymap will remain because it was declared in global scope and is still on the stack.  Correct me if any of this was wrong.

---

