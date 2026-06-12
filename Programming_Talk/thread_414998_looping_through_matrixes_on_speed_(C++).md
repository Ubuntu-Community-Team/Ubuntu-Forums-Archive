---
title: "looping through matrixes on speed (C++)"
date: 2007-04-20
forum: Programming Talk
---

### Post by susscorfa on 2007-04-20
hi i have a project for which i need to loop though matrixes very often so i want to do it as quickly as possible.  so i decided to do a speed compairison between different option and i was quite amazed by the outcome. i used the folowing code and compaired the speed using kachegrind


```
#include <iostream>
#include <cstdlib>
#include <boost/numeric/ublas/matrix.hpp>
#include <vector>


void function ()
{
	boost::numeric::ublas::matrix<double> x;
	x.resize(30,30);
	for(int f=0; f!=10;++f){
	boost::numeric::ublas::matrix<double> ::iterator1 it1 ;
	boost::numeric::ublas::matrix<double> ::iterator1 it1_end (x.end1 ());
	for(it1=x.begin1(); it1!=it1_end; ++it1)
	 {
		boost::numeric::ublas::matrix<double> ::iterator2 it2;
		boost::numeric::ublas::matrix<double> ::iterator2 it2_end (it1.end ());
		for(it2=it1.begin(); it2!=it2_end; ++it2)
		{
			(*it2)+=2.2;
			
		}
		
	}}
}

void function2 ()
{
	boost::numeric::ublas::matrix<double> l;
	l.resize(30,30);
	for(int f=0; f!=10;++f){
				
		for(int j=0; j!=30; ++j){for(int i=0; i!=30; ++i)
		{
			l(i,j)+=2.2;
					
		}}}
}

void function3()
{
	std::vector<std::vector<double> > track_env (30, std::vector<double>(30, 0));
	for(int f=0; f!=10;++f){
	std::vector<std::vector<double> >::iterator iter;
	std::vector<std::vector<double> >::iterator y = track_env.end();
	for(iter = track_env.begin(); iter != y; ++iter)
	{
		std::vector<double> ::iterator iter2;
		std::vector<double> ::iterator x = (*iter).end();
		for(iter2 = (*iter).begin(); iter2 != x; ++iter2)	
		{
			(*iter2)+=2.2;
			
		}
	}}
}

using namespace std;

int main()
{
  function();function3();function2();


}
```


the program spents 80% of the time in function() 12% in function2() and 8 in function3()

this amazes me that looping through a matrix with iterators is that slow am i doing something wrong? has anyone better sugestions or should i just switch to use vectors?

---

### Post by WebDrake on 2007-04-20
> **susscorfa said:**
> hi i have a project for which i need to loop though matrixes very often so i want to do it as quickly as possible.  so i decided to do a speed compairison between different option and i was quite amazed by the outcome. i used the folowing code and compaired the speed using kachegrind

the program spents 80% of the time in function() 12% in function2() and 8 in function3()

this amazes me that looping through a matrix with iterators is that slow am i doing something wrong? has anyone better sugestions or should i just switch to use vectors?

In my (rather limited) experience, the more complicated the object you are dealing with, the slower it is.  Matrix and vector objects are both slow compared to ordinary arrays.  You have to decide for yourself whether the object properties of the matrix/vector are more useful than the speed you could get by using the plain array.  This is why I tend to use plain C for number-crunching work. :-)

The discrepancy in speeds is probably not due to the actual speed of the loop but due to the time needed to assign memory for the iterators.  function() in particular will be slow because your iterators are relatively complicated objects that take up larger amounts of memory.  By contrast in function2() you're only having to assign integers which are much smaller and faster.  It might be interesting to add a function4() that uses integers as the iterated variables, just to see if that can cut the performance even more (it might well do).

As a further exercise, try writing a plain array code that would be valid in C as well as C++ and see how that goes.  Probably faster still. :-)

I also wonder if the declaration of variables *inside* the loops might have something to do with it.  I seem to remember taking the declaration outside of the loop speeded things up.  Try taking all declarations outside the loops and seeing if that helps.

---

### Post by hod139 on 2007-04-20
In addition to removing the declarations outside the loop, you also should also enable release mode, which will use expression templates and significantly improve performance.  See the FAQs on the ublas documentation: [http://www.boost.org/libs/numeric/ublas/doc/index.htm](http://www.boost.org/libs/numeric/ublas/doc/index.htm)

Basically, try:
```

using boost::numeric::ublas::matrix;

void function5()
{
    matrix<double> x(30,30);

    matrix<double>::iterator1 it1;
    matrix<double>::iterator1 it1_end (x.end1());
    matrix<double> ::iterator2 it2;
    matrix<double>::iterator2 it2_end;
    
    for(int f=0; f!=10;++f){
       for(it1=x.begin1(); it1!=it1_end; ++it1)
       {    
            it2_end = it1.end();    
            for(it2=it1.begin(); it2!=it2_end; ++it2)
            {
               (*it2)+=2.2;
            }
       }
    }
}

```

and compile as
```

g++ -O2 -DNDEBUG matrix.cpp -o release

```

---

### Post by susscorfa on 2007-04-23
Ok  thanks very much for the reply's, they allready helped me a lot

i tryed function5() and compiling with a higher optimalization level and it turns out that virtually all speed differences disappear at least when i compile from cmd line and that the iterator with vectors and matrixes are about the same speed


The option from Webdrake to go for plain C i will maybe try later on but i'm still improving my c++ so i will stay in that for a while

WebDrake the option in going for function4() sounds very intressting but i do not completely understand how this should be build. can you give a small example. 

thanks any way

---

### Post by WebDrake on 2007-04-23
> **susscorfa said:**
> WebDrake the option in going for function4() sounds very intressting but i do not completely understand how this should be build. can you give a small example.

Well, I was just noting the difference between your function() and function2() -- that in the first you use iterators in the for loops and in the second just integer variables.  I was wondering why you didn't make an analogous variation on function3().  So whereas function3() is given as,

```

void function3()
{
	std::vector<std::vector<double> > track_env (30, std::vector<double>(30, 0));
	for(int f=0; f!=10;++f) {
		std::vector<std::vector<double> >::iterator iter;
		std::vector<std::vector<double> >::iterator y = track_env.end();
		for(iter = track_env.begin(); iter != y; ++iter) {
			std::vector<double> ::iterator iter2;
			std::vector<double> ::iterator x = (*iter).end();
			for(iter2 = (*iter).begin(); iter2 != x; ++iter2) {
				(*iter2)+=2.2;
			}
		}
	}
}

```

function4() would be,

```

void function4()
{
	int i, j, f;
	std::vector<std::vector<double> > track_env (30, std::vector<double>(30, 0));
	for(f=0; f!=10;++f) {
		for(i = 0; i != 30; ++i) {
			for(j = 0; j != 30; ++j) {
				track_env[i][j] += 2.2;			
			}
		}
	}
}

```

See? :-)

Try it out and see if it works.

---

### Post by susscorfa on 2007-04-24
Ok it turns out that function 2 is the quickest with virtualy no difference to function 4 (2% more). I learned that iterators are quicker but in this test they turn out not to be quicker.

---

### Post by WebDrake on 2007-04-24
> **susscorfa said:**
> Ok it turns out that function 2 is the quickest with virtualy no difference to function 4 (2% more). I learned that iterators are quicker but in this test they turn out not to be quicker.

My guess is it's a memory allocation thing.  You are looping through only a very small matrix, so any speed bonus you get from using the iterators is wiped out by the time required to create them when the function starts.

Try doing it with a 1000x1000 matrix (or a 10000x10000 if you're feeling brave...) and you might see the speed improvement you were told about.  Let us know about your results, I'd be interested to find out.

Also, your results are probably being biased by the fact that you declare and allocate the matrix inside the looping function.  Try allocating all the matrices (whether they are the actual matrix class or vectors or whatever) in a different place and passing them to your looping functions as pointers.  Then you will probably see the real speed difference better.

---

### Post by susscorfa on 2007-04-26
> **WebDrake said:**
> 

Try doing it with a 1000x1000 matrix (or a 10000x10000 if you're feeling brave...) and you might see the speed improvement you were told about.  Let us know about your results, I'd be interested to find out.


well i dared to go upto  3000X3000 compaired to 30 *30

and for vectors the speed difference completly disapears and matrixes are still slower with iterators as the slowest

for people intressed i attached the test file again (as txt)
i test by the following cmd line arguments
```

$ g++ -DNDEBUG -O3 speed.cpp -o test
$ valgrind --tool=callgrind ./test
$ kcachegrind callgrind.out.*

```

btw i tryed taking out the declarations but then kcachegrind does not make a distinction between the functions anymore

---

### Post by WebDrake on 2007-04-28
I note you're still declaring the matrix iterators within one of the for loops .... take them outside and check! ;-)

Other than that, I don't know.  It might just be the boost matrix class isn't as effective in its implementation as the standard vector class.

I'm not familiar with the debug/profiling tools you're using so can't really advise you further.  I did try looking at your code with gprof earlier in the week but it didn't give me a function-by-function report either.  In fact the allocation statements were listed first....

How did you go about taking the memory allocations outside the individual functions?  I would declare your matrixes and vectors in main() and pass pointers to the individual functions.

Anyway, good luck and don't sweat the small stuff too much.

---

