---
title: "error: invalid use of template-name ‘std::vector’ without an argument list"
date: 2011-09-27
forum: Programming Talk
---

### Post by linuxfreak003 on 2011-09-27
Hey I've been trying for a little bit to get this program of mine working. It simply prints all of the prime numbers up to a certain number. After trying google for a bit I decided to see if anyone could help me here. The code is:
```
#include <iostream>
#include <math.h>
#include <vector>
using namespace std;


vector checkprimes(vector<long> primelist,long test)
{
	long i = 0;
	while (1)
	{
		float FloatTest = float test/primelist[i];
		long IntTest = long (test/primelist[i]);
		if (FloatTest == IntTest)
			break;
		else if primelist[i] > sqrt(test)
		{
			primelist->push_back(test);
			break;
		else
			continue;
		i+=1;
	return primelist;
	}
}
/*print primes*/
void printprimes(long cap)
{
	vector<long> primes(1, 2);
	i = 3;
	while ((int)primes.size() <= cap)
	{
		primes = checkprimes(primes, i);
		i+=2;
	}
	cout << primes << endl;
	cout << "These are the first " << cap << " primes.\n";
}

int main()
{
	long cap;
	cout<< "How high?" << endl;
	cin >> cap;
	printprimes(cap);
}
```
When I try to compile it gives me the following error.
```
primefinder.cpp:7: error: invalid use of template-name &#8216;std::vector&#8217; without an argument list
```
I have the same program in python and it works fine.. I'm a little new to c++ though(and programming for that matter). So some help would be nice.
Thanks to anyone in advance..

---

### Post by karlson on 2011-09-27
> **linuxfreak003 said:**
> The code is:
```
vector checkprimes(vector<long> primelist,long test)

```


What exactly is your return type?

---

### Post by linuxfreak003 on 2011-09-28
The return type would be a vector, I believe.. I'm trying to add the integer test to the the vector primelist. then return it back to be able to use it again..

---

### Post by dazman19 on 2011-09-28
```


template <class T=long> //You should create the template class Vector with a default type long in your case.
class Vector {
public:
	//some constructors blah blah blah 
	Vector(); //default constructor                        
	explicit Vector( long num );  //prevent type conversion using explcit     
	Vector( const Vector<T>& vec ); //copy constructor
	~Vector() { delete [] array; } //destructor
	//some more stuff. .. 
private:
        //some var data you may want to use.
	int capacity;
	int size;
	T *array;
};


template <class T>  
T Vector<T>::getVec(int a) const { //note must be signed as const
	return array[a];
} //get item at position a

template <class T>  
void Vector<T>::setVec(int a, const T& value) {
	array[a] = value;
} //set item at position a

```

So you might want to use a template. or give a return type. in your case i think you are returning a vector<long>?
EDIT:
What you could do is change the vector that was there by passing a reference: 
void checkprimes(vector<long> &primelist, int noOfItemsInPrimelist ,long test )

then when you are working with primelist inside your function you know it is accessing a piece of data in the address you have given it. you know how big this data is, because you know its a vector of type long and you know the size of it. This is a different way of returning data from a function, rather than using its traditional return type. Its used to change data that is located in heap memory.

---

### Post by PaulM1985 on 2011-09-28
> **dazman19 said:**
> ```


template <class T=long> //You should create the template class Vector with a default type long in your case.
class Vector {
public:
	//some constructors blah blah blah 
	Vector(); //default constructor                        
	explicit Vector( long num );  //prevent type conversion using explcit     
	Vector( const Vector<T>& vec ); //copy constructor
	~Vector() { delete [] array; } //destructor
	//some more stuff. .. 
private:
        //some var data you may want to use.
	int capacity;
	int size;
	T *array;
};


template <class T>  
T Vector<T>::getVec(int a) const { //note must be signed as const
	return array[a];
} //get item at position a

template <class T>  
void Vector<T>::setVec(int a, const T& value) {
	array[a] = value;
} //set item at position a

```

So you might want to use a template. or give a return type. in your case i think you are returning a vector<long>?
EDIT:
What you could do is change the vector that was there by passing a reference: 
void checkprimes(vector<long> &primelist, int noOfItemsInPrimelist ,long test )

then when you are working with primelist inside your function you know it is accessing a piece of data in the address you have given it. you know how big this data is, because you know its a vector of type long and you know the size of it. This is a different way of returning data from a function, rather than using its traditional return type. Its used to change data that is located in heap memory.

Are you saying to create a custom vector class instead of simply set vector<long> to be the return type of the function checkPrimes?

Paul

---

### Post by karlson on 2011-09-28
> **linuxfreak003 said:**
> The return type would be a vector, I believe.. I'm trying to add the integer test to the the vector primelist. then return it back to be able to use it again..

std::vector is a container of elements of some type.  If you are passing std::vector<long> you need to return it in the same fashion.

And further you might want to pass the parameters in by reference unless you want C++ creating copies of it during the call.

---

### Post by linuxfreak003 on 2011-09-28
> std::vector is a container of elements of some type. If you are passing std::vector<long> you need to return it in the same fashion.

And further you might want to pass the parameters in by reference unless you want C++ creating copies of it during the call.
Perfect. That at least sounds exactly what I am looking for. I will be testing it soon. hopefully this morning if my laptop doesn't die on me.

---

### Post by linuxfreak003 on 2011-09-28
> So you might want to use a template. or give a return type. in your case i think you are returning a vector<long>?
EDIT:
What you could do is change the vector that was there by passing a reference: 
void checkprimes(vector<long> &primelist, int noOfItemsInPrimelist ,long test )
Yes I would be returning a vector<long>.. so does int noOfItemsInPrimelist need to be passed as a parameter? or can I still figure it out in the function even though it's the reference being passed? Not really a problem though.

---

### Post by linuxfreak003 on 2011-09-28
Ok, So I modified the code to this..
```
void checkprimes(vector<long> &primelist,long test)
 11 {
 12         long i = 0;
 13         while (1)
 14         {
 15                 float FloatTest;
 16                 float ftest = test;
 17                 long IntTest;
 18                 FloatTest = ftest/primelist[i];
 19                 IntTest = (test/primelist[i]);
 20                 if (FloatTest == IntTest)
 21                         break;
 22                 else if (primelist[i] > sqrt(test))
 23                 {
 24                         primelist.push_back(test);
 25                         break;
 26                 }
 27                 else
 28                         continue;
 29                 i+=1;
 30         return &primelist;
 31         }
 32 }

/*And this as well*/
void printprimes(long cap)
 35 {
 36         vector<long> primes(1, 2);
 37         int i = 3;
 38         while ((int)primes.size() <= cap)
 39         {
 40                 primes = checkprimes(primes, i);
 41                 i+=2;
 42         }
 43         for (int i = 0, i <(int) primes.size(), i++)
 44         {
 45         cout << primes << " ";
 46         }
 47         cout << "These are the first " << cap << " primes.\n";
 48 }


```
And this is what I get when I try to compile it...
```
primefinder.cpp: In function &#8216;void checkprimes(std::vector<long int, std::allocator<long int> >&, long int)&#8217;:
primefinder.cpp:30: error: return-statement with a value, in function returning 'void'
primefinder.cpp: In function &#8216;void printprimes(long int)&#8217;:
primefinder.cpp:40: error: no match for &#8216;operator=&#8217; in &#8216;primes = checkprimes(((std::vector<long int, std::allocator<long int> >&)(& primes)), ((long int)i))&#8217;
/usr/include/c++/4.4/bits/vector.tcc:156: note: candidates are: std::vector<_Tp, _Alloc>& std::vector<_Tp, _Alloc>::operator=(const std::vector<_Tp, _Alloc>&) [with _Tp = long int, _Alloc = std::allocator<long int>]
primefinder.cpp:43: error: expected initializer before &#8216;<&#8217; token
primefinder.cpp:48: error: expected primary-expression before &#8216;}&#8217; token
primefinder.cpp:48: error: expected &#8216;)&#8217; before &#8216;}&#8217; token
primefinder.cpp:48: error: expected primary-expression before &#8216;}&#8217; token
primefinder.cpp:48: error: expected &#8216;;&#8217; before &#8216;}&#8217; token

```
I think I might be missing some stuff. I'm not sure I understood how to pass the reference of primelist as a parameter, I also need to return the value at the end...

---

### Post by karlson on 2011-09-28
> **linuxfreak003 said:**
> 
```
primefinder.cpp: In function ‘void checkprimes(std::vector<long int, std::allocator<long int> >&, long int)’:
primefinder.cpp:30: error: return-statement with a value, in function returning 'void'

```
You are trying to return something from a function that is not supposed to return anything.  Don't do it.

> ```

primefinder.cpp: In function ‘void printprimes(long int)’:
primefinder.cpp:40: error: no match for ‘operator=’ in ‘primes = checkprimes(((std::vector<long int, std::allocator<long int> >&)(& primes)), ((long int)i))’
/usr/include/c++/4.4/bits/vector.tcc:156: note: candidates are: std::vector<_Tp, _Alloc>& std::vector<_Tp, _Alloc>::operator=(const std::vector<_Tp, _Alloc>&) [with _Tp = long int, _Alloc = std::allocator<long int>]
primefinder.cpp:43: error: expected initializer before ‘<’ token
primefinder.cpp:48: error: expected primary-expression before ‘}’ token
primefinder.cpp:48: error: expected ‘)’ before ‘}’ token
primefinder.cpp:48: error: expected primary-expression before ‘}’ token
primefinder.cpp:48: error: expected ‘;’ before ‘}’ token

```
I think I might be missing some stuff. I'm not sure I understood how to pass the reference of primelist as a parameter, I also need to return the value at the end...

You are:

1.  You assigning "void" to a vector, which doesn't make any sense.  
2.  Have you included <iostream> to use std::cout?
3.  Are you sure that operator<< is defined for a vector?
4.  Terms in for loop are separated by ; not ,

---

### Post by cgroza on 2011-09-28
You should have done like this:

```

vector<long> myfuncname(vector<long>)
{
....
return myvec;
}


```

You still have to give it the template arguments even if it is in the return type.

---

### Post by linuxfreak003 on 2011-09-29
Ok.. I didn't know you had to give it the template arguments in the return type.. Though I showed this to my teacher today and we figured out how to get it to work. pretty much I left the return type as void. and just passed the parameter reference(I didn't know, or just wasn't thinking that you don't have to return it when you pass the reference.) so when I call the function it looks like this:
```
void checkprimes(vector<long> &primelist, long test)
```
and at the end of the function I don't return any values.
another one of the problems was because I was using commas instead of semicolons in a for loop. Those two things i think pretty much fixed it. we continued to make it a little more efficient too. thanks for the help though. glad to finally have it working.

---

