---
title: "define my own iterator for my own container class"
date: 2008-09-25
forum: Programming Talk
---

### Post by monkeyking on 2008-09-25
Hi,
Can someone help me with defining my own iterator for my own class.
Or point me in the right direction.

I've been looking through some stl libs, and that didn't really help.

Do I need to define all iterator methods,
or just the ones I'm going to use.

stl compiler messages are a hell debugging.

thanks

edit:
btw I'm using a templated container, if this helps.

---

### Post by dwhitney67 on 2008-09-25
I'm sorry to ask...

But why are you defining your own container class when there is a rich suite of them available in the Standard Template Library?

For most practical purposes, there is the vector (or the deque) that emulate the behaviour of an array.

If indeed you are merely attempting to extend your C++ knowledge of the internal workings of STL, then you should take a look at the GCC code (it is open source!).

Here's an impractical example of how one _could_ define/use an iterator for a home-made container (I'm not implying this is the best way to do things!).  But seriously, the use of an STL vector would be better suited here.
[PHP]
#include <stdexcept>
#include <sstream>

namespace nonstd
{
template< class T >
class Vector
{
  public:
    typedef T const * const_iterator;     // const iterator
    typedef T *       iterator;           // non-const iterator

    Vector( size_t size = 5 )
      : m_size(size),
        m_tail(0),
        m_data(new T[size])
    {
    }

    Vector( const Vector<T>& other )
      : m_size(other.m_size),
        m_tail(other.m_tail),
        m_data(new T[m_size])
    {
      for ( size_t i = 0; i < m_size; ++i )
      {
        m_data[i] = other.m_data[i];
      }
    }

    ~Vector()
    {
      delete []m_data;
    }

    void push_back( T data )
    {
      if ( m_tail == m_size )
      {
        // allocate more memory into temporary location
        const size_t newSize = (m_size == 0 ? 5 : m_size * 2);

        T * temp = new T[ newSize ];

        // transfer data
        for ( size_t i = 0; i < m_size; ++i )
        {
          temp[i] = m_data[i];
        }

        // destroy existing memory
        delete []m_data;

        // restore the data, and adjust m_size
        m_data = temp;
        m_size = newSize;
      }

      m_data[ m_tail++ ] = data;
    }

    iterator begin()
    {
      return &m_data[0];            // return the address of element zero
    }

    iterator end()
    {
      return &m_data[ m_tail ];     // return the address of the "last" element
    }

    size_t size() const
    {
      return m_tail;
    }

    const T operator[]( const size_t index ) const
    {
      if ( index >= m_tail )
      {
        std::ostringstream ostr;
        ostr << "Index (" << index << ") is out of range.";
        throw std::range_error( ostr.str() );
      }

      return m_data[ index ];
    }

    Vector<T>& operator=( const Vector<T>& other )
    {
      delete []m_data;

      m_size = other.m_size;
      m_tail = other.m_tail;
      m_data = new T[m_size];

      for ( size_t i = 0; i < m_size; ++i )
      {
        m_data[i] = other.m_data[i];
      }

      return *this;
    }

  private:
    size_t m_size;
    size_t m_tail;
    T *    m_data;
};

}  // end namespace nonstd


#include <iostream>
#include <algorithm>    // for_each()
#include <cassert>      // assert()


template< class T >
void displayValue( const T& value )
{
  std::cout << value << " ";
}


int main()
{
  try
  {
    nonstd::Vector<int> vec1( 5 );   // request initial size of 5 elements

    vec1.push_back( 1 );
    vec1.push_back( 2 );
    vec1.push_back( 3 );
    vec1.push_back( 4 );
    vec1.push_back( 5 );
    vec1.push_back( 6 );             // this will force a reallocation of memory


    nonstd::Vector<int> vec2 = vec1;    // test copy constructor
    nonstd::Vector<int> vec3;
    vec3 = vec1;                         // test operator=()

    assert( vec1.size() == vec2.size() );
    assert( vec2.size() == vec3.size() );

    // Display results
    std::cout << "vec1: ";
    std::for_each( vec1.begin(), vec1.end(), displayValue<int> );
    std::cout << std::endl;

    std::cout << "vec2: ";
    std::for_each( vec2.begin(), vec2.end(), displayValue<int> );
    std::cout << std::endl;

    std::cout << "vec3: ";
    for ( size_t i = 0; i < vec3.size(); ++i )
    {
      std::cout << vec3[i] << " ";
    }
    std::cout << std::endl;

    // Force exception to be thrown...
    std::cout << "Value of vec3[" << vec3.size() << "] = ";
    std::cout << vec3[ vec3.size() ] << std::endl;
  }
  catch ( std::exception& ex )
  {
    std::cout << ex.what() << std::endl;
  }

  return 0;
}
[/PHP]

---

### Post by monkeyking on 2008-09-29
Hi, sorry for not getting back to you before,
I've been on an extended weekend.

I've defined my own matrixclass/array class,
and instead of trying to develop all algorithms in the world,
I just wanna hook it up with the stl<algorithms>,
but I'm having problems doing this.
I'm just trying to learn c++/stl, not to rethink c++.

The problem I'm facing is something like this.
I can use the 'std::multimap' easily like this

[PHP]
int dat[5] = {0,6,3,7,3};
  
 typedef std::multimap< int, int >  asso;
 asso dict;
 for (int i=0;i<5;i++){
   dict.insert(make_pair(dat[i],i));
 }
  
  asso::iterator pos;
  
  for(pos=dict.begin(); pos!=dict.end() ;pos++)
    cout << pos->first <<" next "<< pos->second <<endl;
[/PHP]
This will give me the order of an array, 
that is the permutation that maps the array into weak ascending set.

But if I want to use this on my own array template I run into all sort of problems.

An example code for this is

[PHP]
template<typename T>
void test(Array<T> ai){
  typedef std::multimap< Array<T>, int >  asso;
  asso dict;
  for (int i=0 ; i<5 ; i++){
   dict.insert(make_pair(ai(i),i));
  }
  
  asso::iterator pos;
  
  for(pos=dict.begin() ; pos!=dict.end() ; pos++)
    cout << pos->first <<" next "<< pos->second <<endl;
}
[/PHP]

So I think my problem is, that I don't know which iterator types, I need to implement before being able to use the generic stl functions.


[PHP]
  
  typedef T              value_type;
  typedef T*             iterator;
  typedef const T*       const_iterator;
  typedef T&             reference;
  typedef const T&       const_reference;
  typedef std::size_t    size_type;
  typedef std::ptrdiff_t difference_type;
  
        // iterator support
  iterator begin() { return data_; }
  const_iterator begin() const { return data_; }
  iterator end() { return data_+x_; }
  const_iterator end() const { return data_+x_; }
[/PHP]

thanks

---

### Post by dwhitney67 on 2008-09-29
I'm sorry, but I am confused.  Maybe it is because you are showing me your solution, but not discussing the "problem".

It looks odd that you are setting the "key" of your multimap to be an Array<T>, as opposed to an elemental object (say type T).  Do you understand my confusion?  It's like:
[php]
std::multimap< std::vector< int >, int > weirdMap;
[/php]

It doesn't make sense!

-------------------------
Update....

I attempted to implement something similar to the multimap you described in your post.  Whether it makes sense or not is probably not for me to decide.  It just seems weird.

I edited the Vector code I provided earlier to include both the const_iterator methods for begin() and end(), and also added a bool operator<() method.

Here's the code... minus what I already posted previously...
[php]
// ...

namespace nonstd
{

template< class T >
class Vector
{
    // ...

    const_iterator begin() const
    {
      return &m_data[0];            // return the address of element zero
    }

    const_iterator end() const
    {
      return &m_data[ m_tail ];     // return the address of the "last" element
    }

    // ...

    bool operator<( const Vector<T>& other ) const
    {
      // this method should be augmented more... but I was lazy.
      return m_size < other.m_size;
    }
    // ...
};

}  // end namespace nonstd


#include <map>
#include <string>
#include <iostream>
...

template< class T >
void displayValue( const T& value )
{
  std::cout << value << " ";
}


int main()
{
  // ...

  typedef nonstd::Vector< std::string >        StrVec;

  typedef std::multimap< StrVec, std::string > MM_Dictionary;
  typedef MM_Dictionary::const_iterator        MM_CIter;
  typedef MM_Dictionary::iterator              MM_Iter;

  MM_Dictionary dictionary;

  StrVec vec;
  vec.push_back( "This is string one" );
  vec.push_back( "This is string two" );
  vec.push_back( "This is string three" );

  dictionary.insert( std::pair< StrVec, std::string >( vec, "This is another string one" ) );
  dictionary.insert( std::pair< StrVec, std::string >( vec, "This is another string two" ) );
  dictionary.insert( std::pair< StrVec, std::string >( vec, "This is another string three" ) );

  for ( MM_CIter it = dictionary.begin(); it != dictionary.end(); ++it )
  {
    const StrVec &      vec = it->first;
    const std::string & str = it->second;

    std::for_each( vec.begin(), vec.end(), displayValue<std::string> );
    std::cout << "str = " << str << std::endl;
  }

  return 0;
}
[/php]

---

### Post by monkeyking on 2008-09-29
Hi I'll be looking into your code shortly,
but let me explain the logic behind,
so it doesn't seem to strange.


Given a list of 10 numbers I want these sorted,
but not only that,
I also want the permutation order that will sort the numbers.

If I use std::multimap the key will be a standard less.
Which means that when I iterate through the inserted multimap datastructure, I will get the elements in a ascending order.

The value corresponding to each key will then be their original position.

The rationale behind this elaborate scheme is straight forward.

Given a Matrix of size 4x7, If I want to sort all the rows so the third column of the matrix is ascending.
Then I'll just use the permutation list from the sorted multimap third column, and swap the rows after this list.


I've already implemented this solution, and it works nicely.
But I need to have 3 different multimaps, for 'int', 'float' and 'double'.

This version will do for now,
but for future projects, it's nice to have solutions and not work arounds.

I'll look into the code you posted, and see if the const iterator works for this.

thanks again.

---

### Post by dwhitney67 on 2008-09-29
Ok, I understand you are dealing with a Matrix (or 2-dim array).  How does this fit into a multimap?  A multimap is used to store data that can potentially have "keys" with the same value.  A map, on the other hand, must employ the use of unique "keys".  In either case, the map is sorted by the key (using std less), unless you provide your own sorting method.  I believe you know this already.

So what data-type are you using for the "key"?  Is it the row number?  Earlier, it seemed that you were using the Matrix.

---

### Post by monkeyking on 2008-09-30
Hi again,

I'm dealing with a matrix of probabilities,
these are in a domain from 0 to 1, both included. that would be double/float.
But I have no guarantee that these values are unique so I choose the multimap.

I just used the mapping < int , int>, as the simplest example.

---

### Post by dribeas on 2008-09-30
> **monkeyking said:**
> If I use std::multimap the key will be a standard less.

Not necessarily, you can provide your own order functor:
```

template <typename T>
struct greater : public std::binary_function< T, T, bool >
{
    bool operator()( T const & a, T const & b )
    {
        return a > b;
    }
};

int main()
{
   std::multimap< int, int, greater<int> > rmap;
   // rmap is a multimap in reverse order...
}

```

That order could be just as complex as you need it. 

```

template <typename T, int element_>
class n_element_less : public std::binary_function< Array<T>, Array<T>, bool >
{
public:
  bool operator()( Array<T> const & a, Array<T> const & b )
  {
     return a[ element_ ] < b[ element_ ]; // assuming operator[] const defined
  }
};
int main()
{
   std::multimap< Array<int>, int, n_element_less<int,2> > order_map;
   // Multimap ordered non-decreasingly by third element of Array
}

```

I don't know how you have implemented your 2D matrix, but if it where (just to make a simple example) a vector of vectors then you could provide your own hand made order functor to std::sort and have std algorithms solve your reordering at once.

```

template <typename T>
class greater_element : public std::binary_function< std::vector<T>, std::vector<T>, bool >
{
public:
    greater_element( int column ) : index_( column ) {}

    bool operator()( std::vector<T> const & a, std::vector<T> const & b )
    {
        return a[ index_ ] > b[ index_ ];
    }
private:
    int index_;
};

int main()
{
   std::vector< std::vector<int> > v;
   // fill in 2D data
   std::sort( v.begin(), v.end(), greater_element<int>(1) );
}

```

The code above will sort all the vectors inside v in non-ascending order by the 2nd element of the internal vectors. Note that this is an example, and thus does not take care of bounds... This should serve as a simple base to adapt for your own data type.

I am attaching a file with the code above and a simple test.

Also note that this algorithms are quite inefficient: the whole row is being moved, probably many times while sorting. This can be enhanced by using pointers in the outer vector and adapting the code. This way, sorting the whole 2D structure will take about the same time as sorting a 1D vector of int, adding the overhead of dereferencing the column number. This will yield (with SGI STL, I am not sure on gcc) a O(N log(N)) algorithm with N being the number of rows, which is better than what you get while inserting into a multimap.

Without the use of pointers, the time complexity raises to O(NM log(N)), where M is the number of columns in the matrix.

   David

P.S. Anyone knows why a Programming Forum won't allow .cpp attachments? Or is it me?

---

### Post by monkeyking on 2008-10-01
Hi, thanks for all your inputs.
After spending many hours,
I found a solution, when defining my own iterator that depends on a template type.
It's apparently very important to add the keyword 'typename'

[PHP]
template<typename T>
void test(Array<T> ai){
  typedef std::multimap< T, int >  asso;
  asso dict;
  for (int i=0 ; i<5 ; i++){
   dict.insert(make_pair(ai(i),i));
  }
  
  //asso::iterator pos; //old and very wrong
  typename std::multimap<T,int>:iterator pos; //this works
  
  for(pos=dict.begin() ; pos!=dict.end() ; pos++)
    cout << pos->first <<" next "<< pos->second <<endl;
}  
[/PHP]

thanks again for your help,
without your code samples.
I would never have been able to solve this.

---

### Post by dribeas on 2008-10-02
> **monkeyking said:**
> It's apparently very important to add the keyword 'typename'
[PHP]template<typename T>
void test(Array<T> ai){
  typedef std::multimap< T, int >  asso;
//...
  //asso::iterator pos; //old and very wrong
  typename std::multimap<T,int>:iterator pos; //this works
//...
}  
[/PHP]


On the **typename** keyword.

When you are using templates, the compiler must fulfill a two step checking on the templated code. During the first step the template (generic) is validated *before* being instantiated with the type. Then on the second validation, real instantiation occurs and the (now specific) is again validated.

During the first step of validation the compiler often times needs help in determining the meaning of some of the generic code, that is what typename is about: you instruct the compiler that whatever (instantiation dependent) element follows is indeed a type name and not a member function or attribute. Note that even if it might seem clear to you that it is a data type it does not need to be (example below). Finally note that even if you have typedef'ed to a local type alias, asso is still a instantiation dependent type, and thus has the same limitations as std::multimap<T,int>.

```

template <typename T>
void test( Array<T> & ai ) // reference? const reference?
{
   typedef std::multimap< T, int >  asso;
   typename asso::iterator it; // valid
}

```

Why is typename needed?

```

template <typename T>
struct Test;

template <typename T>
void f( Test<T> const & x )
{
   Test<T>::data x; // <- could this be valid? (Assume typename was not required)
}

template <typename T>
struct Test // 1
{
   typename T data; // not too good a name, ok
};

template <> 
struct Test<int> // 2
{
   int data;
};

```

As you see in the example above, f() can be correct or not depending on the definition of Test<T>. Moreover, even if with the generic definition of Test [1] it f() is a valid function with the int specialization [2] it is not valid anymore. f() cannot be checked for validity until T is resolved, but that only happens in the second validation step. During the first step, to check the correctness of f() the compiler must decide whether Test<T>::data is a type or a member attribute (or function). Compilers must default to assuming that it will be a member attribute, and it is up to the user to hint on the opposite direction.

This is a rather confusing part of the standard until you get the hold of it. Anyway there is a simple rule: in a template, all types that depend on template parameters must be preceded by the typename keyword.

BTW, you must know that your definition of test() takes Array<T> as a value argument, and thus will make a copy of it for internal use. As Array<T> sounds as something expensive to copy, you should probably resort to constant references or references (depending on the internal use you make of the argument). That is oftentimes a good rule of thumb: with all but basic types, prefer to pass constant references instead of value arguments.

After rereading, I am not sure it is easy to follow the reasoning. f() is invalid as it needs the typename keyword as a hint. With the typename keyword in place, f( Test<double>() ) will compile but f( Test<int>() ) will fail during the second template validation step, as Test<int> does not have a type by the name of data.

---

### Post by monkeyking on 2008-10-03
> **dribeas said:**
> 
BTW, you must know that your definition of test() takes Array<T> as a value argument, and thus will make a copy of it for internal use. As Array<T> sounds as something expensive to copy, you should probably resort to constant references or references (depending on the internal use you make of the argument). That is oftentimes a good rule of thumb: with all but basic types, prefer to pass constant references instead of value arguments.

Yes in my code, I have made everything a const ref.
The code was just a fast manual copy, of my problem.


> **dribeas said:**
> On the **typename** keyword.

This is a rather confusing part of the standard until you get the hold of it. Anyway there is a simple rule: in a template, all types that depend on template parameters must be preceded by the typename keyword.


After rereading, I am not sure it is easy to follow the reasoning. f() is invalid as it needs the typename keyword as a hint. With the typename keyword in place, f( Test<double>() ) will compile but f( Test<int>() ) will fail during the second template validation step, as Test<int> does not have a type by the name of data.

omg, this is hardcore, 
Where have you learned this?

I need to get a book on template and stl's in general.
I have the black book [http://www.oreillynet.com/cs/catalog/view/cs_msg/88955](http://www.oreillynet.com/cs/catalog/view/cs_msg/88955) .
This book is rather vague when it comes to templates.

But then again, I actually think,
I've encountered every problem that is possible, so I might not need a book.

Thanks for you elaborate help.

---

### Post by dribeas on 2008-10-04
> **monkeyking said:**
> 
omg, this is hardcore, 
Where have you learned this?


Time, experience and reading many different books, each one build over the details others forgot. I can recommend Exceptional/More exceptional C++ from Herb Sutter. Most of the content is available on-line in [Guru of the Week]("http://www.gotw.ca/gotw/") There are a bunch of short problem/test + solutions that explain a bunch of corners in the language, design issues... The one on typenames is [here]("http://www.gotw.ca/gotw/035.htm").

---

