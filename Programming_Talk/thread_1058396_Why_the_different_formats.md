---
title: "Why the different formats"
date: 2009-02-02
forum: Programming Talk
---

### Post by S0m3th1ngw13rd on 2009-02-02
Learnig C++ and I noticed that after compiling: 

```
#include <iostream>

	int main() 
		{
			std::cout << "Hello World";
			return 0;

		}
```

And then:


```
#include <iostream>

int main()
	{
using namespace std; 


cout << "Hello World!" << endl;  // cout and endl live in the iostream library

return 0;

	}
```

Give the same result, so question is which way is easier, or standard. Or should I just do it one way and do it the same way every time and not worry about the differences.

---

### Post by slavik on 2009-02-02
it's called style, pick the one you like and use it.

---

### Post by S0m3th1ngw13rd on 2009-02-02
Thanks Slavik 

thats what I thought but just wanted to be sure

---

