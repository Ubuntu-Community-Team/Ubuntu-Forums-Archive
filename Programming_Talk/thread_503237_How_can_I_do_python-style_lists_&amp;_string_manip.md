---
title: "How can I do python-style lists &amp; string manipulation in c++?"
date: 2007-07-17
forum: Programming Talk
---

### Post by Torajima on 2007-07-17
I'm currently learning c++, but I'm having a hard time doing anything interesting as I can't figure out how to create python-style lists (and I use lists a lot).

Arrays don't cut it, as they can't be resized, and my class pretty much skipped over vectors.

Basically, I need to be able to do the same sort of stuff you can do in python... easily add/remove items from a list (dynamic resizing), convert a text string to a list based on a delimiter, replace words in a string or list, search for a text string in a list and return index number if found, set one list to the contents of another, etc.

Can this be done in c++ without having to create my own LIST class?

---

### Post by rjfioravanti on 2007-07-17
good luck!  welcome to c++...

check out std::vector, std::list

Sounds like you want 
std::vector<std::string> stringList;

kind of thing

You probably will have to write much of the functionality you were talking about yourself

---

### Post by Jessehk on 2007-07-17
Like the previous poster mentioned, look into std::vector and the related classes in the STL.

Also, make sure to look at the various pre-written algorithms in <algorithm>.
I find this site is a great reference: [http://www.cppreference.com/](http://www.cppreference.com/)
:)

---

### Post by Torajima on 2007-07-17
Thanks, I'll check those links.

Do you have to use iterators with vectors and lists, or can most stuff be done with indexes?

---

### Post by Jessehk on 2007-07-17
> **Torajima said:**
> Thanks, I'll check those links.

Do you have to use iterators with vectors and lists, or can most stuff be done with indexes?

For your own programs, you *can* use indexes, although it is better practise to use iterators. For the algorithms in <algorithm>, iterators are required.

It is not difficult though. Here's an example:

```

#include <vector>
#include <algorithm>
#include <iostream>

// Just a helper function to
// display a vector. Ignore the implementation.
template <typename T>
void displayVector( const std::vector<T> &vec ) {
    typename std::vector<T>::const_iterator iter;
    
    for ( iter = vec.begin(); iter != vec.end(); iter++ )
        std::cout << *iter << " ";
    
    std::cout << std::endl;
}

int main() {
    // create a vector of int's
    std::vector<int> numbs;
    
    // Add a few in random order...
    numbs.push_back( 3 );
    numbs.push_back( -2 );
    numbs.push_back( 8 );
    numbs.push_back( 5 );
    
    displayVector( numbs );
    
    // sort the vector...
    std::sort( numbs.begin(), numbs.end() );
    
    displayVector( numbs );
}

```

---

### Post by hod139 on 2007-07-18
Here are two answers to your question: "convert a text string to a list based on a delimiter."  There are two solutions, write your own [tokenizer]("http://www.hispafuentes.com/hf-doc/HOWTOs/C++Programming-HOWTO-html/C++Programming-HOWTO-7.html") or use [boost's tokenizer class]("http://www.boost.org/libs/tokenizer/tokenizer.htm").

---

