---
title: "Retrieving the type of a typedef"
date: 2008-08-15
forum: Programming Talk
---

### Post by Markhor on 2008-08-15
Hello. My question is as follows: is it possible to retrieve the type from a typedef in a generic fashion? 
e.g., vector<int>::value_type will return the int type. 

However, suppose we write:

typedef pair<string, string> pstring;

pstring.first::value_type &string1 (.....);
pstring.second::value_type &string2 (.....);

Now I understand first_type and second_type are defined for pair,
 but I'm looking to find whether there is a general solution that would work for the built-in types
 analogously to how the value_type container typedef works for element types.... i.e.,

typedef int Integer
Integer::value_type int1 (.....);

Is this possible? 
Or is it simply a good reason to stay away from typedefs of primitive built-in types?

---

### Post by Jessehk on 2008-08-15
```

#include <iostream>

typedef int integer;

int main() {
    int x = 3;
    integer y = 5;

    std::cout << x << std::endl;
    std::cout << y << std::endl;
}

```

?


:)

---

