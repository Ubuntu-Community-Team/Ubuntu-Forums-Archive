---
title: "C++ String Matching"
date: 2008-09-13
forum: Programming Talk
---

### Post by nickbird on 2008-09-13
Hello,

I'm trying to read data into an array, here's my problem:
the data contains redundancies, the same thing may appear more then once,
so the file would look like this;
```

A 7
B 3
C 2
A 4
A 5
A 6
B 7
C 4
D 2
A 3
B 1

```
In the above file, there are 11 lines, but only 4 different items, A, B,C,D.  I've been fighting for close to two hours now to try to figure out a way to get those 11 lines to fit into 4 item array.

Lets say i need to add these items and have a total for A, B, C, D, my program keeps thinking that the five different A's are different items, but they are not!

If that made sense any feed back would be appreciated, my brains are pretty scrambled right now...

---

### Post by Sockerdrickan on 2008-09-13
is it a vector?

---

### Post by lian1238 on 2008-09-13
It would help us help you if you posted the file as well.
Anyway, I think I get what you mean.
So, the final result would be A=7+4+5+6+3=25, etc. right?
I assume you're using array of type int.
```
int result[4] = {0}; // initialize to 0
```
So when you read the contents, you need to add them into your array.

---

### Post by Sockerdrickan on 2008-09-13
I wrote this it might help.

[php]#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<string> letters;

    //Here goes your loading code
    letters.push_back("A");
    letters.push_back("A");
    letters.push_back("C");
    letters.push_back("D");
    letters.push_back("D");
    letters.push_back("B");
    letters.push_back("A");

    //Sort just for a better view in this example
    sort(letters.begin(),letters.end());

    //Before...
    for(size_t i=0; i<letters.size(); i++)
        cout<<letters[i]<<endl;

    //Only unique should be in there!
    letters.resize(unique(letters.begin(),letters.end())-letters.begin());

    cout<<endl<<"Fixed"<<endl;

    //...After
    for(size_t i=0; i<letters.size(); i++)
        cout<<letters[i]<<endl;

    return 0;
}[/php]

---

### Post by dribeas on 2008-09-13
> **nickbird said:**
> In the above file, there are 11 lines, but only 4 different items, A, B,C,D.  I've been fighting for close to two hours now to try to figure out a way to get those 11 lines to fit into 4 item array.


Do you really want to use an array/vector for it? Seems as if a map was more apt for the task:

```

#include <iostream>
#include <string>
#include <map>
int main()
{
   std::map< std::string, int > data;
   std::string key;
   int value;
   while ( cin >> key >> value )
   {
      data[ key ] += value;
   }
   // map contains pairs like A->27, B->...
   for ( std::map< std::string, int >::const_iterator it = data.begin();
      it != data.end(); ++it )
   {
      std::cout << it->first << ": " << it->second << std::endl;
   }
}

```

First time you call operator[] on a map for a given key, a default constructed element is returned, which for int is 0, so you don't have to initialize beforehand.

---

