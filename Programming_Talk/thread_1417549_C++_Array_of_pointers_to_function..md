---
title: "C++ Array of pointers to function."
date: 2010-02-27
forum: Programming Talk
---

### Post by OVERPOWER8 on 2010-02-27
I am writing a program with function pointers. But it isn't working.
It's output is 
1 1 1 1 1,
but should be:
1 2 3 4 5.

I don't understand what's wrong.
Can someone help me?

here's the code:

```
#include <iostream>
using namespace std;

int func1() { return 1; }
int func2() { return 2; }
int func3() { return 3; }
int func4() { return 4; }
int func5() { return 5; }

int (*seq_array[5])() = {
    func1, func2, func3, func4, func5 };

enum ns_type { ns_func1, ns_func2, 
    ns_func3, ns_func4, ns_func5 };

int main()
{
    cout << seq_array[ns_func1] << endl;
    cout << seq_array[ns_func2] << endl;
    cout << seq_array[ns_func3] << endl;
    cout << seq_array[ns_func4] << endl;
    cout << seq_array[ns_func5] << endl;

    return 0;
}
```

---

### Post by dwhitney67 on 2010-02-27
You may want to consider actually calling the function to get the desired results.  For example:
```

...

cout << seq_array[ns_func1]() << endl;
cout << seq_array[ns_func2]() << endl;
cout << seq_array[ns_func3]() << endl;
cout << seq_array[ns_func4]() << endl;
cout << seq_array[ns_func5]() << endl;

```
Note the ()'s.

---

### Post by OVERPOWER8 on 2010-02-27
>> [B][dwhitney67]("http://ubuntuforums.org/member.php?u=322753")

[/B]Thanks. That,s right.

---

