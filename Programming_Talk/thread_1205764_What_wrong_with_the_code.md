---
title: "What wrong with the code?"
date: 2009-07-06
forum: Programming Talk
---

### Post by kcode on 2009-07-06
```
vector< pair<int, int> > vp(1);
	pair< int, int> p;
	p.first = 0;
	p.second = 1;
	vp.push_back(p);
	p = vp[0];
	cout << p.first << "\t" << p.second << endl;
```

Its output is
0        0

---

### Post by MadCow108 on 2009-07-06
vector< pair<int, int> > vp(1);
initialiases one element (with 0,0)
push_back adds another one (=>size = 2)
so your element is vp[1]

use reserve if you want to set the size without initialising

btw theres are nice shortcut to create pairs:
make_pair(0,1)

---

### Post by dwhitney67 on 2009-07-06
That's because you never initialized the first entry in the vector.  When you inserted (push_back) an entry, you are actually inserting the second entry into the vector.

Here's some code for you to play with:
```

#include <vector>
#include <iostream>

int main()
{
   using namespace std;

   vector< pair<int, int> > vp(1);
   pair< int, int> p;
   p.first = 0;
   p.second = 1;
   vp.push_back(p);

   cout << "vp.size() = " << vp.size() << std::endl;

   p = vp[0];
   cout << p.first << "\t" << p.second << endl;

   p = vp[1];
   cout << p.first << "\t" << p.second << endl;
}

```

P.S.  The next time you post a snippet of code, please be courteous and provide a complete program.

---

### Post by kcode on 2009-07-06
Thanks for the help, I got my mistake.

@dwhitney67
Thought of it, but the rest was irrevelant.

---

