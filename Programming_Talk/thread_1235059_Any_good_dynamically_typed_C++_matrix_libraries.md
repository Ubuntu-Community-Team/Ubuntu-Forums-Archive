---
title: "Any good dynamically typed C++ matrix libraries?"
date: 2009-08-08
forum: Programming Talk
---

### Post by stair314 on 2009-08-08
I've been using Eigen for a while now and really like it, but I am finding that using templated types rather than inheritance makes it kind of a pain for object oriented projects. For example, I have a class representing vector-valued mathematical functions. Subclasses implement a method for returning the Jacobian matrix. In many cases, the Jacobian is diagonal, so it would be nice to be able to return a DiagonalMatrix, but of course there is no way of doing this without making two separate functions and querying which one to call at runtime.
I realize using dynamic types probably makes it very hard to get anywhere near as good of performance as Eigen has, especially when working with large nested expressions, but does anyone have any good experiences with dynamically typed matrix libraries to share?

---

### Post by Habbit on 2009-08-08
What is exactly the point of contention in your project? Using class hierarchies with templated types should not pose any problems as long as you don't splice the objects (i.e. as long as you use [FONT="monospace"]list<Matrix*>[/FONT] or [FONT="monospace"]list< some_smart_pointer<Matrix> >[/FONT] instead of [FONT="monospace"]list<Matrix>[/FONT]). Covariant return types of virtual functions work just fine, and you can use dynamic_cast without problems.

---

### Post by stair314 on 2009-08-08
The point of contention is that we can't do covariant return types in many places where we would like to, because eigen doesn't use inheritance. For example, if our base class declares a computeJacobian matrix that returns a Matrix *, we can't return a DiagonalMatrix instead. If DiagonalMatrix were a derived class of Matrix we could, but it is not.

---

### Post by Habbit on 2009-08-09
Then the problem is likely that Matrix specifies both the interface (which you want) and the implementation (which you want to "replace" with that of DiagonalMatrix). Since deriving DiagonalMatrix from Matrix seems to be a non-option to you, why don't you create an ABC (Abstract Base Class) specifying the pure virtual functions that comprise the part of the Matrix interface you want, then derive both Matrix and DiagonalMatrix both from this ABC and pass pointers to it around, instead of Matrix*.

Obviously, this requires you being able to modify the library you are using (Eigen) and recompile it, but as it is mostly a few-lines header change, you should be able to do so without a lot of hassle. I once had to do something similar with OGDF (Open Graph drawing Framework) -- remember to make the destructor of your ABC virtual!

---

### Post by TheStatsMan on 2009-08-09
> **stair314 said:**
> I've been using Eigen for a while now and really like it, but I am finding that using templated types rather than inheritance makes it kind of a pain for object oriented projects. For example, I have a class representing vector-valued mathematical functions. Subclasses implement a method for returning the Jacobian matrix. In many cases, the Jacobian is diagonal, so it would be nice to be able to return a DiagonalMatrix, but of course there is no way of doing this without making two separate functions and querying which one to call at runtime.


If you know the matrix is diagonal at compile time couldn't you use static polymorphism and avoid a query at runtime?

---

### Post by stair314 on 2009-08-09
> 
Then the problem is likely that Matrix specifies both the interface (which you want) and the implementation (which you want to "replace" with that of DiagonalMatrix). Since deriving DiagonalMatrix from Matrix seems to be a non-option to you, why don't you create an ABC (Abstract Base Class) specifying the pure virtual functions that comprise the part of the Matrix interface you want, then derive both Matrix and DiagonalMatrix both from this ABC and pass pointers to it around, instead of Matrix*.

Obviously, this requires you being able to modify the library you are using (Eigen) and recompile it, but as it is mostly a few-lines header change, you should be able to do so without a lot of hassle. I once had to do something similar with OGDF (Open Graph drawing Framework) -- remember to make the destructor of your ABC virtual!


Well, the problem goes deeper than that. In Eigen, complex expressions like A = (B+C)*D+E get sped up a lot by lazy evaluation / temporary elimination. To do this with dynamic types you'd need some sort of runtime environment. If I wrapped everything in an abstract base class, I would still get mathematically correct results, but without a lot of the optimizations that make Eigen appealing.


> 
If you know the matrix is diagonal at compile time couldn't you use static polymorphism and avoid a query at runtime? 


Only the callee knows that the matrix is diagonal at compile time. The callee has no idea. Besides, the callee is always forced to return the same type of matrix since there is no inheritance in Eigen. The way I get around it now is to always return a dense matrix, and if I want to return a diagonal matrix, I return a matrix consisting of a single column representing the diagonal:

```

void foo(MyClass *  a, MyClass * b)
{
 bool dense = true;
 Matrix c_dense;
 DiagonalMatrix c_diag;

 if (a->returnsDiagonal() && b->returnsDiagonal())
  {
     dense = false;
     c_diag = a->getSomeMatrix().col(0).asDiagonal() * b->getSomeMatrix().col(0).asDiagonal();
  }
  else
  {
     if (a->returnsDiagonal())
        c_dense = a->getSomeMatrix().col(0).asDiagonal() * b->getSomeMatrix();
     else if (b->returnsDiagonal())
        c_dense = a->getSomeMatrix() * b->getSomeMatrix().col(0).asDiagonal();
     else
         c_dense = a->getSomeMatrix() * b->getSomeMatrix();
  }

  // Now use either c_dense or c_diag based on value of dense
  // ....

```

Obviously this is a bit of a pain, and not very nice for another person to have to read later.

---

### Post by Habbit on 2009-08-09
Why would you need to return the same type of matrix always? You can use member function template specializations plus overloading to achieve similar results to covariant return types, with the additional benefic of making easier for the compiler to perform the Return Value Optimization and its variants, which might be harder to apply on the "foo" you posted:```

class MyClass {
public:
    template<typename T>
    T bar();
};

template<>
DiagonalMatrix MyClass::bar() {
    // Do bar and return a DiagonalMatrix
}

template<>
Matrix MyClass::bar() {
    // Do bar and return a Matrix, possibly with an algorithm
    // more efficient than calling the other version of foo
    // and creating a dense matrix from the diagonal one
}

// User code:
MyClass c;
DiagonalMatrix dm = c.bar<DiagonalMatrix>();
Matrix m = c.bar<Matrix>();
TridiagonalMatrix m3d = c.bar<TridiagonalMatrix>(); // would fail

```

---

### Post by stair314 on 2009-09-15
Doesn't this still depend on the caller knowing which kind of matrix to ask for? What I'm looking for is a way for the callee to specify the kind of matrix without the caller's intervention.

---

