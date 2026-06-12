---
title: "Dynamic list of items?(C++)"
date: 2008-08-07
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-08-07
It's me again. I am using C++ and I am experimenting with Gtkmm and Gstreamer. But I'll describe my problem in an abstract manner. Let's say you have 2 lists of things(any things-->items). The first list is huge. You use certain criteria to pick specific items and populate the second list. 
My problem is here. I don't know from the begining, the number of items my second list will hold. The number will be different depending on my criteria and the items the first list has. So how can I create a list of items on run-time and know how many it holds?

Clarifications:
1.items->these can be any data type eg int/float/string/GstElement
2.list->I am not refering to some keyword/function/object of C++. To me even an array is list.

I hope you can help...

---

### Post by CptPicard on 2008-08-07
Read up on the STL "vector" and then just push_back() your items as you find them...

---

### Post by cszikszoy on 2008-08-07
You'll have to create a dynamic array using pointers

Look at this program I made to demonstrate:
```

#include <iostream>
 
using namespace std;

int main()
{
    //some variables
    int a[10] = {0,1,2,3,4,5,6,7,8,9};
    int sel;

    //determine the size of our new array
    cout << "How many items do you want?" << endl;
    cin >> sel;
    cout << "Sel = " << sel << endl;

    //allocate memory for our array
    int *b = new int[sel];

    for (int i=0; i<sel; i++)
        b[i] = a[i];

    //now print the array
    for (int i=0; i<sel; i++)
        cout << b[i] << " ";
    cout << endl;

    return(0);
}

```

The output looks like this:
```

chris@chris-laptop:~/Desktop$ g++ ./arraytest.cpp -o a
chris@chris-laptop:~/Desktop$ ./a
How many items do you want?
5
Sel = 5
0 1 2 3 4 

```

---

### Post by Jessehk on 2008-08-07
Certain uses of the STL are easy, but they can easily become complicated.

Here, an IsEven functor provides a predicate for the std::remove_if function which returns an iterator to the new end of the std::vector (it moves the "failing" elements to the end of the container).

```

#include <iostream>
#include <vector>
#include <algorithm>

class IsEven {
public:
    bool operator()( int x ) {
        return !(x & 1);
    }
};

int main() {
    std::vector<int> numbers;

    for ( int i = 0; i != 10; ++i )
        numbers.push_back( i );

    std::vector<int>::iterator iter, end;
    end = std::remove_if( numbers.begin(), numbers.end(), IsEven() );

    // Print the odd numbers from 1-10
    for ( iter = numbers.begin(); iter != end; iter++ )
        std::cout << *iter << std::endl;
}

```

---

### Post by prshah on 2008-08-07
> **SledgeHammer_999 said:**
> Let's say you have 2 lists of things(any things-->items). The first list is huge. You use certain criteria to pick specific items and populate the second list. I don't know from the begining, the number of items my second list will hold.

You're looking for ["linked lists"]("http://www.google.co.in/search?hl=en&q=linked+lists"); [wikipaedia explains it well]("http://en.wikipedia.org/wiki/Linked_list").

---

### Post by cszikszoy on 2008-08-07
Linked lists are a good idea.  More info here: [http://www.yolinux.com/TUTORIALS/LinuxTutorialC++STL.html#LIST](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++STL.html#LIST)

---

### Post by catchmeifyoutry on 2008-08-07
> **SledgeHammer_999 said:**
> 
1.items->these can be any data type eg int/float/string/GstElement


I'm afraid you'll need to use some sort of special structure for your list
that contains info on _what_ your data type is (for example use enum value to identify int = 1, float = 2, string = 3 GstElement = 4, ..., undefined = 0), and also either a pointer or index to refer to the actual int/float/string/GstElement which are stored in extra lists (one for each data type).

Let me try to clarify this a bit.

The point is that if you keep a list of "things" in C++, the compiler needs to know how many bytes each "thing" will take in memory at compile time.
Once an item is in memory, nothing will tell what kind of "thing" it actually is, that's why variables, which refer to stuff in memory, _must_ be defined as a being of a certain datatype/class once (and only once).
So if you want to combine items, then
a) your program needs to track what the item is itself somehow,
and
b) the list of combined items can actually only contain one specific fixed datatype/structure/class.

It follows that the list should be a list containing instances of a structure that identifies what kind of item it is, 
and maintains an index or pointer to find the actual instance in the memory. You could make use of unions (union is part of the C++ language):
[http://www.cplusplus.com/doc/tutorial/other_data_types.html](http://www.cplusplus.com/doc/tutorial/other_data_types.html)
For default data types the value instead of a pointer is probably sufficient.

Pseudo code example:
[PHP]
typedef enum {
  MI_UNDEFINED = 0,
  MI_INT = 1,
  MI_FLOAT = 3,
  ...
} mixed_item_type;

typedef struct  {
  mixed_item_type datatype;
  union {
    int int_value;
    float float_value;
    ...
    GstElement * gst_index;
  }
} mixed_item;

std::vector<mixed_item> my_mixed_list;

// insertion usage
mixed_item item1;
item1.datatype = MI_FLOAT;
item1.float_value = 3.14156;
my_mixed_list.push_back(item1);

mixed_item item2;
item2.datatype = MI_GSTELEMENT;
item2.gst_pointer = new GstElement(/* ... */);
my_mixed_list.push_back(item2);

// retrieval usage
mixed_item item = my_mixed_list.at(1);
assert(item.datatype != MI_UNDEFINED);

switch(item.datatype)
{
   case MI_INT:
     std::cout << item.int_value << std::endl;
     ...
   break;
  
   case MI_GSTELEMENT:
      std::cout << *item.gst_pointer << std::endl;
     ...
   break;

   // etc!
}
[/PHP]

Also, you have already been advised by others here to look up stl::vector and stl::list, but note that there are clear differences between the two.
You should choose which one to use (and you should use STL over your own list implementation if possible) based on their properties.

If you need mostly sequential access (thus, iterate from begin to end) but insert stuff at random points, use a linked list.
If you need mostly to retrieve items in random order, use a vector.
Vectors are basically arrays, but take care of resizing and memory allocation for you (yay!). 
I would suspect that a vector is all you need, but again, google for differences between the two first.

Or does anybody know of a better way?

Hope its clear, success.

---

### Post by SledgeHammer_999 on 2008-08-07
Thank you. I think std::vector is what I need.

@catchmeifyoutry I meant that the list will have one data type(GstElement), I just wanted to say that my 'abstract' example didn't refer to any specific data type at that moment. I won't mix data types(yet :D )

---

### Post by catchmeifyoutry on 2008-08-07
> **SledgeHammer_999 said:**
> Thank you. I think std::vector is what I need.

@catchmeifyoutry I meant that the list will have one data type(GstElement), I just wanted to say that my 'abstract' example didn't refer to any specific data type at that moment. I won't mix data types(yet :D )

ah, right.
thank god. :p

---

### Post by hod139 on 2008-08-07
> **catchmeifyoutry said:**
> I'm afraid you'll need to use some sort of special structure for your list
that contains info on _what_ your data type is (for example use enum value to identify int = 1, float = 2, string = 3 GstElement = 4, ..., undefined = 0), and also either a pointer or index to refer to the actual int/float/string/GstElement which are stored in extra lists (one for each data type).

<snip>

Or does anybody know of a better way?

This solution is very C-ish, here is a "better" (at least more C++) way:
[http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6](http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6)

---

### Post by catchmeifyoutry on 2008-08-08
> **hod139 said:**
> This solution is very C-ish, here is a "better" (at least more C++) way:
[http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6](http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6)

Hmm, yes, but I had understood that he/she wanted built-in data types on the list too. The (better) solution in your link only works for object with a shared base class which has some virtual function to remove the switch.
But the virtual function means the compiler has to add a runtime class identifier to each object too.

But a good compromise is possible: define a MixedItem base class with virtual functions for common behavior, and derive an IntItem class to keep an int, FloatItem for a float, GtkElementItem, ..., etc. (using templates), instances of which can be pushed on a std::vector<MixedItem>.
The template could include a template<tyepname T> T get_as<T>() function to wrap runtime type checking in case specific behavior can't be put in the virtual functions (similar to what is done in boost::program_options).

Now that I'm thinking about it, isn't there some template to do this in the STL, boost?

---

### Post by DavidBell on 2008-08-08
> **catchmeifyoutry said:**
> Hmm, yes, but I had understood that he/she wanted built-in data types on the list too. The 
....
Now that I'm thinking about it, isn't there some template to do this in the STL, boost?

Is there a portable Variant datatype? I know in windows you can do std::list|vector<VARIANT*|CComVariant> but don't know in linux. I see there is boost::variant and boost::any, not sure how they comapre though.

DB

---

### Post by hod139 on 2008-08-08
> **DavidBell said:**
> Is there a portable Variant datatype? I know in windows you can do std::list|vector<VARIANT*|CComVariant> but don't know in linux. I see there is boost::variant and boost::any, not sure how they comapre though.

DB
You have to use boost for a portable any type.  However, C++0x will include new keywords "auto" and "decltype" that will allow automatic deduction of types.  This will come in handy for all those metaprogramming people.

---

