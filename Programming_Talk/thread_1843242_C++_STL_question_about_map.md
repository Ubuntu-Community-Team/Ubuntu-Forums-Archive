---
title: "C++ STL question about map"
date: 2011-09-13
forum: Programming Talk
---

### Post by erotavlas on 2011-09-13
Hi,

I have a simple question about the use of a map of the C++ STL. The map is defined as ```
std::map<const std::string, float> myMap; 
```
I have a function
```

float myFunction(const std::string& name)
{
 return myMap.at(name);
 return myMap[name]; // I get a compiler error
		    // error: passing &#8216;const myMap&#8217; as &#8216;this&#8217; argument of ... discards qualifiers
}

```
I don't understand why...

Thank you

---

### Post by Senesence on 2011-09-13
Need more context.

This works fine for me:

```

#include <iostream>
#include <string>
#include <map>

std::map<const std::string, float> myMap;

float myFunction(const std::string& name){
	return myMap[name];
}

int main(int argc, char** argv){

	myMap["one"] = 1;
	myMap["two"] = 2;

	std::cout << myFunction("one") << std::endl;

	return 0;
}

```

---

### Post by GeneralZod on 2011-09-13
As Senesence said, more context is needed, but while we're waiting: I'm guessing myMap is const, or a const reference, in which case see:

[http://stackoverflow.com/questions/687789/c-const-stdmap-reference-fails-to-compile](http://stackoverflow.com/questions/687789/c-const-stdmap-reference-fails-to-compile)

---

