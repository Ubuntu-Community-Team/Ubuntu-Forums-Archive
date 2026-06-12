---
title: "STL portability question on list iterators"
date: 2011-03-15
forum: Programming Talk
---

### Post by Jonas thomas on 2011-03-15
Hi,
I'm taking a class a in c++ and I work on my homework at lunch in VS2010, at school in vs08 and prefer doing things in ubuntu at home.

Anyway... I have this templated function that searches for a max value in a list and returns an iterator.
I had it functioning just fine in vs2010 at lunch and it looks like this.

```

template <typename T>
typename  list<T>::iterator maxLoc(list<T>& alist)
{

	list <T>::iterator iter,maxIter;

	if (alist.empty())
		return alist.end();

	iter = maxIter = alist.begin();

	iter++;

	while (iter!= alist.end())
	{
		if (*iter>*maxIter)
			maxIter =iter;
		iter++;
	}
	//
	return maxIter;
}
```

When I try compiling using gcc and code::blocks I'm coming up with a compiler errors that look like this:
```
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp||In function ‘typename std::list<T, std::allocator<_CharT> >::iterator maxLoc(std::list<T, std::allocator<_CharT> >&)’:|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|44|error: expected ‘;’ before ‘iter’|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|49|error: ‘iter’ was not declared in this scope|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|49|error: ‘maxIter’ was not declared in this scope|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp||In function ‘typename std::list<T, std::allocator<_CharT> >::iterator maxLoc(std::list<T, std::allocator<_CharT> >&) [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]’:|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|24|instantiated from here|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|44|error: dependent-name ‘std::list::iterator’ is parsed as a non-type, but instantiation yields a type|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|44|note: say ‘typename std::list::iterator’ if a type is meant|
||=== Build finished: 4 errors, 0 warnings ===|

```

It's making absolutely no sense on why this doesn't work for me in linux.
Complicating the issue the function call out has changed from when the textbook was written. (supposedly when .NET came in...)
Apparently the way it used to look was without the second typename. 
iow"
> 
template <typename T>
  list<T>::iterator maxLoc(list<T>& alist)


I tried that.. and I get this error:
```
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|11|error: expected constructor, destructor, or type conversion before ‘maxLoc’|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp||In function ‘int main()’:|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|24|error: ‘maxLoc’ was not declared in this scope|
/media/0AFD-2985/CIS2542/LAB06/Lab06Source/lab06.cpp|41|error: expected constructor, destructor, or type conversion before ‘maxLoc’|
||=== Build finished: 3 errors, 0 warnings ===|
```

Soo... I'm thinking that linux like the second "typename" also...
Any thoughts anyone??

---

### Post by Jonas thomas on 2011-03-15
Solution was obvious 
I changed:
list <T>::iterator iter,maxIter;
to 
typename list <T>::iterator iter,maxIter;

and problem was solved..

---

