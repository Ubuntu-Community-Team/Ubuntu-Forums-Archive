---
title: "[SOLVED] C++ algorithm count_if"
date: 2008-02-02
forum: Programming Talk
---

### Post by Houman on 2008-02-02
hi there;

I have decided to use the C++ standard libraries algorithms for the first time, 
so the first problem i was going to solve with it was basically counting the number of "trues" in a vector of bools, simple enough, but its confusing me;

here is the code that i have:

```

int countTrues(const vector<bool>& vec)
{

return (int) count_if (vec.begin(), vec.end(), isTrue);


}

bool isTrue(bool val)
{
return val;
}

```

now with my good old C i could have written this in one line, so is there any way not to have to use an additional function? is there any way to use the algorithms to solve this problem in less number of lines?


regards

Houman

---

### Post by aks44 on 2008-02-02
Why not use plain std::count? std::count_if is best used for "fancy" predicates, which is clearly not your case.

---

### Post by Houman on 2008-02-02
hi there;

oh I didnt know about count, thanks, i looked it up, its exactly what i need;

this is the problem when you try to use something you havnt learned systematically :S


regards

Houman

---

### Post by lnostdal on 2008-02-02
the c++ boost libraries have a lambda facility 

but, i'm not gonna bother with lambdas in c++ .. here is how it looks in lisp tho:
```

(defun count-trues (sequence)
  (count-if (lambda (val) val)
            sequence))
 
```

edit: i guess i kinda answered a different question; "how to splice the function definition 'into' the function call" -- that is how i read it :)

---

### Post by uljanow on 2008-02-04
```
#include <vector>
#include <algorithm>
#include <functional>

int main()
{
        std::vector<bool> vec(3);
        vec.at(0) = true;
        vec.at(1) = false;
        vec.at(2) = true;

        std::count_if(vec.begin(), vec.end(), std::bind2nd(std::equal_to<bool>(), true));
}
```
.

---

### Post by aks44 on 2008-02-04
uljanow I really like your example. :)

Reminds me of one of my favourite sayings (roughly translated from french): "*why make it simple when you could make it complicated?*" ;)

---

