---
title: "C++ OStream Problem"
date: 2008-07-30
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-07-30
At this [[COLOR="Blue"]_site_[/COLOR]]("http://www.codersource.net/cpp_stream_operators.html") I saw this example
[PHP]
ostream& operator <<(ostream &os,const Base &obj)
{
      os<<obj.strVal;
      return os;
}[/PHP]

I tried to copy it in my code

[PHP]template <class T>
class List {
	private:
		T * dat;
		void resize(int x) {
			T * tmp = new T[x];
			for (int i=0;i<length;i++) {
				tmp[i] = dat[i];
			}
			length = x;
			delete[] dat;
			dat = tmp;
		}
	public:
		int length;
		List() {
			dat = new T[1];
			length = 1;
		}
		List(int l) {
			dat = new T[l];
			length = l;
		}
		List(const List<T> & l) {
			length=l.length;
			dat = new T[length];
			for (int i=0;i<length;i++) dat[i] = l.dat[i];
		}
		~List() {
			delete[] dat;
		}
		void push(T x) {
			operator[](length) = x;
		}
		T& pop() {
			return operator[](length-1);
		}
		
		T& operator [] (int x) {
			if (x >= length) resize(x+1);
			return dat[x];
		}
		const List<T> operator + (List<T> & l0) {
			List<T> tmp (length+l0.length);
			
			for (int i0=0;i0<length;i0++) tmp[i0] = operator[](i0);
			for (int i1=0;i1<l0.length;i1++) tmp[i1+l0.length] = l0[i1];
			
			return tmp;
		}
		List<T>& operator = (const List<T>& l) {
			if (this == &l) return *this;
			length=l.length;
			delete[] dat;
			dat = new T[length];
			for (int i=0;i<length;i++) dat[i] = l.dat[i];
		}
		bool operator == (const List<T> & l) const {
			if (length != l.length) return false;
			for (int i=0;i<length;i++) {
				if (dat[i] != l.dat[i]) return false;
			}
			return true;
		}
		ostream& operator << (ostream & os, const List<T> & l) {
			
			return os;
		}
};[/PHP]
Although their appears to be no functionality, i successfully got these errors
```
List.h:65: error: ISO C++ forbids declaration of ‘ostream’ with no type
List.h:65: error: ISO C++ forbids declaration of ‘ostream’ with no type
List.h:65: error: expected ‘;’ before ‘&’ token
List.h:69: error: expected `;' before ‘}’ token

```

---

### Post by Jessehk on 2008-07-30
[http://ubuntuforums.org/showpost.php?p=5391230&postcount=2](http://ubuntuforums.org/showpost.php?p=5391230&postcount=2)

---

### Post by dribeas on 2008-07-30
> **Mr.Macdonald said:**
> 
[PHP]template <class T>
class List {
//...
	ostream& operator << (ostream & os, const List<T> & l) {
//...
};[/PHP]
Although their appears to be no functionality, i successfully got these errors
```
List.h:65: error: ISO C++ forbids declaration of &#8216;ostream&#8217; with no type
List.h:65: error: ISO C++ forbids declaration of &#8216;ostream&#8217; with no type
List.h:65: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
List.h:69: error: expected `;' before &#8216;}&#8217; token

```

First of all, the compiler error means that 'ostream' is unkwnown to the compiler at that point. That is due to two things: you have not included the appropiate header, and that you are not qualifying it correctly.

Now, once you solve that, you won't get your expected result either, as that operator must be defined as a free function, not a member function which can be done in any of two ways:

```

#include <ostream>

template <typename T>
class List {
//...
   friend std::ostream& operator<<( std::ostream o, List<T> const & l )
   { 
      // [2]...
   }
};

template <typename T>
std::ostream& operator<< ( std::ostream& o, List<T> const & l )
{
   // [1]...
};

```

[1] Would be the standard for any general purpose class (non-templated) without access to list internals
[2] Is a trick to define a free function inside the class definition. This also allows the code to access all private and protected data inside the class, and has some advantages with templated code. I remember reading about it, but don't remember the book and I don't want to be un precise here.

Now, I am assuming that your class is not designed to be used as a base class. If it where, the recomedation would be having a virtual dump( std::ostream & ) method that does the real work and the internals of operator << would be just calling that dump() method. This would allow you to output the most derived class through a base pointer/reference.

Now for the rest of the class' design. Your implementation seems rather awkward for a List, and closer to a vector. Even then, push()/pop() operations are stack operations...

I take it that you are writing the class just for learning, and there are some smart interesting things done in your code, and some others that could be easily improved, but I won't keep writting here, this is already too long.

   David

P.S. operator<< and operator>> for output and input from iostreams must be externally defined. operator= must be defined inside the class. Most other (common) operators can be defined either internally or externally, but out-of-class definition can have advantages as the free function version are symmetric, which in-class defined operators are not.

P.S.2 Do read [Class mechanics]("http://www.gotw.ca/gotw/004.htm"), from the web or in [Exceptional C++]("http://www.amazon.com/Exceptional-Engineering-Programming-Solutions-Depth/dp/0201615622/ref=sr_1_1?ie=UTF8&s=books&qid=1217442580&sr=8-1")

---

### Post by Mr.Macdonald on 2008-07-30
> #include <ostream>

It would be very nice if the guides said that i needed to include a library!?!?!

> Now for the rest of the class' design. Your implementation seems rather awkward for a List, and closer to a vector. Even then, push()/pop() operations are stack operations...

I take it that you are writing the class just for learning, and there are some smart interesting things done in your code, and some others that could be easily improved, but I won't keep writting here, this is already too long.

I am trying to make it similar to the Python List because those make me really happy. I didn't like the Vector class to much, i wanted something simple and automated. As for the push/pop, i put those because i was bored, i will probably take them out latter.

But could you tell me what i need to fix and how i should do it. I am learning C++ and perfecting my programming right now.

attach a .txt or .pdf if you want!

---

### Post by dribeas on 2008-07-31
> **Mr.Macdonald said:**
> I am trying to make it similar to the Python List because those make me really happy. I didn't like the Vector class to much, i wanted something simple and automated.[...]

But could you tell me what i need to fix and how i should do it. I am learning C++ and perfecting my programming right now.

attach a .txt or .pdf if you want!

My recommendation is getting used to std::vector<>, it is really hard (even for experts) to come close to the quality in design of STL. What did you not like from std::vector? At the end, your implementation is a rough std::vector by other name. 

Even if you want to do it, use std::vector internally, as it will ease your development time and code quality.

   David

Some deatils:
length should never be public, that will allow users to change the length without actually incrementing buffer size -> recipe for desaster. Use a private member and a public accessor:
```

class List {
   std::size_t length_; // size_t is an unsigned integer type
public:
   std::size_t length() const // accessor: does not allow changes, marked const
   { return length_; } 

```

What is the point of having the List contain 1+ elements if you are going to grow it as required? Make 
```

explicit List( std::size_t size=0 ) : length_(size), data_(new T[size]) {} 

```
Here you are providing a default + (int) constructor at once, implementation is exactly the same (if no parameter is given, then 0 is assumed). Constructor marked explicit to avoid implicit casts from int to List.


pop() is indeed a top(): shows the upper element of the stack, does not erase it. If you want your container to be exception safe, then that separation is required, but you'll need to implement both top() and pop().

operator+ should be a free function:
```

template <typename T> class List {...}

template <typename T> List<T>& operator+( List<T> const &, List<T> const & ); // and then implemented

```
Same for operator ==. If you offer operator== then you should also offer operator!=

operator= should always return this. It is not exception-safe (most of your methods aren't, but this is clearer to explain. If memory acquisition fails with an exception you end up with a List<T> that is in an unrecoverable state. The same happens if any of the copy operations fail (raises an exception). Those operations should be performed on a temporary and only when all potential failing operations are completed you should move your data structures.

Making this class exception safe needs a design review. Real data structure should be kept inside an implementation class held through an auto_ptr<>, with the class offering a constructor that takes size as an argument and accessor methods for internal data positions. This is quite longer to explain, the idea is that you can solve your memory issue if you held the memory through a smart pointer (so that if an exception is raised stack-unwinding will destroy the smart pointer that will free memory). Now the problem is that the standard smart pointer std::auto_ptr cannot be used to hold array references, as on destruction it will call delete instead of delete[]. The easy solution is wrapping the array into an internal detail class that can be held in the smart pointer and will free memory on destruction.

This pretty much covers most of the details on the operations that you provided in your code. Trust me, even experts (which I don't consider myself to be) will miss things that are already solved in STL containers, and there are reasons for most everything

---

