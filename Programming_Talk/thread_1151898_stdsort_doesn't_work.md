---
title: "std::sort doesn't work"
date: 2009-05-07
forum: Programming Talk
---

### Post by cl333r on 2009-05-07
Folks can anyone please make this sorting example work? It compiles and runs, but doesn't actually sort the elements from the vector.. I spent a few hours and can't figure out what's the matter..

main.cpp:
```

#include <stdlib.h>
#include <iostream>
#include <vector>
#include <algorithm>
#include "Person.h"

using namespace std;

int main(int argc, char** argv) {

    Person *p1 = new Person( "James" );
    Person *p2 = new Person( "Brian" );
    Person *p3 = new Person( "John" );
    Person *p4 = new Person( "Mark" );

    vector<Person*> v;
    v.push_back(p1);
    v.push_back(p2);
    v.push_back(p3);
    v.push_back(p4);

    std::sort(v.begin(), v.end());

    cout << "Sorted: " << endl;
    
    for( int i=0; i<v.size(); i++) {
	Person *p = v.at(i);
	cout << p->getName() << endl;
    }
    
    return (EXIT_SUCCESS);
}

```

Person.h:
```

#ifndef _PERSON_H
#define	_PERSON_H

#include <iostream>
#include <glibmm.h>
using namespace std;

class Person {
public:
    Person(Glib::ustring);
    virtual ~Person();
    Glib::ustring getName();

    bool operator<(Person* other) {
	cout << "called operator < for" << getName() << endl;
	return other->getName().compare(name) > 0;
    }
protected:
    Glib::ustring name;
};
#endif

```

Person.cpp:
```

#include "Person.h"

Person::Person(Glib::ustring s) {
    name=s;
}

Person::~Person() {}

Glib::ustring Person::getName() {
    return name;
}

```

---

### Post by dwhitney67 on 2009-05-07
Of course it is working!  You are sorting the pointers to the Person object you allocated.

But I bet that is not what you intended... you probably wanted the Person objects to be sorted within the vector by the Person's name attribute.

With your design, define a function like:
```

bool nameSort(const Person* one, const Person* two)
{
  return one->getName().compare(two.getName()) < 0;
}

```
Note, this is not a class method of Person, but a free-floating function.

Then in your main() code:
```

...
std::sort(v.begin, v.end(), nameSort);
...

```

P.S.  The string passed to the constructor should be defined as "const Glib::ustring&", and the getName() method should be defined as "Glib::ustring getName() const".

---

### Post by cl333r on 2009-05-07
Thanks a lot! It works now.
My final classes:

main.cpp:
```

#include <stdlib.h>
#include <iostream>
#include <vector>
#include <algorithm>
#include "Person.h"

using namespace std;

bool nameSort(const Person* one, const Person* two)
{
  return one->getName().compare(two->getName()) < 0;
}

int main(int argc, char** argv) {

    Person *p1 = new Person( "James" );
    Person *p2 = new Person( "Brian" );
    Person *p3 = new Person( "John" );
    Person *p4 = new Person( "Mark" );

    vector<Person*> v;
    v.push_back(p1);
    v.push_back(p2);
    v.push_back(p3);
    v.push_back(p4);

    std::sort(v.begin(), v.end(), nameSort);

    cout << "Sorted: " << endl;
    
    for( int i=0; i<v.size(); i++) {
	Person *p = v.at(i);
	cout << p->getName() << endl;
    }
    
    return (EXIT_SUCCESS);
}

```

Person.h:
```

#ifndef _PERSON_H
#define	_PERSON_H

#include <iostream>
#include <glibmm.h>
using namespace std;

class Person {
public:
    Person(const Glib::ustring& );
    virtual ~Person();
    Glib::ustring getName() const;
protected:
    Glib::ustring name;
};

#endif

```

Person.cpp:
```

#include "Person.h"

Person::Person(const Glib::ustring& s) {
    name=s;
}

Person::~Person() {}

Glib::ustring Person::getName() const {
    return name;
}


```

---

