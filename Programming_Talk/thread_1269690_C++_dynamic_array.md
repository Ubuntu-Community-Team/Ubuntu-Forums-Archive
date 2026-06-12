---
title: "C++ dynamic array"
date: 2009-09-18
forum: Programming Talk
---

### Post by nmccrina on 2009-09-18
Is this the correct way to deallocate a multidimensional dynamic array?

```
	int row = 0;

	for (row = 0; row < this->size; row++)
	{
		delete [] this->matrix[row];
		this->matrix[row] = NULL;
	}

	delete [] this->matrix;
```

I'm making a matrix object; this would be in the destructor. After some googling I'm 99.5% this is correct, but would like some confirmation :)

---

### Post by MadCow108 on 2009-09-18
this is correct if matrix is an array of pointers to pointers to memory block (e.g. double ** matrix)
delete [] ptr frees a memory block allocated with new []
delete frees a ptr allocated with new
and you need the loop because your matrix is not a continuous memory block in above case.

you would not need the loop if you allocate your matrix like that:
```

double * matrix = new double[rows*columns];
matrix[rowindex*columns + columnindex] = somevalue;
delete [] matrix;

```

if you are unsure use valgrind to check for memory leaks.

I would suggest using c++ native dynamic arrays, they don't need such a destructor:
```

#include <vector>
vector<vector<type> > matrix;
// or 
vector<type> matrix(dimension1*dimension2);

```

you can also use TR1 or boosts fixed sized arrays if you don't want variable size (or directly use boosts (or any other libraries) matrix class: [http://www.boost.org/doc/libs/1_40_0/libs/numeric/ublas/doc/matrix.htm](http://www.boost.org/doc/libs/1_40_0/libs/numeric/ublas/doc/matrix.htm))

---

### Post by nmccrina on 2009-09-18
Thanks, a lot of useful information there! I hadn't heard of valgrind before, I will check it out.

---

