---
title: "Question about  (itr2++)++;"
date: 2011-09-20
forum: Programming Talk
---

### Post by xuyuangogogo on 2011-09-20
Hi all!
 
I have a question about a very little program:
 
```
#include<iostream>
#include<vector>
#include<stdio.h>
using namespace std;
int main() {
 vector<int> v;
 vector<int>::iterator itr1, itr2;
 v.push_back(1);
 v.push_back(2);
 itr1 = v.begin();
 (itr2++)++;
 cout << *itr1 << endl << *itr2 << endl;
 return 0;
}

```
 
I got 
1
2
as the result.
 
But I have no idea why the result is like this.
 
Anybody can help me to figure out?
 
Thanks.

---

### Post by NovaAesa on 2011-09-20
Your code is buggy, while it does produce output on your machine, it segfaults on mine. Have a look at iter2, you never initialize it with anything.

---

### Post by xuyuangogogo on 2011-09-20
Sorry, the code is:
```
#include<iostream>
#include<vector>
#include<stdio.h>
using namespace std;
int main() {
 vector<int> v;
 vector<int>::iterator itr1, itr2;
 v.push_back(1);
 v.push_back(2);
 itr1 = v.begin();
 itr2 = itr1;
 (itr2++)++;
 cout << *itr1 << endl << *itr2 << endl;
 return 0;
}

```
 
> **NovaAesa said:**
> Your code is buggy, while it does produce output on your machine, it segfaults on mine. Have a look at iter2, you never initialize it with anything.

---

### Post by NovaAesa on 2011-09-20
the line (iter2++)++; is possible what is confusing you. First, iter2++ will increment the iterator. It is also an expression, evaluating to the iterator *before* it's incremented. This new iterator is then incremented by the outer++ but then thrown away because it isn't assigned to anything. So the net result is that iter2 has been incremented once (hence is pointing to v[1]).

Does that clear things up?

---

