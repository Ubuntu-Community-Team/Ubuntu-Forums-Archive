---
title: "compiler error in geany C++"
date: 2013-09-09
forum: Packaging and Compiling Programs
---

### Post by jinx3 on 2013-09-09
so i am in the process of learning C++ and am reading a book on it, one of the programs it has you make is:

```
#include <iostream>

using namespace std;


typedef unsigned short int SMALLNUMBER;


int main()
{
    SMALLNUMBER = 65535;
    cout << "small number:" << SMALLNUMBER << endl;
    SMALLNUMBER++;
    cout << "small number:" << SMALLNUMBER << endl;
    SMALLNUMBER++;
    cout << "small number:" << SMALLNUMBER << endl;
    return 0;
}



```

the code above is exactly how it appears in the book, but geany is giving me these errors:

```
g++ -Wall -c "exersize8.cpp" (in directory: /home/neo/Documents/c++/exercises)exersize8.cpp: In function ‘int main()’:
exersize8.cpp:9:14: error: expected unqualified-id before ‘=’ token
exersize8.cpp:10:41: error: expected primary-expression before ‘<<’ token
exersize8.cpp:11:13: error: expected unqualified-id before ‘++’ token
exersize8.cpp:12:41: error: expected primary-expression before ‘<<’ token
exersize8.cpp:13:13: error: expected unqualified-id before ‘++’ token
exersize8.cpp:14:41: error: expected primary-expression before ‘<<’ token
Compilation failed.



```

now i have no idea why these have popped up but some help would be great

---

### Post by steeldriver on 2013-09-09
The typedef defines a *type* of variable, not an actual variable - think of the word 'SMALLNUMBER' as a synonym for 'unsigned short int'. To define a variable of that type you would then do something like

```
SMALLNUMBER mynumber = 65535;
```

just as for any other simple type; and then use it like

```
cout << "small number: " << mynumber << endl;
```

and so on

---

### Post by jinx3 on 2013-09-09
> **steeldriver said:**
> The typedef defines a *type* of variable, not an actual variable - think of the word 'SMALLNUMBER' as a synonym for 'unsigned short int'. To define a variable of that type you would then do something like

```
SMALLNUMBER mynumber = 65535;
```

just as for any other simple type; and then use it like

```
cout << "small number: " << mynumber << endl;
```

and so on

see but the last program had that typed exactly the same way as is here, i double checked it cause it was just added into the book at the point im on as is shown here: 

```
#include <iostream>

using namespace std;


typedef unsigned short int USHORT;


int main()
	
{
	USHORT Width = 5;
	USHORT Length = 10;
	Length = 10;
	
	USHORT Area = Width * Length;
	
	cout << "width:" << Width <<"\n";
	cout << "length:" << Length << endl;
	cout << "area:" << Area << endl;
		return 0;
}
```

---

### Post by Kevin_Arnold on 2013-09-09
> **jinx3 said:**
> see but the last program had that typed exactly the same way as is here, i double checked it cause it was just added into the book at the point im on as is shown here: 

```
#include <iostream>

using namespace std;


typedef unsigned short int USHORT;


int main()
    
{
    USHORT Width = 5;
    USHORT Length = 10;
    Length = 10;
    
    USHORT Area = Width * Length;
    
    cout << "width:" << Width <<"\n";
    cout << "length:" << Length << endl;
    cout << "area:" << Area << endl;
        return 0;
}
```
These all have the type along with a variable name, like the other poster mentioned. You need 'TYPE Variable = value;'

---

### Post by jinx3 on 2013-09-09
well now i see exactly what i did and i feel like an idiot, #-oanyway thanks for the help

---

