---
title: "std::vector functions"
date: 2008-09-10
forum: Programming Talk
---

### Post by Emill on 2008-09-10
Hello. I am trying to make some functions for vectors. I am trying this:

void vector_function(std::vector &v){
	//Code
}
This gives me a compile error.

I want to have the same function for all the kinds of datatypes in it. Now I have to type:
void vector_function_int(std::vector<int> &v){
	//Code
}
and
void vector_function_string(std::vector<std::string> &v){
	//Code
}
and so on for every datatype I need. Is there a way in which I only need one function?

---

### Post by cb951303 on 2008-09-10
C++ is a statically-typed language meaning you have to specify the type of the object

---

### Post by mike_g on 2008-09-10
I thhink you will need to remove the ampersands(&). EG:
```
void vector_function(std::vector v){
//Code
}
```

Edit: oh maybe not.

Edit 2: cant you template it?

---

### Post by Emill on 2008-09-10
Removing the ampersand doesn't work.

So C++ is a stacically typed language.
So there are no workaround for this? Can I maybe add a function myself to the vector class somehow?

---

### Post by hod139 on 2008-09-10
```

template< typename T >
void vector_function(std::vector<T> &v){
	//Code
}

```
The compiler will determine the type of T at compile time.

This is called generic programming.
[http://www.boost.org/community/generic_programming.html](http://www.boost.org/community/generic_programming.html)
[http://en.wikipedia.org/wiki/Generic_programming](http://en.wikipedia.org/wiki/Generic_programming)

---

### Post by Emill on 2008-09-10
That worked :)

---

### Post by mike_g on 2008-09-10
Yeah, thats what I meant by templating it. I was just about to dig out some old code I wrote that I dont understand any more, but you beat me to it :D

---

### Post by Emill on 2008-09-10
Hmm. I have some problems.
When I use:
```

template <class T>
void vector_function(std::vector<T> &v){
	std::vector<T>::iterator it;
	//Code
}

```
I get
error: expected `;' before "it"

---

### Post by hod139 on 2008-09-10
This is a common problem with C++ and templates.  The problem is that the compiler cannot determine if you are making a function call, or using a type.  The solution is to use the typename keyword to help the compiler:
```

typename std::vector<T>::iterator it;

```

---

### Post by dribeas on 2008-09-10
Your question has already been answered, but still just a general comment on design:

If your function can cope with any iterable container you can template on that iterator kind and that way your code will work for any other container.

```

template <typename ForwardIterator>
void dump( std::ostream & out, ForwardIterator begin, ForwardIterator end )
{
   for ( ; begin != end; ++begin )
   {
      out << ' ' << *begin;
   }
}

//usage
std::vector<int> v; // and fill in data
dump( std::cout, v.begin(), v.end() );

std::list<double> l; // and fill in data
dump( std::cerr, l.begin(), l.end() );

```

The example above is very simplistic in that being such a simple loop it could be achieved with std::for_each, but nonetheless it is an easy to follow example.

---

### Post by Emill on 2008-09-10
So I have to use an extra function for my loop?
Edit: Didn't see post #9. Now it works :)

---

### Post by dribeas on 2008-09-10
> **Emill said:**
> ```

template <class T>
void vector_function(std::vector<T> &v){
	std::vector<T>::iterator it;
	//Code
}

```

That is something funny when using templates. Some times you must help the compiler:

```

//...
   typename std::vector<T>::iterator it;
//...

```

The reason is that template compilation has a two step validation process. During the first round the template itself is validated without considering the particular instantiation (what T is in this case), and then the code is checked with the particular T you are using.

During the first step the compiler cannot possibly know whether std::vector<T>::iterator is indeed a data type or an attribute. As a simpler example:

```

template <typename T>
struct MyTemplate
{
   typedef T type;
};

template <>
struct MyTemplate<int> // specialization for int
{
   int type;
};

template <typename T>
void f( MyTemplate<T> & in )
{
   MyTemplate<T>::type; // what is this?
}

```

Before real instantiation of the function f() the compiler cannot know whether MyTemplate<T>::type is a data type or a member. If it is instantiated with an int then it will be an attribute, for most other data types (at least for all for which there is no specialization) then it is a data type.

---

