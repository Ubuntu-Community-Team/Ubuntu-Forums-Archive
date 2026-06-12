---
title: "Syntax Issue - C++ Pointer to Vector"
date: 2009-10-28
forum: Programming Talk
---

### Post by kachofool on 2009-10-28
Hey... 

I can't get the following (trivial) code to compile. I'm doing something stupid but I can't see it... any ideas?

```

int main()
{

std::vector<double> *_sensorPosition;
_sensorPosition = new std::vector<double>;
_sensorPosition.push_back(22.345);

std::cout << _sensorPosition[0] << std::endl;

return 0;
}

```

And the error(s):

try.cpp: In function ‘int main()’:
try.cpp:211: error: request for member ‘push_back’ in ‘_sensorPosition’, which is of non-class type ‘std::vector<double, std::allocator<double> >*’
try.cpp:214: error: no match for ‘operator<<’ in ‘std::cout << * _sensorPosition’


I'm guessing my vector pointer and subsequent (new) function call aren't working out.

Regards,

-KF

---

### Post by escapee on 2009-10-28
[PHP]
int main()
{
  std::vector<double> *_sensorPosition;
   _sensorPosition = new std::vector<double>;
   _sensorPosition->push_back(22.345);
   std::cout << _sensorPosition->at(0) << std::endl;
 
  return 0;
}

[/PHP]

This should work.  If you are using a pointer to a reference, you need to deference the pointer while accessing it. (-> instead of .)  Also, if there is a way to do it, I don't know how, but since the [] operator is actually a pointer offset, you should use the at() method of the vector to access it's elements.

---

### Post by SledgeHammer_999 on 2009-10-28
> **escapee said:**
> 
Also, if there is a way to do it, I don't know how, but since the [] operator is actually a pointer offset, you should use the at() method of the vector to access it's elements.

or do a **(*_sensorPosition)[]**

to the OP another way of doing the thing you want(very ugly for me) is **(*_sensorPosition).push_back()**

You should read again that chapter about pointer dereference :p

---

### Post by escapee on 2009-10-28
> **SledgeHammer_999 said:**
> or do a **(*_sensorPosition)[]**

to the OP another way of doing the thing you want(very ugly for me) is **(*_sensorPosition).push_back()**

You should read again that chapter about pointer dereference :p

Hah, good thing I didn't try to show him the alternative syntax as you did.  I was going to put it as *(_var), which would explain why that wouldn't compile  :p Been a while.

Ah well, at least I don't have to deal with this crap daily anymore :D

---

### Post by MadCow108 on 2009-10-29
why are you allocating a vector with new?
a vector is a ~12 byte non-polymorphic structure which should fit in the stack without problems
allocating it dynamically just creates memory leak and exception safety problems

---

### Post by dribeas on 2009-10-29
Agree with MadCow: there is no justifiable reason to add the complexity of dynamic memory management into the problem there. The vector should be an auto variable (local, stack allocated) as the real data will be heap allocated internally inside the vector class. That would indirectly get rid of the memory leak you have in your code (you are not deleting the vector at the end of the function)

---

