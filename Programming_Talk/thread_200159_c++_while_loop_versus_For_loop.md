---
title: "c++ while loop versus For loop"
date: 2006-06-19
forum: Programming Talk
---

### Post by hod139 on 2006-06-19
All,

**Background:**  Some code I've been writing required a lightweight matrix/vector class with some basic linear algebra.  After writing up something quick, I decided to compare the running time of my matrix-matrix multiply with Boost's ublas library.  My code was slower and I was confused why as matrix-matrix multiplication is fairly straight forward.  A colleague of mine suggested replacing the for loops with corresponding decrementing while loops.  To my shock, using while loops improved my running time and it was as fast as Boost's.  This is confusing to me, as I would have expected g++ to produce the same assembly for such a straight forward segment of code.

My friend didn't know why decrementing while loops were faster than incrementing for loops, but in all the vision code he works with he noticed that while loops were always used in preference to for loops.  I did some quick googling, and the best I could come up with was that most CPUs tend to have better branching tools for >= 0 tests.  But replacing the incrementing for loops with decrementing for loops still did not net the gain in performance found when using decrementing while loops.  

**Questions:** 
1. Does anyone here have a guess as to why g++ does not produce the same assembly code for the corresponding methods?
2. Why is the decrementing while loop implementation much faster than the incrementing for loops (at least for the first run)?  
3.  The subsequent improvements in running time for the FOR loop implementation when calculating an average time over 20 runs is probably due to caching; but the running time eventually overtakes that of the while loop!  Why is the performance increase in the FOR loop over subsequent calls so large, eventually beating the while loop?

The methods:
```

Matrix<T> mult_FOR(const Matrix<T>& rhs) const{
    assert(nCol_ == rhs.size1() );     
    size_t rhs_size2 = rhs.size2();
    Matrix<T> theMatrix(nRow_, rhs_size2);
    size_t dataLoc;
    for (size_t r=0; r < nRow_; ++r) {
       for (size_t c=0 ; c < rhs_size2; ++c) {
          T& x = theMatrix(r, c);
          dataLoc = nCol_*r;
          for (size_t i=0; i < nCol_; ++i) { 
             x += data_[dataLoc++] * rhs(i,c);
         }
      }
   }
   return theMatrix;
}

``` 
```

Matrix<T> mult_WHILE(const Matrix<T>& rhs) const{
    assert(nCol_ == rhs.size1() );
    int rhs_size2 = rhs.size2();
    Matrix<T> theMatrix(nRow_, rhs_size2);
    int dataLoc;
    
    int r, c, i;
    r = nRow_ -1;
    do{
      c = rhs_size2 -1;
      do{
         T& x = theMatrix(r, c); 
         i = nCol_ -1;
         dataLoc = nCol_*r + i; 
         do{     
            x += data_[dataLoc--] * rhs(i,c);
            --i;
         } while(i >= 0);
      --c;
      } while (c >= 0);
      --r;
    } while(r >=0);
    return theMatrix;
}

``` 
and execution:
```

 g++ -O2 Post.cpp
./a.out
First time for mult_FOR (seconds): 2.76
Average time for mult_FOR (seconds): 2.0005
Deviation for mult_FOR (seconds): 0.81
First time for mult_WHILE (seconds): 2.28
Average time for mult_WHILE (seconds): 2.27
Deviation for mult_WHILE (seconds): 0.02

``` 

If anyone wants the entire file, I have attached it (I had to name it Post.txt as it would not let me upload Post.cpp). here: [ATTACH]11480[/ATTACH]

---

### Post by thumper on 2006-06-20
Just a small point, but have you tried running the mult_WHILE first and the mult_FOR second?  It could just be the initial paging.

Also, one difference in your code is that the while version uses **int** whereas your for version uses **size_t**.  Depending on your platform, these may be different.

---

### Post by hod139 on 2006-06-20
[quote=thumper]Just a small point, but have you tried running the mult_WHILE first and the mult_FOR second?  It could just be the initial paging.
[/quote] Thanks for this suggestion.  When I switched the call order to mult_WHILE first, and mult_FOR second, the large deviation in time was now with mult_WHILE, so the initial paging must be the culprit for the time variation.

> 
Also, one difference in your code is that the while version uses **int** whereas your for version uses **size_t**.  Depending on your platform, these may be different. 
I had changed the datatype to int in the decrementing while version since the values in the iteration had to go to -1.  I forgot to change them in the FOR version for consistency, thanks for pointing that out. 

Listening to your suggestions, I changed the methods to use consistent datatypes and I now ignore the timing results of the first call.  The results are: (I was getting impatient so I decreased the size of the matrices being multiplied, which is why the time decreased):
```

Results when calling mult_WHILE first
Average time for mult_WHILE (seconds): 0.7535
Average time for mult_FOR (seconds): 0.5875
Results when calling mult_FOR first
Average time for mult_FOR (seconds): 0.597
Average time for mult_WHILE (seconds): 0.755

``` Now it would appear that the FOR loop implementation is faster!!  The code that generated the above results is attached here: [ATTACH]11510[/ATTACH]. 

At least my question of timing deviations between the first run and subsequent runs is answered, but why is there still a large difference in time between the FOR loop implementation and the WHILE loop implementation?

---

### Post by thumper on 2006-06-20
Many compilers have optimisations that they run over for loops as they are probably the most common looping construct that is used.

I have some style comments if you are interested in hearing them.

---

### Post by hod139 on 2006-06-20
[quote=thumper]I have some style comments if you are interested in hearing them.[/quote]

Not my original intent with this post, but yeah I'd like to hear your comments.

---

### Post by thumper on 2006-06-20
1) Use typename instead of class - small thing but double isn't a class
```
template <typename T>
class Matrix
{
   //...
};
```
2) Put things in a namespace - I admit that this is just sample code, and the original may well be, but anyway, it is good practice.

3) Methods size1 and size2 could be more readable as row_size and col_size, or sum such.

4) Better to write operator= with a copy constructor and swap.

5) Initialiser lists are better practice than assignment in constructors.

6) Doing an assert after a new isn't going to give you anything because by default if new cannot allocate it throws an exception.

7) Perfer non-member non-friend functions.
```

template <typename T>
Matrix<T> operator*(Matrix<T> const& lhs, Matrix<T> const& rhs)
```

8) More descriptive variable names are good when coming back to read your own code.

9) Does it really make sense to have a default arg for the operator() ?

---

### Post by hod139 on 2006-06-20
Thumper, thanks for the feedback.  I have posted responses below all of your suggestions.

> **thumper]1) Use typename instead of class - small thing but double isn't a class
```
template <typename T>
class Matrix
{
   //...
} said:**
>  To be honest I wrote class simply because it is shorter :).  Is there a reason I should choose one over the other (other than clarifying the expected type as you noted).

> 
2) Put things in a namespace - I admit that this is just sample code, and the original may well be, but anyway, it is good practice.
 In actual code it is.

[quote]
3) Methods size1 and size2 could be more readable as row_size and col_size, or sum such.
 I agree completely, but Boost's ublas library used size1 and size2; and this class is meant to replace our dependence on ublas.  To make porting easier, I simply used their naming convention.

> 
4) Better to write operator= with a copy constructor and swap.
 Guess I don't understand why with this point.  My copy constructor only calls the private copy method, so why is operator= better calling the copy constructor and a swap?

> 
5) Initialiser lists are better practice than assignment in constructors.
 For primitive types does it matter?  Why is it better practice?

> 
6) Doing an assert after a new isn't going to give you anything because by default if new cannot allocate it throws an exception.
 Thanks, must be leftover practice from my malloc days.

> 
7) Perfer non-member non-friend functions.
```

template <typename T>
Matrix<T> operator*(Matrix<T> const& lhs, Matrix<T> const& rhs)
``` 
8) More descriptive variable names are good when coming back to read your own code.
 Why prefer non-member non-friend functions over member functions?  Why is a non-member operator* preferential to a member operator*
```

Matrix<T> operator*(const Matrix<T>& rhs) const{

``` 
> 
9) Does it really make sense to have a default arg for the operator() ? It was when I was using this class to also store vectors.  Then I could access the element using a single param.  Now that I also wrote a Vector class, you are correct in that the default is no longer needed.

---

### Post by LordHunter317 on 2006-06-20
[QUOTE=hod139]Guess I don't understand why with this point.  My copy constructor only calls the private copy method, so why is operator= better calling the copy constructor and a swap?[/quote]Because calling copy constructor and swap automatically handles self-assignment correctly in the face of exceptions, which is why it used in 99% of cases.

Your function as written isn't exception safe.  If copy() throws, your object will go into an undefined state.

>  For primitive types does it matter?  Why is it better practice?In practice it doesn't matter for primitives.  The issue is that if you don't use an initalizer list, everything gets set a default value before the constructor body is run.  For a primitive, this isn't a big deal.  For other things, it is.

>  Why prefer non-member non-friend functions over member functions?It improves encapsulation: a non-friend non-member function can only be dependent on your classes' public interface.  This means that you can change class implementation without affecting them.

---

### Post by hod139 on 2006-06-20
[quote=LordHunter317]
It improves encapsulation: a non-friend non-member function can only be dependent on your classes' public interface.  This means that you can change class implementation without affecting them.[/quote]

But I can always change which methods are public in the class.  Too me, using non-friend non-member functions seems to be the C way of doing things, where you have all these stucts laying around and accessor methods to them.  

If the method is not going to alter the state of the class, you can declare it const, which gains the same protection as a non-friend non-member function.

---

### Post by LordHunter317 on 2006-06-20
[QUOTE=hod139]But I can always change which methods are public in the class.[/quote]Which is an API break, but sure.  It doesn't change the fact that non-member, non-friend functions *depend on fewer details* then member functions or non-friend functions.  

Basically, encapsulation is enhanced because there are fewer things you can change that would require you to change the calling function.

> Too me, using non-friend non-member functions seems to be the C way of doing things,They're clearly not.  The STL uses them everywhere, as does the standard library.

> where you have all these stucts laying around and accessor methods to them.  No, that's not what's being suggested.  Accessor methods are dependent on private details, hence they should be member functions.  But functions that only need the accessor methods aren't dependent on private details, hence they shouldn't be member functions.

> If the method is not going to alter the state of the class, you can declare it const, which gains the same protection as a non-friend non-member function.No, it does not.  You're confusing mutability with encapsulation.  I could have a non-member function that alters state (e.g., for_each()) but is still non-member.  Const means the class state is immutable.  Non-friend, non-member means I can only access public details.

---

### Post by hod139 on 2006-06-20
So, lets take this to the extreme.  Are you suggesting that a class should only contain constructors, destructors and accessor methods, with everything else being non-member non-friend classes.

Also, isn't there going to be a loss in performance if you hide all the class details from these methods, and rely soley on accessor methods?

How would this work for virtual methods and inheritance?

---

### Post by LordHunter317 on 2006-06-20
[QUOTE=hod139]So, lets take this to the extreme.  Are you suggesting that a class should only contain constructors, destructors and accessor methods, with everything else being non-member non-friend classes.[/quote]No.  What I said, and I'll say again is simple:  If a method relies only on public members, it should be a non-friend, non-member function.

For a class like std::valarray, operator* can be a non-friend, non-member function because it can use operator[] to get access to all the entries of the valarray to do the multiplication.

If there wasn't an operator[], then it'd have to be a member function, obviously.

> Also, isn't there going to be a loss in performance if you hide all the class details from these methods,If you're worried about loss at that level, you probably shouldn't be using C++.  The answer is that it doesn't matter for the overwhelming majority of cases.  But you shouldn't be creating accessors simply to make functions non-friend, non-member *per se*. 

> How would this work for virtual methods and inheritance?Dynamic binding doesn't change based on the caller.

---

### Post by hod139 on 2006-06-20
Ok, I'm convinced that non-member non-friend functions can improve data encapsulation, but there still seems to be problems.

All these functions are now going to be global (protection inside a namespace is a must), so isn't there going to be problems with templates?  For example
```

namespace MatrixSpace{
   class Matrix{
      ... class stuff
   };
   Matrix* method1(...params...);

   class Matrix2{
      ... class stuff
   };
   Matrix2* method1(...params...);
}
template<class T>
void doSomething( /* params */ )
{
   // invoke T's function
   T *pt = T::method1( /* params */ );    // Can't determine T
   ...
}
``` 
Anyways, the issue of non-member non-friend aside, do you have any idea why the running time between the WHILE loop and FOR loop implementations of matrix multiply have such different running times?

---

### Post by thumper on 2006-06-20
You cannot override a method soley on return type, so the example given does not hold.

Most of the time the type is passed as a parameter into the function, and hence the type deducable.

---

### Post by Harleen on 2006-06-20
I'd expect both kind loops to be equally fast. In you while-loop example you have one subtraction and one addition more in the inner loop than in the for loop.
I think about these lines:
```
         i = nCol_ [COLOR="Red"]-1[/COLOR];
         dataLoc = nCol_*r [COLOR="Red"]+ i[/COLOR]; 
```
versus these in the for-loop example:
```
          dataLoc = nCol_*r;
          for (size_t i=0; i < nCol_; ++i) { 

```

And I also like to add one style hint. I would declare rhs_size2 constant in this function. This won't speed it up, but would make own mistakes less likely.
To improve speed, you could use pointers instead of  data_[dataLoc++].
And instead of 
```
dataLoc = nCol_*r;
```
you can write 
```
dataLoc += nCol_;
```
This May improve speed, as you are no longer accessing the variable r and replace the multiplication with an addition.

---

### Post by StickGuy on 2006-06-20
[QUOTE=LordHunter317]
[QUOTE=hod139]
How would this work for virtual methods and inheritance?[/QUOTE]
Dynamic binding doesn't change based on the caller.[/QUOTE]
I think the point he was trying to make is that this system seems to breakdown when working with polymorphism.  Consider this example:
```

#include <iostream>

class Circle {
public:
	Circle():radius(0.0) {}
	Circle(double r):radius(r) {}
	~Circle() {}

	double GetRadius() const { return radius; }
	void SetRadius(double r) { radius = r; }

	virtual double MyArea() const {
		return GetRadius() * GetRadius() * 3.14159;
	}
private:
	double radius;
};

double Area(const Circle &c) {
	return c.GetRadius() * c.GetRadius() * 3.14159;
}

class Sphere : public Circle {
public:
	Sphere():Circle() {}
	Sphere(double r):Circle(r) {}
	~Sphere() {}

	virtual double MyArea() const {
		return GetRadius() * GetRadius() *
				GetRadius() * 3.14159 * (4.0 / 3.0);
	}
};

double Area(const Sphere &s) {
	return s.GetRadius() * s.GetRadius() *
			s.GetRadius() * 3.14159 * (4.0 / 3.0);
}

int main(int argc, char **argv){
	Circle c(3.0), *p;
	Sphere s(2.0);

	p = &s;

	std::cout << "Area of c: " << Area(c) << std::endl;
	std::cout << "Area of s: " << Area(s) << std::endl;
	std::cout << "Area of p: " << Area(*p) << std::endl;

	std::cout << "Area of c by member: " << c.MyArea()
			  << std::endl;
	std::cout << "Area of s by member: " << s.MyArea()
			  << std::endl;
	std::cout << "Area of p by member: " << p->MyArea()
			  << std::endl;
	return 0;
}

```
Admittedly, this is not the best example, but the point is that calling p->MyArea() returns the correct value while Area(*p) does not.  How would your system deal with this situation?

I'm not sure that your suggestions leads to better data encapsulation.  From a programmer's perspective, both member functions and these external functions present, effectively, the same interface to the data.  The difference being that when/if the class implementation changes, there are fewer places where the code may break.

---

### Post by LordHunter317 on 2006-06-20
[QUOTE=StickGuy]I think the point he was trying to make is that this system seems to breakdown when working with polymorphism.[/quote]But it doesn't.    Area() shouldn't be non-friend, non-member beacuse it is dependent on a semantic property of the class.  Specifically, how area is computed is a property of the class.

That's an implict gotcha present in any OOP though: details that aren't expressed in code are always effectively private.  In this case, the missing detail is the area formula.

So the rule does hold as long as your specification is complete.  The issue here is your specification is incomplete: you're reliant on details not specified as part of the class implementation.

The proof is in the non-member Area function itself.  When it comes to computing area, a Circle is-not-a Sphere.  If you broke the 'is-a' rule, it means you did something wrong. 

> I'm not sure that your suggestions leads to better data encapsulation.It does, as long as you follow the rule.

> From a programmer's perspective, both member functions and these external functions present, effectively, the same interface to the data.If you have that you already have a problem.  Multiple functions to do the same thing are almost universally bad.

---

### Post by StickGuy on 2006-06-21
[QUOTE=LordHunter317]But it doesn't.    Area() shouldn't be non-friend, non-member beacuse it is dependent on a semantic property of the class.  Specifically, how area is computed is a property of the class.
[/quote]
I'm confused here.  You support internalizing the computation of the Area function because it is dependent on the semantic properties of the class.  However, you support the externalization of the matrix multiplication, which is also dependent on the semantic properties of the class.  Which is it?

[QUOTE=LordHunter317]That's an implict gotcha present in any OOP though
[/quote]
If your argument is against OOP in general, then that is a different discussion entirely...

[quote=LordHunter317]
The proof is in the non-member Area function itself.  When it comes to computing area, a Circle is-not-a Sphere.  If you broke the 'is-a' rule, it means you did something wrong. 

It does, as long as you follow the rule.
[/quote]
Your implication here is that the base class function should always perform the correct operation for any derived class.  However, this is not always true, which is why there are virtual functions.  Are you saying that any function that is virtual should be made a member function due to semantic dependencies?

[QUOTE=LordHunter317]
[quote=StickGuy]
From a programmer's perspective, both member functions and these external functions present, effectively, the same interface to the data.
[/quote]
If you have that you already have a problem.  Multiple functions to do the same thing are almost universally bad.[/QUOTE]
That was not what I meant.  I meant that if you have either a set of member functions or (exclusive or!) a set of external functions that provide a certain set of functionality, then from a programmer's perspective, the interface provided is the same.  There is no win for encapsulation by using non-member, non-friend functions.  The win is for maitainability.

---

### Post by LordHunter317 on 2006-06-21
> **StickGuy]I'm confused here.  You support internalizing the computation of the Area function because it is dependent on the semantic properties of the class.  However, you support the externalization of the matrix multiplication, which is also dependent on the semantic properties of the class.  Which is it?[/quote]I wasn't clear.  Area shouldn't be non-friend, non-member because it is dependent on a *unstated* semantic property of the class.

It all comes to do the 'is-a' rule, which can never be broken.  Can Area be computed in the same way for all shapes?  No.  This means it must be a virtual member function.  It cannot be anything else said:**
> If your argument is against OOP in general, then that is a different discussion entirely...No, it isn't.  But the point is you must be careful to ensure you haven't broken the 'is-a' relationship.  How to compute area is a detail that was missed in your example.

> Your implication here is that the base class function should always perform the correct operation for any derived class.No, it isn't.  It's perfectly permissible to call virtual functions from non-friend, non-member functions.

What is not permissible is to encapsulate non-public class details inside a non-friend, non-member function.  Which is what your example did: the area formula is a detail of Shape classes.  The proof is in the fact you violated the 'is-a' relationship rule.

> Are you saying that any function that is virtual should be made a member function due to semantic dependencies?You cannot have a virtual non-member function, so of course.

>  meant that if you have either a set of member functions or (exclusive or!) a set of external functions that provide a certain set of functionality, then from a programmer's perspective, the interface provided is the same.Right and you if you have both, you've broken the duplication rule.  You don't do that.

 > There is no win for encapsulation by using non-member, non-friend functions.  The win is for maitainability.No, wrong, here's a simple example:```
class IMatrix2D {
public:
    virtual void at(int row, int col) = 0 const;
}

IMatrix2D*
multiply(const IMatrix2D& lhs, const IMatrix2D rhs) {
    // Do multiply using at
}
```Encapsulation is clearly enhanced here because the multiply() function can never be dependent on anything but public members of IMatrix.  If the class is changed later, nothing will affect multiply unless the definition of at() is changed.  Yet, I could still have two implementations of IMatrix2D: one that used an array and one that used a linked list.

So encapsulation is unquestionably improved: I'm only dependent on a smaller set of class members (jsut the public ones).

---

### Post by hod139 on 2006-06-21
[quote=Harleen]
To improve speed, you could use pointers instead of  data_[dataLoc++].
And instead of 
```
dataLoc = nCol_*r;
``` you can write 
```
dataLoc += nCol_;
``` This May improve speed, as you are no longer accessing the variable r and replace the multiplication with an addition.[/quote] 
Thanks for the suggestions.  I'm not sure how I missed the dataLoc += nCol_ improvement.  Is this example more of what you had in mind?
```

Matrix<T> operator*(const Matrix<T>& rhs) const{
    assert(nCol_ == rhs.size1() );
    const size_t rhs_size2 = rhs.size2(); 
    Matrix<T> theMatrix(nRow_, rhs_size2); 
    size_t dataOffset = 0;  
    T *val; // Pointer to data_ array starting at correct offset.
    for (int r=0; r < nRow_; ++r) {
       for (int c=0 ; c < rhs_size2; ++c) {
          T& x = theMatrix(r, c);
          val = &data_[dataOffset];  
          for (int i=0; i < nCol_; ++i) {
           x += (*val++) * rhs(i,c);
         }
      }
      dataOffset += nCol_;
   }
   return theMatrix;
}

``` 
Note: For performance reasons suggested by Harleen I am now using a private internal member variable, so unless I want to allow an accessor that returns a pointer the data_ array, this method must remain a class method.  So we no longer have to worry about non-member non-friend versus member 8)

---

### Post by StickGuy on 2006-06-21
[QUOTE=LordHunter317]I wasn't clear.  Area shouldn't be non-friend, non-member because it is dependent on a *unstated* semantic property of the class.
[/QUOTE]
I fail to see how this differs from matrix multiplication.  In order to perform it correctly, one must have knowledge about what a matrix is and therefore its internal structure as well.

[QUOTE=LordHunter317]Right and you if you have both, you've broken the duplication rule.  You don't do that.
[/QUOTE]
Once again, I never implied there was duplication.  I merely stated that, from a programmer's perspective, there is no difference (in terms of functionality) between either interface choice (members or non-members).

[QUOTE=LordHunter317]No, wrong, here's a simple example:
```
class IMatrix2D {
public:
    virtual void at(int row, int col) = 0 const;
}

IMatrix2D*
multiply(const IMatrix2D& lhs, const IMatrix2D rhs) {
    // Do multiply using at
}
```
Encapsulation is clearly enhanced here because the multiply() function can never be dependent on anything but public members of IMatrix.  If the class is changed later, nothing will affect multiply unless the definition of at() is changed.  Yet, I could still have two implementations of IMatrix2D: one that used an array and one that used a linked list.

So encapsulation is unquestionably improved: I'm only dependent on a smaller set of class members (jsut the public ones).[/quote]
```

class IMatrix2D {
public:
    virtual void at(int row, int col) = 0 const;
    IMatrix2D* multiply(const IMatrix2D& rhs) const {
        // Do multiply using at
    }
};

```
This code has exactly the same guarantees (albeit not compiler verified) and exactly the same encapsulation as your code.  Therefore, encapsulation is not "clearly enhanced".  You seem to want data encapsulation to mean hiding class data from the programmer(s) designing/coding/maintaining a particular class.  However, the classical definition relates to hiding class data from programmer(s) working with instances of the class.

I think that this debate is essentially a difference of opinion on what defines an external utility/helper method for a class.

---

### Post by LordHunter317 on 2006-06-21
[QUOTE=StickGuy]I fail to see how this differs from matrix multiplication.[/quote]Because the algorithm for computing the product of two matricies is identical if I have can access every entry in the matrix via some function call.  This is true regardless of how the matrix actually stores it's data in memory.

The algorithm for computing the area of the shape is not the same, I must also know the type of shape in order to compute the area.

The difference here is that the algorithm for doign matrix multiplication is not dependent on type.  In your example, the algorithm for doing area computation was dependent on type. 

 > In order to perform it correctly, one must have knowledge about what a matrix is and therefore its internal structure as well.You're only correct about the former.  I need to know nothing about the internal structure.

If this were true, then how do the STL algorithms work on vectors, lists, sets, and maps?  Clearly, they cannot know anything about the internal structure because all of those have radically different internals yet they do exactly what you claim is impossible.


> Once again, I never implied there was duplication.Yes, you did:> I'm not sure that your suggestions leads to better data encapsulation. **From a programmer's perspective, both member functions and these external functions present, effectively, the same interface to the data.**(emphasis mine).  My whole point is that if oyu're in this situation, you already likely made a mistake.  So if you're making that statement, it means you *already did something wrong.*


> I merely stated that, from a programmer's perspective, there is no difference (in terms of functionality) between either interface choice (members or non-members).From a class user's prospective, perhaps (even that's not completely true when templates are involved).   But not from the class designer's prospective at all.  Non-friend, non-member functions have stronger type checking enforced by the compiler: the fact their dependent only on public data is enforced.  If they are member functions, that fact cannot be enforced.


[code]This code has exactly the same guarantee (albeit not compiler verified)[/quote]Which means it doesn't have the same guarantees.  What the compiler has enforced is worlds different from what is enforced by convention.

> and exactly the same encapsulation as your code.Nope, greater encapsulation because of the above.  The compiler is enforcing the rule now, not me.

> You seem to want data encapsulation to mean hiding class data from the programmer(s) designing/coding/maintaining a particular class.No, it means information hiding.  If I can write my functions such that they're dependent on details that I've already had to make public, then it behooves me to write them in such a way that the compiler enforces that rule.  This means that the coupling between that function and the class definition is less.  It means I'm promised that in no situation will I have to change the function definition unless I change the public class members in a breaking way.

That's a useful thing.

> However, the classical definition relates to hiding class data from programmer(s) working with instances of the class.That's actually not the classical defintion and it's a poor definition.  The compiler is clearly capable of more than that, so it's clearly inadequate. 

> I think that this debate is essentially a difference of opinion on what defines an external utility/helper method for a class.No, it's clearly a core one.  Your definition of encapsulation is fundamentally wrong.

---

### Post by hod139 on 2006-06-21
[SIZE=2]It seems like this thread has turned into a debate between information hiding versus encapsulation.  LordHunter seems to be using the two terms interchangeably, whereas StickGuy is attempting to draw a distinction (I apologize if my interpretation on your usage of the terms is incorrect).  

[Here]("http://www.javaworld.com/javaworld/jw-05-2001/jw-0518-encapsulation.html") is a decent article (albeit using Java not C++ but still about OOP) attempting to clarify the distinction between the two.  If you don't wish to read the whole thing, the following are some key statements:

[/SIZE]  [FONT=verdana, arial, helvetica][SIZE=2]Encapsulation refers to the bundling of data with the methods that operate on that data. Often that definition is misconstrued to mean that the data is somehow hidden.

[/SIZE][/FONT][SIZE=2][FONT=verdana, arial, helvetica]However, hiding data is not the full extent of information hiding. David Parnas first introduced the concept of information hiding around 1972. He argued that the primary criteria for system modularization should concern the hiding of critical design decisions. He stressed hiding "difficult design decisions or design decisions which are likely to change." Hiding information in that manner isolates clients from requiring intimate knowledge of the design to use a module, and from the effects of changing those decisions.

[/FONT][FONT=verdana, arial, helvetica] Encapsulation is a language construct that facilitates the bundling of data with the methods operating on that data. Information hiding is a design principle that strives to shield client classes from the internal workings of a class. Encapsulation facilitates, but does not guarantee, information hiding. Smearing the two into one concept prevents a clear understanding of either.[/FONT][/SIZE]

---

### Post by Harleen on 2006-06-21
[QUOTE=hod139]Thanks for the suggestions.  I'm not sure how I missed the dataLoc += nCol_ improvement.  Is this example more of what you had in mind?[/QUOTE]
Yes. You can even drop dataOffset entirely and just go sequentially through your array.

**Edit**: after taking a closer look at the code, it's not that simple to drop dataOffset . So the following code won't work. Maybe with a second pointer.... So just ignore the following code.

```

Matrix<T> operator*(const Matrix<T>& rhs) const{
    assert(nCol_ == rhs.size1() );
    const size_t rhs_size2 = rhs.size2(); 
    Matrix<T> theMatrix(nRow_, rhs_size2); 
[COLOR="Red"]    // size_t dataOffset = 0;  
    // T *val; // Pointer to data_ array starting at correct offset.
    const T *val = data_; // Pointer to data_ array
[/COLOR]    for (int r=0; r < nRow_; ++r) {
       for (int c=0 ; c < rhs_size2; ++c) {
          T& x = theMatrix(r, c);
[COLOR="Red"]          // val = &data_[dataOffset];  [/COLOR]
          for (int i=0; i < nCol_; ++i) {
           x += (*val++) * rhs(i,c);
         }
      }
[COLOR="Red"]      // dataOffset += nCol_;
[/COLOR]   }
   return theMatrix;
}

``` 

But I'm really interested in the comparison between the for and while loop, when you apply this change to them. This change eleminates one of ther two additional operations I mentioned. The other one ( i = nCol_ -1; ) can be eleminated by defining a constant for (nCol_ -1) and then assingning that constant to i.

P.S.: Sorry about becoming On-Topic again. :smile:

---

### Post by LordHunter317 on 2006-06-21
[QUOTE=hod139]LordHunter seems to be using the two terms interchangeably,[/quote]That's because they're synonymous.

> [FONT=verdana, arial, helvetica][SIZE=2]Encapsulation refers to the bundling of data with the methods that operate on that data. Often that definition is misconstrued to mean that the data is somehow hidden.Yet this is clearly a poor definition because it is meaningless.  By that definition, any class or any function taking parameters is encapsulated at the right scope.

Clearly, that's not a sufficent definition.  Making encapsulation being synonymous with grouping hasn't gained us anything.

More importnatly, as soon as you define it as a language construct, you include non-friend, non-member functions.  So I'm still correct, because they're a method for encapsulation. 

So his definition, that encapsulation is a language feature is clearly bunk, becuase it fails to also make any distinctions.  Again, any class or function taking parmeters is encapsulated.

So clearly, we're only left with the defintions being the same.  His article is based on a fundamental fallacy anyway: that since Java is OOP all code written in Java is OOP.  The former isn't completely true and the latter certainly is true, so his article is bunk anyway.

---

### Post by hod139 on 2006-06-21
> **LordHunter317]That's because they're synonymous.
[/quote] Oh really...
[http://nat.truemesh.com/archives/000498.html]("http://nat.truemesh.com/archives/000498.html")
[http://en.wikipedia.org/wiki/Information_hiding]("http://en.wikipedia.org/wiki/Information_hiding")
[http://discuss.joelonsoftware.com/default.asp?design.4.145438.37]("http://discuss.joelonsoftware.com/default.asp?design.4.145438.37")
[http://www.toa.com/pub/abstraction.txt]("http://www.toa.com/pub/abstraction.txt")
[http://www.roseindia.net/software-tutorials/detail/2941]("http://www.roseindia.net/software-tutorials/detail/2941")

Now, I don't expect you to read these articles (I only glanced) said:**
> Information hiding lets one build higher level abstractions on top of lower level details. Good information hiding lets one ignore details of the system that are unrelated to the task at hand.
  Encapsulation ensures that there are no unexpected dependencies between conceptualy unrelated parts of the system. Good encapsulation lets one easily predict how a change to one object will, or will not, impact on other parts of the system. 
Now, I'm still trying to sort out the distinctions myself, but after doing some googling statements such as:
[quote=LordHunter317]
Your definition of encapsulation is fundamentally wrong.
[/quote] > 
Yet this is clearly a poor definition because it is meaningless.
 > 
That's because they're synonymous.
 
appear to be more personal opinion rather than fact.

Instead of random google hits, we can always try an appeal to authority. [According to Stroustrup]("http://www.research.att.com/%7Ebs/glossary.html"):
**information hiding** -   placing information where it can be accessed only through a well-defined interface[B]
encapsulation[/B] -      the enforcement of abstraction by mechanisms that prevent access to implementation details of an object or a group of objects except through a well-defined interface.  C++ enforces encapsulation of private and proteced members of a class as long as users do not violate the type system using casts.

Except I don't think that clarifies anything and leaves the debate open#-o

---

### Post by LordHunter317 on 2006-06-21
> **hod139]Now, I don't expect you to read these articles (I only glanced) said:**
> And if their definitions are like the Javaworld one, then they're wrong for the same reasons.  You need to make a meaingful distinction, he failed to do so. 

> The first article I linked sums it up pretty nice:Which gives different terms to both of them.  And it clearly defines encapsulation as a form of information hiding, because reducing dependencies is hiding information.

It leaves room for more generalized information hiding, which I suppose I could accept, except that I believe it could be shown that all information hiding in code is dependency reduction.  Which would make the statements equivocial.

[quote]Except I don't think that clarifies anything and leaves the debate open#-oThe definition clearly includes non-friend, non-member functions as part of the interface.  Stroustrup is clearly talking about more than just public class members.

---

### Post by hod139 on 2006-06-22
[quote=Harleen]
But I'm really interested in the comparison between the for and while loop, when you apply this change to them. [/quote] 
Sorry for taking so long to make the changes and post an update.  Anyways, I made the changes to the multiply methods and also attempted to eliminate any caching/paging optimizations by declaring 2 new matrices before each multiply and deleting them afterwards.  

The 2 versions of the matrix multiply now look like:
```

Matrix<T> mult_FOR(const Matrix<T>& rhs) const{
    assert(nCol_ == rhs.size1() );    
    const size_t rhs_size2 = rhs.size2(); 
    Matrix<T> theMatrix(nRow_, rhs_size2); 
    size_t dataOffset = 0;  
    T *val;
    for (int r=0; r < nRow_; ++r) {
       for (int c=0 ; c < rhs_size2; ++c) {
          T& x = theMatrix(r, c);
          val = &data_[dataOffset];  
          for (int i=0; i < nCol_; ++i) {
           x += (*val++) * rhs(i,c);
         }
      }
      dataOffset += nCol_;
   }
   return theMatrix;
}

Matrix<T> mult_WHILE(const Matrix<T>& rhs) const{
    assert(nCol_ == rhs.size1() );
    size_t rhs_size2 = rhs.size2();
    Matrix<T> theMatrix(nRow_, rhs_size2);
    T *val;   
    int r, c, i;
    r = nRow_ -1;
    int dataOffset = nCol_*r + nCol_ -1;  
    do{
      c = rhs_size2 -1;
      do{
         T& x = theMatrix(r, c);
         val = &data_[dataOffset];  
         i = nCol_ -1;
         do{    
            x += (*val--) * rhs(i,c);
            --i;
         } while(i >= 0);
      --c;
      } while (c >= 0);
      dataOffset -= nCol_;
      --r;
    } while(r >=0);
    return theMatrix;
}

``` 
The for loop doing the timing/testing looks like this now:
```

for(int i = 0; i < N; ++i){
   Matrix<double> *M1 = new Matrix<double>(n1, n2);
   Matrix<double> *M2 = new Matrix<double>(n2, n3);  
   start = clock();
   M1->mult_WHILE(*M2);
   finish = clock();
   time = ((double)(finish - start))/CLOCKS_PER_SEC;
   ave_time_WHILE += time;
   delete M1;
   delete M2;
   
   Matrix<double> *M3 = new Matrix<double>(n1, n2);
   Matrix<double> *M4 = new Matrix<double>(n2, n3);    
   start = clock();
   M3->mult_FOR(*M4);
   finish = clock();
   time = ((double)(finish - start))/CLOCKS_PER_SEC;
   ave_time_FOR += time;
   delete M3;
   delete M4;
}

``` The newing and deleting seems to remove the speed ups from caching and paging, and now the methods appear to run about the same.

And for the results:
```

 ./a.out
Average time for mult_WHILE (seconds): 1.4265
Average time for mult_FOR (seconds): 1.384

``` 
Or, if you feel like bigger matrices and waiting forever for a result:
```

Average time for mult_WHILE (seconds): 10.272
Average time for mult_FOR (seconds): 10.2855

``` 
In either case, it seems without the performance boosts from the caching, both methods appear to take just as long now.  The entire code is attached here:[ATTACH]11665[/ATTACH]

---

