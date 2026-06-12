---
title: "No matching function for call..."
date: 2010-07-16
forum: Programming Talk
---

### Post by tdheff on 2010-07-16
*I have looked through numerous forums for a solution to this problem, but nothing seems to quite apply to my problem. Every time i call the function get (member of the class MixTable) it gives me an error that reads:*
> error: no matching function for call to ‘MixTable::get(int)’
**This is being called in this way from the file fitscreate.cpp:**
```
MixTable colData = MixTable(colPath, vector<char>(3,'s'));
vector<string> colName = colData.get(0);
```
**The MixTable class is defined in MixTable.h:**
```
#ifndef MIXTABLE_H
#define MIXTABLE_H

#include <iostream>
#include <fstream>
#include <string>
#include <vector>

class Index
{
	int pos;
	char whichvec;
	
	public:	
		int getPos();
		int getVec();
		Index(int i, char c);
};
		

class MixTable
{
	std::vector< std::vector<std::string> > svec;
	std::vector< std::vector<int> > ivec;
	std::vector< std::vector<double> > dvec;
	std::vector<Index> indices;
		
	
	public:
		void put(std::vector<std::string> invec);
		void put(std::vector<int> invec);
		void put(std::vector<double> invec);
		int get(int a);
		// template <typename T>  std::vector<T> get(int index);
		MixTable(std::string path, std::vector<char> types);

};

#endif
```
**And the relevant function in MixTable.cpp is:**
```
template <class T> vector<T> MixTable::get(int index)
{
    Index ind = indices[index];

    switch ( ind.getVec() )
    {
        case 's':
            return svec[ind.getPos()];
        case 'i':
            return ivec[ind.getPos()];
        case 'd':
            return dvec[ind.getPos()];
        default:
            return vector<int>(1,1);
    }
}
```

**Thank you so much for your help.**

---

### Post by MadCow108 on 2010-07-16
for one the get witrh the right signature must not be commented out.

and you need to provide the template type to the get function:
vector<char> g = t.get<char>(0);
the compiler cannot use assignee variable as type information due to implicit conversion rules (I guess).

And your implementation is incorrect. you cannot return multiple types with a single function, also not if its templated.
templates just create code bound to a fixed set of _compile_ time determined types.

You may need polymorphism which provides runtime type dependance
Or maybe your design is flawed.

---

