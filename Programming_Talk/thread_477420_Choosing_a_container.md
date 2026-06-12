---
title: "Choosing a container"
date: 2007-06-18
forum: Programming Talk
---

### Post by [h2o] on 2007-06-18
I have a list of elements that each contain a list of integers:
class Element
{
  vector<int> int_list;
}

vector<Element> elements;

I need to loop through each elements int_list and count how many times each int occurs within the elements list.

Example:
elements contains three Element objects that have the int_lists:
[1 2 3 4], [2 6 9] and [1 2]

Later I must be able to query to find out how many 1's or 2's there are present within the elements list (in this case 2 and 3 times respectivly)

My implementation in C++ is using std::map<int,int> to map each int in int_list to a number referring to it's number of occurences.

However... when I run the program it is incredibly slow, and profiling shows that most of the time used goes to find() and insert()-calls to create the map. Since speed is of the utmost essence I need to speed this up.

Am I using the wrong type of container altogether or is it just std::map that sucks? Are there any good alternatives?

I need to both insert and extract values quickly, but I think inserting is the bottle-neck so the faster inserts the better.

---

### Post by WW on 2007-06-18
Can you determine in advance the minimum and maximum values of the integers in your lists?  If so, and if they aren't too huge, you could use an integer array instead of a map.

---

### Post by [h2o] on 2007-06-18
> **WW said:**
> Can you determine in advance the minimum and maximum values of the integers in your lists?  If so, and if they aren't too huge, you could use an integer array instead of a map.

I thought about this and I could probably do that. The array will be over a million units long, but then that is only a few MB, and I can afford that (since memory is not a constraining factor, CPU is).

If I use memcpy to clear it between passes (I do the calculations a lot of times) I guess it would be pretty quick. Or atleast a lot faster than std::map.

---

### Post by hod139 on 2007-06-18
Why don't you use a hash_map inside the element class.  Something like:
```

class Element
{
hash_map<int, int> int_hash;
};

```Where the first int is the number, and the second int is the occurrence of that number.   You also should not use a vector, unless you really need the random access, and consider making the container contain pointers to the Elements.

Actually, I got a little excited about this and actually wrote an entire implementation

```

#include <ext/hash_map>
#include <list>
#include <iostream>

class Element
{
public:
  /**
   * Inserts the key into the table, or increments the value if already exists
   * This is tricky, the [] operator will insert the key into 
   * the hash_map if it does not exist, with the default value of 0
   * which subsequently gets incremented to 1.  If the key is in the table,
   * it is simply incremented
   */
  void insert(int key){
      int_hash[key] += 1; 
  }

  /**
   * In order to keep this method const, I cannot use the [] operator
   * This method first makes sure the element exists, then returns the 
   * value (count) else, returns 0
   */
  int numberOf(int key) const{
    mapType::const_iterator itr;
     itr = int_hash.find(key);
    if(itr == int_hash.end()){
         return 0;
    }
    else 
      return (*itr).second;
  }

private:
  __gnu_cxx::hash_map<int, int> int_hash; // the hash table
  typedef __gnu_cxx::hash_map< int, int > mapType; // iterator type
};

/**
 * The count method.  
 * Linear cost to traverse all the elements of the vector, 
 * but the cost of each numberOf() function call is constant,
 * so the total time is O(N), where N is the number of elements
 */
int count(const std::list<Element*> &elements, int num){
  std::list<Element*>::const_iterator itr;
  int count = 0;
  for(itr = elements.begin(); itr != elements.end(); ++itr){
     const Element* const &e = *itr;
      count += e->numberOf(num);
  }
  return count;
}

/**
 * Main entry point
 */
int main(){

  // Create 3 Elements
  Element e1, e2, e3;
  e1.insert(1);
  e1.insert(2);
  e1.insert(3);
  e1.insert(4); 
  e2.insert(2);
  e2.insert(6);
  e2.insert(9);
  e3.insert(1);
  e3.insert(2);
   
  // Create the elements vector, and add the Elements
  std::list<Element*> elements;
  elements.push_back(&e1);
  elements.push_back(&e2);
  elements.push_back(&e3);

  // Count the number of 1s
  std::cout << "There are " << count(elements, 1) << " ones " << std::endl;
  
  // Count the number of 2s
  std::cout << "There are " << count(elements, 2) << " twos " << std::endl;

  return 0;
}

```

Let me know if it runs any faster!

---

### Post by the_unforgiven on 2007-06-19
> **hod139 said:**
> Why don't you use a hash_map inside the element class.  Something like:
```

class Element
{
hash_map<int, int> int_hash;
};

```Where the first int is the number, and the second int is the occurrence of that number.   You also should not use a vector, unless you really need the random access, and consider making the container contain pointers to the Elements.

Actually, I got a little excited about this and actually wrote an entire implementation

```

#include <ext/hash_map>
#include <list>
#include <iostream>

class Element
{
public:
  /**
   * Inserts the key into the table, or increments the value if already exists
   * This is tricky, the [] operator will insert the key into 
   * the hash_map if it does not exist, with the default value of 0
   * which subsequently gets incremented to 1.  If the key is in the table,
   * it is simply incremented
   */
  void insert(int key){
      int_hash[key] += 1; 
  }

  /**
   * In order to keep this method const, I cannot use the [] operator
   * This method first makes sure the element exists, then returns the 
   * value (count) else, returns 0
   */
  int numberOf(int key) const{
    mapType::const_iterator itr;
     itr = int_hash.find(key);
    if(itr == int_hash.end()){
         return 0;
    }
    else 
      return (*itr).second;
  }

private:
  __gnu_cxx::hash_map<int, int> int_hash; // the hash table
  typedef __gnu_cxx::hash_map< int, int > mapType; // iterator type
};

/**
 * The count method.  
 * Linear cost to traverse all the elements of the vector, 
 * but the cost of each numberOf() function call is constant,
 * so the total time is O(N), where N is the number of elements
 */
int count(const std::list<Element*> &elements, int num){
  std::list<Element*>::const_iterator itr;
  int count = 0;
  for(itr = elements.begin(); itr != elements.end(); ++itr){
     const Element* const &e = *itr;
      count += e->numberOf(num);
  }
  return count;
}

/**
 * Main entry point
 */
int main(){

  // Create 3 Elements
  Element e1, e2, e3;
  e1.insert(1);
  e1.insert(2);
  e1.insert(3);
  e1.insert(4); 
  e2.insert(2);
  e2.insert(6);
  e2.insert(9);
  e3.insert(1);
  e3.insert(2);
   
  // Create the elements vector, and add the Elements
  std::list<Element*> elements;
  elements.push_back(&e1);
  elements.push_back(&e2);
  elements.push_back(&e3);

  // Count the number of 1s
  std::cout << "There are " << count(elements, 1) << " ones " << std::endl;
  
  // Count the number of 2s
  std::cout << "There are " << count(elements, 2) << " twos " << std::endl;

  return 0;
}

```

Let me know if it runs any faster!
Even a normal std::map should be sufficient.
I just changed the __gnu_cxx::hash_map to std::map in your code above and it is still working. ;)
hash_map (hash table) makes more sense with really large data set.
For more information on hash tables, check out:
[http://en.wikipedia.org/wiki/Hash_table](http://en.wikipedia.org/wiki/Hash_table)

HTH ;)

---

### Post by [h2o] on 2007-06-19
Changing the std::map to __gnu_cxx::hash_map took care of all my problems. Thanks a lot!

---

