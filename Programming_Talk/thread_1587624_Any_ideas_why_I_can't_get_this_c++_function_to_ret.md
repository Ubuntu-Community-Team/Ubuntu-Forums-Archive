---
title: "Any ideas why I can't get this c++ function to return a value"
date: 2010-10-03
forum: Programming Talk
---

### Post by SavantStrike on 2010-10-03
EDIT: edited to add entire source code and not just part of it. 

I'm almost done with a program I need to write for class, and it runs (and does everything it's expected to do), but I'm scratching my head as to *why* it runs because one of the functions cannot return a value (compiler error if I try to make it return a value), yet it works.

I wrote a non templated version of the same program and the same class, and I can return *this just fine. But this problem required I do the same thing with a template.

returning *this in the overloaded= operator function causes the following error:
```

driver.cc: In member function &#8216;const T& myList<T>::operator=(const myList<T>&) [with T = int]&#8217;:
driver.cc:110:   instantiated from here
driver.cc:95: error: invalid initialization of reference of type &#8216;const int&&#8217; from expression of type &#8216;myList<int>&#8217;

```

```

#include <iostream>
using std::cout;
using std::endl;
using std::string; //needed to handle non integer types
#ifndef TmyList_h
#define TmyList_h

template<class T> class myList
{
public:
	myList();	//default constructor
	void printall();
	template<class TT> //needed to overload +
	//the + operator is not a member of the myList class because it is a friend
	//therefore, a second template is needed, the previously defined template <class TT>
	friend myList<TT> &operator+(myList<TT> &, const TT &);
	const T &operator=(const myList &);
	int &operator[](int);
	~myList(); //destructor
private:
	int size;//integer to control size or array
	T *ptr;	//pointer to array
};

template<class T>
myList<T>::myList(){
	size = 0; //setting left variable to zero means array will have zero elements
	ptr = NULL; //set ptr to null because the array is empty
}

template<class T>
void myList<T>::printall(){
		int counter = 0; //temporary counter used for printing the elements of the array referenced by ptr
		while (counter < size){ // loop which runs from 0 to j where j is the last element of the array referenced by ptr
			//and n is the element of the array at the position "counter"
			cout << *(ptr + counter) << " ";//print out the value of array[n]
			counter++; //increment counter to the next position in the array
		}//all of the elements in the array that ptr references have been printed to the screen
		cout << endl;
}

template<class T>
myList<T> &operator+(myList<T> &left, const T &right){
	if (left.ptr == NULL){
		left.size = left.size + 1;
		left.ptr = new T[left.size];
		left.ptr[(left.size - 1)] = right;
		return left;
	}
	else{
		int *tmpArray = new T[left.size]; //create a new array for deep copy operation

		//deep copy values in pointer to tmpPointer
		for(int i=0; i<(left.size); i++){
		tmpArray[i] = *(left.ptr + i);
		}

		delete [] left.ptr; //deallocate ptr

		left.size++; //a new array will be created with one extra element

		//reallocate pointer to point to a larger array
		left.ptr = new T[left.size];

		//deep copy tmpArray into the array referenced by ptr
		for(int i=0; i<(left.size-1); i++){//stop at one less than the new size, as tmpArray is one element smaller than the array referenced by ptr
			left.ptr[i] = tmpArray[i];
		}

		left.ptr[(left.size-1)] = right; //add the last element to the array referenced by ptr

		delete[] tmpArray; //deallocate tmpArray

		return left;
	}
}

template <class T>
int &myList<T>::operator[](int index){
	return ptr[index];
}

template <class T>
const T &myList<T>::operator=(const myList &right){
		if(&right !=this){ //check for self assignment
			if (size != right.size){ //then the array in the list on the left of the = operator must be expanded
				delete [] ptr;	//delete original array in memory
				size = right.size; //increment size by 1
				ptr = new int[size]; //create a new array one unit larger
			}
			for (int i=0; i<size; i++){
				ptr[i]=right.ptr[i]; //set each element [n] in the array in the left hand object to the value at [n] in right hand object
			}
		}
		return *this; //this line causes the error
}

template<class T>
myList<T>::~myList(){
	size = 0;
	delete [] ptr;
}

#endif

int main ()
{
myList<int> a;
a.printall();
a= a + 10;
a= a + 5;
a.printall();
a[0]=a[1];
a.printall();
return 0;
}

```


Any help would be appreciated as I'm still not sure I've 100 percent grasped what I did with this code... I understood it better without forcing it into a template. 

It would also be nice to hand it in without a comment stating I can't return *this like I'm supposed to :P.

TIA

---

### Post by GeneralZod on 2010-10-04
The code you've given compiles fine here if I 

return *this; 

at the end of the implementation of operator=.

In future, please:

- Actually tell us the compiler error; and
- Post a full source file that someone can just paste into a text file and immediately reproduce the error you're getting.

Thankyou :)

Anyway, the main problem is that you are attempting to return const T&, rather than const myList<T> &.

Edit:

Why is the friend declaration bolded?

---

### Post by SavantStrike on 2010-10-04
I figured no one would want to look at all of the other code. I didn't think about someone actually compiling the whole shebang.

The bold is just so it's legible after all of the comments, as it's the offending funciton.

I'll edit my original post to include all of the source code. 

The error was as follows:
```

driver.cc: In member function &#8216;const T& myList<T>::operator=(const myList<T>&) [with T = int]&#8217;:
driver.cc:110:   instantiated from here
driver.cc:95: error: invalid initialization of reference of type &#8216;const int&&#8217; from expression of type &#8216;myList<int>&#8217;

```

Edit: yeah, I'm lost more than ever now.

Looking at the code as a whole, it almost looks like the = operator is being evaluated before the + operator in main? I didn't think that could happen. Honestly I (mostly) understood what I was doing until I forced this into a template, then it got iffy. The template hasn't even fulfilled it's true purpose as I can't pass this thing strings without it going nuts (which should be possible as a myList<string> class should be a possibility with the template).

I'm messing up my syntax somewhere.

---

### Post by SavantStrike on 2010-10-04
I think I may have just solved it!

Much thanks. The return type was a huge clue. 

changing 
```

const T &operator=(const myList &);

```

to
```

const T &operator=(const T &);

```

Changes the return type, and *this works.

While I'm at it, when I declared template <TT> for the overloaded + function, did I do the right thing there, or is there a better way to do that? I want to learn this rather than just scrape by :).

---

### Post by GeneralZod on 2010-10-04
> **SavantStrike said:**
> 
While I'm at it, when I declared template <TT> for the overloaded + function, did I do the right thing there, or is there a better way to do that? I want to learn this rather than just scrape by :).

What you did is probably too "strong" (I think it may grant friendship to more template variants of myList than you should) : check out 

[http://www.devx.com/cplus/10MinuteSolution/30302/1954](http://www.devx.com/cplus/10MinuteSolution/30302/1954)

It's more convoluted, but closer to what you actually want to express.

---

### Post by dwhitney67 on 2010-10-04
> **SavantStrike said:**
> I think I may have just solved it!


Can you please provide a description of what these two methods are intended for?
```

template<class TT>
friend myList<TT> &operator+(myList<TT> &, const TT &);

const T &operator=(const myList &);

```
I realize there are syntax errors above, thus what I am asking for has nothing to do with this or with the actual implementation.  I am merely trying to ascertain if you have a requirement, and if so, what is it.

For example, is the purpose of the first method to add an item to an existing list, or is the purpose to create a new list, containing the items from an existing list plus the new item?

P.S.  Please consider using the <return> key more often when you code.  There's nothing more unpleasant than attempting to read code that is scrunched together; some line separation would do a world of wonder.

---

### Post by SavantStrike on 2010-10-04
> **dwhitney67 said:**
> Can you please provide a description of what these two methods are intended for?
```

template<class TT>
friend myList<TT> &operator+(myList<TT> &, const TT &);

const T &operator=(const myList &);

```
I realize there are syntax errors above, thus what I am asking for has nothing to do with this or with the actual implementation.  I am merely trying to ascertain if you have a requirement, and if so, what is it.

For example, is the purpose of the first method to add an item to an existing list, or is the purpose to create a new list, containing the items from an existing list plus the new item?

P.S.  Please consider using the <return> key more often when you code.  There's nothing more unpleasant than attempting to read code that is scrunched together; some line separation would do a world of wonder.


The syntax may be wrong, but the program compiles and does what was required with the int main() the prof gave us. I'm definitely going to spend more time on this tomorrow, but today I can hand it in and study for a test in another class :P.

And you're right, my code is pretty hard on the eyes. I should work on that.

As for the requirements, the prof seems to give us room to do whatever we want as long as the main() function provided works with our code.

The first method is simply to add a new element to an existing list, only I believe the prof wants us to do a deep copy and resize the list. Overkill as there are only two adds to the list.

If we were adding 50 items, this would be a huge performance hit as it would mean way too many deep copies. As it stands, I figure I've demonstrated I understood what he was talking about rather than just statically creating an array 2 elements deep (which is all I really needed).

The second method is to return an lvalue from an object=object pair.

---

### Post by dwhitney67 on 2010-10-04
> **SavantStrike said:**
> 
As for the requirements, the prof seems to give us room to do whatever we want as long as the main() function provided works with our code.

I saw the main() program; I did not realize it was provided by the professor.  I'm surprised that you were not asked to implement the operator+=() method.  It would seem more logical than to merely do the operator+().

> **SavantStrike said:**
> 
The first method is simply to add a new element to an existing list, only I believe the prof wants us to do a deep copy and resize the list. Overkill as there are only two adds to the list.

It's not overkill; it merely to augment your knowledge on how to do things.

> **SavantStrike said:**
> 
If we were adding 50 items, this would be a huge performance hit as it would mean way too many deep copies. As it stands, I figure I've demonstrated I understood what he was talking about rather than just statically creating an array 2 elements deep (which is all I really needed).

The deep-copies will occur if you define your template type as a non-pointer (ie concrete) object type.  As for the allocations, you could always declare a suitably sized pool of space, and then re-adjust this as needed.

> **SavantStrike said:**
> 
The second method is to return an lvalue from an object=object pair.
I asked the question earlier because it seemed to me that both methods (the friend one and the second) were not required to accomplish your task.

---

