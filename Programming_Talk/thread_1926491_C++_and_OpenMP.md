---
title: "C++ and OpenMP"
date: 2012-02-16
forum: Programming Talk
---

### Post by erotavlas on 2012-02-16
Hi,

I have two questions about openMP. The first one is related to C++. I would like to parallelize a for loop inside a method of a class and the can the data members of the class (private or public) be shared inside an openMP construct (as myVector1, myMatrix, myVector2)?
```

int i, j;
#pragma omp parallel default(none) shared(myVector1, myMatrix, myVector2) private(i, j)
{
 #pragma omp for schedule (auto)
 for(i = 0; i < myVector.size(); ++i)
 {
 	for(j = 0; j < myVector2.size(); ++j)
 	{
 		myVector[i] = myMatrix[i][j] * myVector2[j];
 	}
 }
}

```
The second question is related to the preprocessor. Can I use the openMP compiler directives inside a preprocessor directive to have or not the parallel code?

```

int i, j;
#if PARALLEL
#pragma omp parallel default(none) shared(myVector1, myMatrix, myVector2) private(i, j)
{
#pragma omp for schedule (auto)
#endif
 for(i = 0; i < myVector.size(); ++i)
 {
 	for(j = 0; j < myVector2.size(); ++j)
 	{
 		myVector[i] = myMatrix[i][j] * myVector2[j];
 	}
 }
#if PARALLEL
}
#endif

```

Thank you

---

### Post by rchrd on 2012-02-16
Did you know that you can ask the developers of the OpenMP specs this question directly?
The OpenMP.org website has it's own forums. And a lot more information about OpenMP.

[http://openmp.org/forum/](http://openmp.org/forum/)

All you need do is register and post your questions.

---

### Post by erotavlas on 2012-02-17
> **rchrd said:**
> Did you know that you can ask the developers of the OpenMP specs this question directly?
The OpenMP.org website has it's own forums. And a lot more information about OpenMP.

[http://openmp.org/forum/](http://openmp.org/forum/)

All you need do is register and post your questions.

Ok, you are right.

Thank

---

