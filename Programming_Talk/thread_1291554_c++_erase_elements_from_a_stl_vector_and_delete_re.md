---
title: "c++: erase elements from a stl vector and delete removed objects"
date: 2009-10-14
forum: Programming Talk
---

### Post by diamantis13 on 2009-10-14
Hi, 
I have a vector of objects and I would like to remove some of its elements. I am using the vector container from the Standard Template Library and not something else because in my program I very rarely have to erase entries from the vector. Most of the time I push back entries or linearly access the vector with an iterator.
The following example uses too much memory, probably because the objects erased from the vector are not deleted. If I had a vector of pointers to objects I could use [FONT="Courier New"]delete[/FONT] but what can I do now???

```

#include <iostream>
#include <vector>
#include <iterator>
using namespace std;
class obj{ /just an object
public:
  void setId( int x ){ id = x; }
  int getId( void ){ return id; }
private:
  int id;
  double a[1000]; //just taking up space in memory in order to make the problem more obvious
};
int main(int argc, char* argv[]){
  vector<obj> v; //make a vector of objects
  for(int i =0; i<100000; i++){ 
    obj one; // start filling the vector
    one.setId(i);
    obj two;
    two.setId(2);
    obj three;
    three.setId(3);
    v.push_back(one);
    v.push_back(three);
    v.push_back(two);
    //delete some
    for (vector<obj>::iterator it = v.begin();     
	 it != v.end();){
      if((*it).getId()>2){
	v.erase(it);
      }else{
	++it;
      }
    }
  }
}

```

Any ideas??
Thanks!

---

### Post by dwhitney67 on 2009-10-14
Regardless of what container you use, or whether you instantiate an object on the stack or the heap, you are going to use the same amount of memory.

If you are looking to sort out inefficiencies, then consider storing pointers to the 'obj' objects so that you avoid instantiating the object on the stack and then turn around to make a copy for the vector.
```

obj one;            // 8004 bytes on stack
...
v.push_back(one);   // 8004 bytes copied via copy-constructor

```

Anyhow, you may want to consider using a multimap for your container.  Using a combination of the lower_bound() and upper_bound() (of which each returns an iterator), you can erase() items from your container.

P.S.  Note that if you decide to store pointers, then calling erase() will *not* deallocate your object(s).  Consider using tr1 or boost smart pointers.

EDIT...

A basic example:
```

#include <tr1/memory>
#include <map>
#include <iostream>
#include <algorithm>

class Object
{
public:
   Object(int id) : id(id) {}
   void setId(int i)  { id = i; }
   int  getId() const { return id; }

private:
   int    id;
   double array[1000];
};

typedef std::tr1::shared_ptr<Object>  ObjectPtr;
typedef std::multimap<int, ObjectPtr> MultiMap;


void display(const std::pair<int, ObjectPtr>& entry) {
   std::cout << entry.first << " ";
}

int main() {
   using namespace std;

   MultiMap mm;

   for (int i = 0; i < 10; ++i) {
      ObjectPtr one(new Object(i));
      ObjectPtr two(new Object(2));
      ObjectPtr three(new Object(3));

      mm.insert(make_pair(one->getId(), one));
      mm.insert(make_pair(two->getId(), two));
      mm.insert(make_pair(three->getId(), three));
   }

   cout << "Before deleting..." << endl;
   for_each(mm.begin(), mm.end(), display);
   cout << endl;

   // erase all objects with ID == 2
   MultiMap::iterator lo_it = mm.lower_bound(2);
   MultiMap::iterator hi_it = mm.upper_bound(2);

   mm.erase(lo_it, hi_it);

   cout << "After deleting..." << endl;
   for_each(mm.begin(), mm.end(), display);
   cout << endl;
}

```

---

### Post by MadCow108 on 2009-10-15
a vector will not shrink when you erase one of its members. It will move the members behind the erased member one position down (very inefficient!) but keep the same capacity.
you need to shrink the vector explicitly:
Consider this code:
```

	vector<int> test;
	test.push_back(5);
	test.push_back(2);
	test.push_back(7);
	std::cout << test.size() << " " << test.capacity() << std::endl;
	test.erase(test.begin());
	std::cout << test.size() << " " << test.capacity() << std::endl;
	vector<int>(test).swap(test); // shrink-to-fit, may throw bad::alloc from temporary creation
	std::cout << test.size() << " " << test.capacity() << std::endl;

```
output:
3 4
2 4
2 2

as you see the vector still has capacity 4 after the erase.
Only after swapping the content with an temporary vector it has reduced its capacity.

just calling vec.resize(size) will not work because resize does not imply a reallocation if size < vec.capacity()!

---

