---
title: "C++ help"
date: 2010-05-07
forum: Programming Talk
---

### Post by tauman5263 on 2010-05-07
I have to implement a hash table to store strings into a list of some sort. So far I got a basic implementation, but I get a segmentation fault when I try to run it.

Here are the files:

main.cpp
```

#include "hash.h"
#include <iostream>

using namespace std;

int main() {
        HashTable htab(15);
        htab.insert("blah");
        htab.search("blah");
        htab.search("bdfj");
        return 0;
}
```hash.cpp
```

#include "hash.h"
#include <iostream>
#include <string>
#include <vector>

using namespace std;

HashTable :: HashTable(int size)
{
    vector<string> table(size);
    current_size = 0;
    table_size = size;
}

void HashTable :: insert(const string & word)
{
    int hash_value = hash(word);
    table[hash_value] = word;
    return;
}

int HashTable :: hash(const string & word)
{
    int hash_value = 0, i;
    char first, last;
    first = word[0];
    last = word[word.length()];
    hash_value = ((int)(first) + (int)(last)) % 23;
    return hash_value;
}

bool HashTable :: search(const string & word)
{
    char first = word[0],
         last = word[word.length()];
    int hash_value = ((int)(first) + (int)(last)) % 23;
    if (word == table[hash_value])
    {
        cout << "yes" << endl;
        return true;
    }
    else
    {
        cout << "no" << endl;
        return false;
    }
}

```hash.h
```

#include <iostream>
#include <string>
#include <vector>

using namespace std;

class HashTable
{
    public:
        HashTable(int size);
        void insert(const string & word);
        bool search(const string & word);
    private:
        vector<string> table;
        int current_size;
        int table_size;
        int hash(const string & key);
};

```Can someone help me pinpoint where my mistake is?

---

### Post by Portmanteaufu on 2010-05-07
Often the easiest way to pinpoint the location/cause of a segmentation fault is to examine the core file that gets dumped. First, enable debugging on your program by using the '-g' flag when you compile.

```
g++ **-g** myprogram.cpp -o myprogram
```

Run:
```
ulimit -c unlimited
```
to permit core files, then re-run your newly compiled program so it can crash. This will produce some file with a name like 'core' or 'core####'. Once you have a core file, run:
```
gdb program_name core_file_name
```
Once it starts up, type:
```
where
```
It will tell you exactly what line the program was on when it crashed. In my experience, a segmentation fault is most frequently caused by trying to use a variable which isn't valid -- a pointer which is NULL, for instance. Look at all the variables on the line in question and make sure that they're valid.

Hope that helps!

---

### Post by gnometorule on 2010-05-07
You allocate a 15 dimensional table, and address it using your hash value. Your hash value is calculated modulo 23, aka, will be in the range 0-22. You can easily see segmentation errors then. Make your table of size 23 and you're probably good (read your code carefully though; there seemed to be stray letters).

Edit: also, at the minimum, use static_cast<int> instead of (int).

---

### Post by gmargo on 2010-05-07
There are several problems in your code, but the immediate one causing the segmentation violation is this: you never initialize the table vector in the class data.

Change the constructor to this:
```

HashTable :: HashTable(int size)
{
    // vector<string> table(size);
    table.resize(size);
    current_size = 0;
    table_size = size;
}

```

---

### Post by tauman5263 on 2010-05-07
Thanks everyone for your help so far!

I changed the constructor which fixed the problem for the most part. I also changed the vector size to 23.

I'll post back if I run into any more problems.

---

### Post by MadCow108 on 2010-05-07
small addition to the gdb post.

you can also run the program directly in gdb and not necessarily have to let it core dump

gdb program
run arguments
//wait for crash
backtrace
frame number-of-frame-of-interest

also you can use breakpoints and step through the code instruction by instruction

---

### Post by alys666 on 2010-05-07
> I changed the constructor which fixed the problem for the most part. I  also changed the vector size to 23.
you must not change the size to 23, but must take modulo to the size of hash table.
so in constructor you must store in your object the number of entries of your table, passed as constructir parameter, and make modulo by this value in hash calculation.

---

### Post by dwhitney67 on 2010-05-07
Where the following statement appears in the code, you have a bug:
```

last = word[word.length()];

```
It should appear as:
```

last = word[word.length() - 1];

```
For example, the word "hello" has a length of 5, yet each character of the string is referenced using values 0 through 4.

---

### Post by dribeas on 2010-05-07
In fact the constructor should use the initialization list:

```

HashTable::HashTable( int size )
   :   table(size), current_size(0), table_size(size)
{} 

```

The difference is that the objects are constructed with their final value, instead of being 'default constructed' and then assigned/modified.

Both insert and search should use the same function to calculate the hash (a call to 'hash'), so that it guarantees that changes in the algorithm are used in both cases (and the correction that dwhitney67 points out can be applied in a single place).

---

### Post by tauman5263 on 2010-05-08
Ok, I'm running into trouble adding collision handling.

The problem is definitely in the collision method. I changed the vector to be filled with an impossible value (as suggested by my professor) so that I can just check if vector element has a word in it using a string compare. 

When I run the code, it will handle collisions sometimes, but at other it just hangs, doing nothing.


main.cpp
```

#include "hash.h"
#include <iostream>

using namespace std;

int main() {
        HashTable htab(23);
        htab.display();
        string word;
        int i = 0;
        do {
            cout << "Enter a string: ";
            cin >> word;

            htab.insert(word);
            i++;
        } while (i<15);
        htab.display();
        return 0;
}

```

hash.h
```

#include <iostream>
#include <string>
#include <vector>

using namespace std;

class HashTable
{
    public:
        HashTable(int size);
        void insert(const string & word);
        bool search(const string & word);
        void display(void);
    private:
        vector<string> table;
        int current_size;
        int table_size;
        int collision_range;
        int hash(const string & key);
        int collision(int hash_value, const string & word);
};


```hash.cpp
```

#include "hash.h"
#include <iostream>
#include <string>
#include <cstring>
#include <vector>

using namespace std;

HashTable :: HashTable(int size)
{
    int i;
    table.resize(size);
    for (i=0; i<size; i++)
    {
        table[i] = "###";
    }
    current_size = 0;
    table_size = size;
    collision_range = 0;
}

void HashTable :: insert(const string & word)
{
    int hash_value = hash(word);
    int value;
    if (!table[hash_value].compare("###"))
    {
        table[hash_value] = word;
    }
    else
    {
        collision_range = collision(hash_value, word);
        hash_value += collision_range;
        value = 0;
        if (hash_value > 23)
        {
            value = collision(value, word);
        }
        table[hash_value] = word;
    }
    display();
    return;
}

int HashTable :: hash(const string & word)
{
    int hash_value = 0;
    char first, last;
    first = word[0];
    last = word[word.length() - 1];
    cout << "ascii first: " << static_cast<int>(first) << endl;
    cout << "ascii last: " << static_cast<int>(last) << endl;
    hash_value = (static_cast<int>(first) + static_cast<int>(last)) % 23;
    return hash_value;
}

bool HashTable :: search(const string & word)
{
    char first = word[0],
         last = word[word.length()];
    int hash_value = (static_cast<int>(first) + static_cast<int>(last)) % 23;
    if (word == table[hash_value])
    {
        cout << word << " Found" << endl;
        return true;
    }
    else
    {
        cout << word << " Not Found" << endl;
        return false;
    }
}

void HashTable :: display()
{
    int i;
    for (i=0; i<(table.capacity()); i++)
    {
//        if (table[i].compare("###"))
//        {
            cout << table[i] << " ";
//        }
    }
    cout << endl;
}

int HashTable :: collision(int hash_value, const string & word)
{
    int collision = collision_range;
    hash_value++;
    while (table[hash_value].compare("###"));
    {
        cout << "GOT HERE" << endl;
        hash_value++;
        collision++;
    }

    if (collision > collision_range)
    {
        collision_range = collision;
    }
    return (collision);

}

```

---

### Post by vtnerd on 2010-05-08
Honestly this program has several bugs in, and there are several ways that it could potentially go wrong. You need to think clearly what problem each component (method) is solving. Currently it is difficult for me to determine that. Basically it breaks down like this:

[LIST]
[*]Your search function shouldn't crash, but is not actually linear probing
[*]It is completely unclear what the function collision is doing, but it needs re-thinking
[*]There is a bug in your first if statement in the insert function
[*]There may be multiple bugs in your insert, but its hard to say because of the call to collision
[*]Collision has several range check issues, and is accessing an un-itialized variable (collision range) the first time you try to insert something. It gets slightly more confusing since you re-use that member variable several times, most likely unintentionally (definitely incorrectly).
[/LIST]
    
Debug this (using gdb, or Visual Studio), or [valgrind ]("http://en.wikipedia.org/wiki/Valgrind")this.  Those are my suggestions. Either one will begin to shed light onto your  problem, and ultimately you will be better off long term for doing so.

---

### Post by tauman5263 on 2010-05-08
Ok, here's what the methods are supposed to do:

insert: inserts an item to the hash table. Uses the hash method to determine where to insert and the collision method in the event that there is already a word in that place.

hash: calculates hash function.

search: searches the hash table for a word.

display: displays all of the hash table elements.

By the way, I did edit my last post if you didn't notice. My program has changed a bit since before the edit.

---

### Post by dwhitney67 on 2010-05-09
Check your array (vector) boundaries; you have a problem there.  Namely in collision().

Suppose your hash_value is 22; after you increment it by 1, your app will crap out when it attempts to access slot 23 of the vector, which does not exist.  Remember, the vector has size of 23; thus it is indexed from 0 through 22.  Even if hash_value is smaller than 22, with the while-loop, you are asking for trouble.

Btw, in your code, where you have a hard-coded 23, replace that with your vector size(), or with table_size (which btw, is superfluous).

Also, for better coding style, remove the "using namespace std" from the header file, and also remove unnecessary include files (ie iostream) from the same header file.

---

