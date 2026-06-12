---
title: "vector of vectors issue(s) in c++"
date: 2005-12-25
forum: Programming Talk
---

### Post by oldmanstan on 2005-12-25
Ok, basically I need to know why this won't work...

Essentially I am trying to create a vector of vectors of ints then insert ints into the vectors of ints. I have been programming on and off for roughly 15 years but I'm a relative newbie to c++.

```

#include <vector>

int main() {
	typedef std::vector<int> IntVec;
	std::vector<IntVec> VecOfVec(5);
	VecOfVec.at(0).insert( 10 );
}

```

Here is the error message g++ spits out...

```
vecinvectest.cc: In function ‘int main()’:
vecinvectest.cc:17: error: no matching function for call to ‘std::vector<int, std::allocator<int> >::insert(int)’
/usr/include/c++/4.0.2/bits/vector.tcc:93: note: candidates are: typename std::vector<_Tp, _Alloc>::iterator std::vector<_Tp, _Alloc>::insert(__gnu_cxx::__normal_iterator<typename _Alloc::pointer, std::vector<_Tp, _Alloc> >, const _Tp&) [with _Tp = int, _Alloc = std::allocator<int>]
/usr/include/c++/4.0.2/bits/stl_vector.h:657: note:                 void std::vector<_Tp, _Alloc>::insert(__gnu_cxx::__normal_iterator<typename _Alloc::pointer, std::vector<_Tp, _Alloc> >, size_t, const _Tp&) [with _Tp = int, _Alloc = std::allocator<int>]
```

Any help would be greatly appreciated!

---

### Post by Jengu on 2005-12-25
try changing:

std::vector<IntVec> VecOfVec(5);

To:

std::vector< IntVec > VecOfVec(5);

I know the difference looks incredibly stupid, but because << and >> are operators, nested templates confuse the compiler unless you put spaces. Maybe it's smart enough to handle that if you use typedef and you're getting those errors for another reason, but that'd be my first guess.

---

### Post by LordHunter317 on 2005-12-25
As the error says, there's no version of insert() that does what you want.  ITYM, std::vector<T>::push_back().

As an aside, look at rolling your own matrix class, or using an existing library (boost::multi_array or similiar).  Anything will be far better than a vector of vectors, which should be generally avoided.

---

### Post by oldmanstan on 2005-12-25
[QUOTE=Jengu]try changing:

std::vector<IntVec> VecOfVec(5);

To:

std::vector< IntVec > VecOfVec(5);

I know the difference looks incredibly stupid, but because << and >> are operators, nested templates confuse the compiler unless you put spaces. Maybe it's smart enough to handle that if you use typedef and you're getting those errors for another reason, but that'd be my first guess.[/QUOTE]

Tried that and no dice, thanks for the feedback though!

---

### Post by LordHunter317 on 2005-12-25
Jengu, that error has nothing to do with what he's having.  And yes, typedefs are sufficent shielding.  The issue with > > vs. >> is a syntax, not semantic, issue.

---

### Post by oldmanstan on 2005-12-26
[QUOTE=LordHunter317]As the error says, there's no version of insert() that does what you want.  ITYM, std::vector<T>::push_back().

As an aside, look at rolling your own matrix class, or using an existing library (boost::multi_array or similiar).  Anything will be far better than a vector of vectors, which should be generally avoided.[/QUOTE]

That worked, thanks much! However, I don't understand why .push_back will work but .insert() won't. Both are methods available to vectors... Just curious, even if you could point me to someplace to read up on it that'd be great. Thanks again all for the help.

---

### Post by LordHunter317 on 2005-12-26
Because push_back() doesn't required a position, and insert() does.  If you use insert(), you must specify *where* to insert it.  

As far as references, look at the 'stl-manual' package, which is SGI's documentation, the Dinkumware and Rougewave STL docs online, the C++ FAQ Lite online, and *Effective STL*.

---

