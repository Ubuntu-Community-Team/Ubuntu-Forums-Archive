---
title: "C++ forbids declaration of ‘vector’ with no type"
date: 2007-07-18
forum: Programming Talk
---

### Post by lightnb on 2007-07-18
I'm using KDevelop and getting the error:

> C++ forbids declaration of ‘vector’ with no type


The line in question is:

```
vector<double> MemberDimmers;
```

In the context:

```

#include <vector>

class Selection
{
	public:
	int Add(int ObjectToAdd, int CurrentObjectType); // Adds an object to the selection
	void Remove(); // Removes an object from the selection
	void Clear(); // Empties the selection / selects nothing
	
	Selection(); // Constructor
	~Selection(); // Destructor

	private:
	char SelectionName[81]; // An 80 charector array - Name or Label for the selection
	vector<double> MemberDimmers; // A vector of Dimmers that belong to this (a) group.
	vector<double> MemberMVLs; // A vector of Moving Lights that belong to this (a) group.
	vector<double> MemberAtmospherics; // A vector of Atmospheric Machines that belong to this (a) group.
};

```

I thought the keyword 'double' made it quite clear which type of vector I'm declaring... but the way it puts 'vector' in quotes- Does it think it's a function? How do I tell it that vector means vector?

---

### Post by the_unforgiven on 2007-07-18
It's **std::vector** and not simply vector.
As per the ISO/IEC C++ standard, the standard library (including STL) stuff is all encapsulated inside the std namespace.

---

### Post by nitro_n2o on 2007-07-18
or add: 
using namespace std;

---

