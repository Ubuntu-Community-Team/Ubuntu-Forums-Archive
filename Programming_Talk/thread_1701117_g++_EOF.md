---
title: "g++ EOF"
date: 2011-03-06
forum: Programming Talk
---

### Post by cap10Ibraim on 2011-03-06
```

#include <iostream>
using namespace std;
int main()
{
	int character; //use int because char can't represent eof	
	cout<<"Before input the value of cin.eof() is "<<cin.eof()<<endl
	<<"enter a setence "<<endl;
	while( (character=cin.get()) != EOF )
		cout.put(character);
	cout<<"EOF in this system is "<<character<<endl;
	return 0;
}

```
```

main.cpp: In function ‘int main()’:
main.cpp:8: error: ‘EOF’ was not declared in this scope

```
why eof is not recognized !

---

### Post by cap10Ibraim on 2011-03-06
i used 0 instead of EOF 
but there is an infinite loop when i press ctrl-d ?!

---

### Post by cgroza on 2011-03-06
Maybe you mean cin.eof(), or .eof() on another stream.

---

### Post by ksprasad on 2011-03-06
Hi,

 Yes. Use cin.eof() function instead of EOF. there is no such macro defined   EOF.

Regards,
ksprasad

---

### Post by cap10Ibraim on 2011-03-06
thanks guys i fixed the while loop as you suggested 
```

while(  cin.eof() != 1 ){
		character = cin.get();
		cout.put(character);
	}

```

---

### Post by cgroza on 2011-03-06
> **cap10Ibraim said:**
> thanks guys i fixed the while loop as you suggested 
```

while(  cin.eof() != 1 ){
        character = cin.get();
        cout.put(character);
    }

```
The while condition could be written as:
```
while( ! cin.eof() );
```
Much simpler.

---

### Post by cap10Ibraim on 2011-03-06
> **cgroza said:**
> The while condition could be written as:
```
while( ! cin.eof() );
```
Much simpler.

i know  ,but i'm just not used to this style yet

---

