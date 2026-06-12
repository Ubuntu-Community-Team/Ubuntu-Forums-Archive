---
title: "std::cout?"
date: 2009-07-05
forum: Programming Talk
---

### Post by arjuntank on 2009-07-05
i use netbeans for c/c++ programs. I dont want to use std::cout. can i change it to only cout?

PS. total newbie

thanks

---

### Post by TheStatsMan on 2009-07-05
using namespace std;

---

### Post by arjuntank on 2009-07-05
hey! thanks, it worked!

---

### Post by MadCow108 on 2009-07-05
and if you want only certain elements in your namespace:

using std::cout;
using std::endl;
cout << "test" << endl;

[http://www.cplusplus.com/doc/tutorial/namespaces/](http://www.cplusplus.com/doc/tutorial/namespaces/)

---

### Post by arjuntank on 2009-07-05
> **MadCow108 said:**
> and if you want only certain elements in your namespace:

using std::cout;
using std::endl;
cout << "test" << endl;

[http://www.cplusplus.com/doc/tutorial/namespaces/](http://www.cplusplus.com/doc/tutorial/namespaces/)
thanks for the tips and tutorial!
:)

---

