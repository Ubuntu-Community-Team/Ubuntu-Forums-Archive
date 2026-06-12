---
title: "[C++] Error: 'not a member'"
date: 2007-10-07
forum: Programming Talk
---

### Post by Mathiasdm on 2007-10-07
I'm working on a small project of mine, and I'm getting an error in Eclipse:
```
Severity and Description	Path	Resource	Location	Creation Time	Id
fout: ‘givenCompare’ is not a member of ‘Sudoku’	cppsudoku/trunk/src	SudokuGrid.cxx	line 56	1191749181962	13

```

The location of the code: [http://cppsudoku.googlecode.com/svn/trunk/src/](http://cppsudoku.googlecode.com/svn/trunk/src/)
I tried adding the 'givenCompare' as a 'friend' to SudokuGrid, but without result.

---

### Post by aks44 on 2007-10-07
First off, Sudoku::givenCompare does not need access to the internals of SudokuGrid. So, get rid of that useless friend declaration.

Now, how would the compiler know about Sudoku::givenCompare if you don't include the relevant header? :-\"

---

### Post by Mathiasdm on 2007-10-07
I am officially an idiot :lolflag:

---

### Post by Mathiasdm on 2007-10-07
Now I have another (probably stupid) question. The same line in the code (the 'sort' function) seems to have a problem:

```

fout: no matching function for call to &#8216;sort(__gnu_cxx::__normal_iterator<std::
 vector<int, std::allocator<int> >*, std::vector<std::vector<int, std::allocator<int> 
 >, std::allocator<std::vector<int, std::allocator<int> > > > >, __gnu_cxx::
 __normal_iterator<std::vector<int, std::allocator<int> >*, std::vector<std::
 vector<int, std::allocator<int> >, std::allocator<std::vector<int, std::
 allocator<int> > > > >, <unresolved overloaded function type>)&#8217;

```

If I'm interpreting this correctly, Eclipse seems to think there's no such thing as a sort function with 3 arguments :confused::confused:

Edit: If you happen to have any other suggestions to improve my code, please do mention :-)

---

### Post by aks44 on 2007-10-07
> **Mathiasdm said:**
> Eclipse seems to think there's no such thing as a sort function with 3 arguments :confused::confused:

I strongly suggest you to use a compiler/environment with more descriptive error messages... (or to copy full error ouput when posting) ;)


eg. G++ tells me:```
invalid initialization of reference of type «std::vector<int, std::allocator<int> >&" from expression of type «const std::vector<int, std::allocator<int> >"
```

I'm pretty sure you can figure it out with this information. ;)


> **Mathiasdm said:**
> If you happen to have any other suggestions to improve my code, please do mention
Make your code const-correct? :p

---

### Post by Mathiasdm on 2007-10-09
Thanks, I managed to fix it :) The error was in the HelperFunctions class.

---

