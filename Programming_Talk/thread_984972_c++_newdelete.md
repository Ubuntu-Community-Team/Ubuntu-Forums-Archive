---
title: "c++ new/delete"
date: 2008-11-17
forum: Programming Talk
---

### Post by abraxas334 on 2008-11-17
I've been trying to find an answer by googling it but no luck so maybe someone can help me with my simple memory allocation problem in c++.

In my the constructor of a class i define the following

```

int ***_lattice;
 assert(_lattice ==NULL);
    cout<<"Initialising 3D lattice space"<<endl;
    _lattice = new int**[size];
    for(int i = 0; i<size; i++)
    {
       _lattice[i]= new int*[size];
    
        for (int j =0; j<size; j++)
        {
            _lattice[i][j] = new int[size];
        }
    }
    assert(_lattice != NULL);
    cout<<"3D lattice initialised"<<endl;



```


and in my destructor i want to dallocate the memory by doing this:

```

     for(int i = 0; i<size; i++)
        {
            for (int j = 0; j<size; j++)

            {
                delete[]_lattice[i][j];
            }
            delete [] _lattice[i];
        }
        delete [] _lattice;
    }
    assert(_lattice==NULL);
    {
        cout<<"lattice deallocation failed"<<endl;
    }



```

am i right in assuming that _lattice should be 0 after deallocation? why does my assert keep failing.
I am a bit lost.

Thanks for any help

---

### Post by Zugzwang on 2008-11-17
> **abraxas334 said:**
> 
am i right in assuming that _lattice should be 0 after deallocation? why does my assert keep failing.


No, delete[] does not change the value of the pointer, it just deallocates the memory. If you want the pointer to point to NULL, you have to do that manually afterwards.

EDIT: Btw, in C++, there is no way to tell whether a pointer points to a valid memory location or not (except that NULL is never a valid memory location)

---

### Post by abraxas334 on 2008-11-17
Ok sorry for being slow here, but another delete question:

if i define an array like this in a class header
```

class cfoo{
int *contacts[2];
};

class cfoo2 : public foo{

} ;

```
and call it in a function of a different class like this:
[PHP]
class another
{
    cfoo* p_cfoo;
    cfoo2* p_cfoo2;
    int someNumber;
    void function();
};

 void another::function()
{
    p_cfoo2 = new p_cfoo2;
    p_cfoo = p_cfoo2;

//and then
    p_cfoo2->contacts = new int [someNumber][2];

}

[/PHP]

my question now is how do i delete the allocated memory in this case? I tried to delete it in the destructor of cfoo as well as cfoo2 but vlagind is never happy with it and i am still not deallocating all memeory.
Can anyone help?
Thanks

---

### Post by Cracauer on 2008-11-17
You should check out 
scoped_ptr
and
scoped_array

---

### Post by Zugzwang on 2008-11-17
> **abraxas334 said:**
> 
my question now is how do i delete the allocated memory in this case? I tried to delete it in the destructor of cfoo as well as cfoo2 but vlagind is never happy with it and i am still not deallocating all memeory.


I double that the example above compiles (Capitalisation is different). Please make sure that you paste the code you've actually tried 1-to-1. I suspect that the compiler complains about something else as well -- namely that your assignment is invalid.

---

### Post by psusi on 2008-11-17
lattice is a local variable, and as such, it's initial value is completely undefined.  Usually it will be whatever garbage was left over in that location on the stack, so your comparison to NULL fails.

---

### Post by abraxas334 on 2008-11-18
The second example i gave (my second post) does compile and run in my actual code, i just simplified the class and function a bit so any syntax errors are not what i am looking for. I ran my working through valgrind and it gives me an error, that 2 blocks are not freed, and when looking at the line it gives me in the code it comes down to the dynamical assignemnt of the contacts array.
So how do i free that memory, so i am not leaking memory any more?



mmmmhhhhh new plan, ill just use a garbage collector for c++, saves me having to work out all the memory allocation/freeing stuff, as i obviously don't quite understand it

---

### Post by dwhitney67 on 2008-11-18
> **abraxas334 said:**
> The second example i gave (my second post) does compile and run in my actual code, i just simplified the class and function a bit so any syntax errors are not what i am looking for.

Are you sure? I have not attempted to compile your code, but this statement looks suspicious:
[php]
...
    p_cfoo2->contacts = new int [someNumber][2];
...
[/php]
'contacts' is a private member of cfoo, thus I doubt you would have access from a function defined within the class another.

> **abraxas334 said:**
> 
I ran my working through valgrind and it gives me an error, that 2 blocks are not freed, and when looking at the line it gives me in the code it comes down to the dynamical assignemnt of the contacts array.
So how do i free that memory, so i am not leaking memory any more?

I did not test the code in your most recent posting, but the code you supplied in the OP appears correct *minus* the check with assert().  I ran a similar test through valgrind (using *--leak-check=full* option) and it reported no leaks.
[php]
template <class T>
class Lattice
{
  public:
    Lattice(unsigned int size = 2)
      : m_size(size)
    {
      m_lattice = new T**[m_size];

      for (unsigned int r = 0; r < m_size; ++r)
      {
        m_lattice[r] = new T*[m_size];

        for (unsigned int c = 0; c < m_size; ++c)
        {
          m_lattice[r][c] = new T[m_size];
        }
      }
    }

    ~Lattice()
    {
      for (unsigned int r = 0; r < m_size; ++r)
      {
        for (unsigned int c = 0; c < m_size; ++c)
        {
          delete [] m_lattice[r][c];
        }

        delete [] m_lattice[r];
      }
      delete [] m_lattice;
    }

  private:
    unsigned int m_size;
    T***         m_lattice;
};
[/php]

> **abraxas334 said:**
> 
mmmmhhhhh new plan, ill just use a garbage collector for c++, saves me having to work out all the memory allocation/freeing stuff, as i obviously don't quite understand it
C++ garbage collector?

---

### Post by abraxas334 on 2008-11-18
> 

appears correct *minus* the check with assert().



yes i have got rid of that assert as it is pointless, but i did not realise that before.

> 
contacts' is a private member of cfoo

actually it is public, i just missed out the public, when i copied and pasted obviously.

> 
C++ garbage collector? 

Yes there is a library written by Hans Boehm, which in the end managed to solve all my problems (Am a java girl and was only recently forced to do c++ stuff and therefore not used to having no garbage collector i.e having too free memory manually).
Check it out it really can save alot of time and my whole code is leak free now :)
[http://www.hpl.hp.com/personal/Hans_Boehm/gc/]("http://www.hpl.hp.com/personal/Hans_Boehm/gc/")
and ubuntu kindly got it installed already :)
Thanks for all the help

---

### Post by dwhitney67 on 2008-11-18
The C++ GC looks interesting, but the use of uppercase letters for the API functions look horrendous.

I decided to brush up a little on my C++/Boost skills, so I took on Cracauer's suggestion at using shared_array.

I do not know if I did it correctly; unfortunately I can't get it to release all of the memory.  I'll keep looking into it.

[php]
#include <boost/shared_array.hpp>
#include <stdexcept>
#include <vector>
#include <iostream>


template <class T, size_t S>
struct Matrix
{
  Matrix()
  {
    m_matrix.resize(S);

    for (size_t i = 0; i < S; ++i)
    {
      m_matrix[i].resize(S);
    }
  }
  std::vector< std::vector<T> > m_matrix;
};


template <class T, size_t S>
class Lattice
{
  public:
    Lattice()
      : m_lattice(new Matrix<T,S>[S])
    {
    }

    void insertValue(size_t row, size_t col, size_t depth, const T value)
    {
      if (row >= S || col >= S || depth >= S)
        throw std::range_error("index out of range.");

      (m_lattice[row]).m_matrix[col][depth] = value;
    }

    T getValue(size_t row, size_t col, size_t depth)
    {
      if (row >= S || col >= S || depth >= S)
        throw std::range_error("index out of range.");

      return (m_lattice[row]).m_matrix[col][depth];
    }

  private:
    boost::shared_array< Matrix<T,S> > m_lattice;
};


int main()
{
  Lattice<int, 3> lattice;

  try
  {
    lattice.insertValue(1,1,1,10);

    std::cout << lattice.getValue(1,1,1) << std::endl;

    lattice.insertValue(4,1,1,10);
  }
  catch (std::exception& ex)
  {
    std::cerr << "Exception: " << ex.what() << std::endl;
  }

  return 0;
}
[/php]

UPDATE:
I found the problem.  I mistakenly used reserve() when attempting to pre-size the vectors.  I should have been using resize().  Now the memory leaks are cleared up.

---

### Post by psusi on 2008-11-18
Or you could just use std::vector<>.

```

#include <vector>
using std;

vector< vector< int > > matrix;

```

---

### Post by dwhitney67 on 2008-11-18
> **psusi said:**
> Or you could just use std::vector<>.

```

#include <vector>
using std;

vector< vector< int > > matrix;

```

I agree, even though the OP wanted a 3-dimensional matrix (lattice).  Without knowing more about the intent or the needs of the project being supported by the OP, one can only hypothesize as to why memory had to be allocated from the heap.

P.S.  There are cases where STL (or Boost) are not useful.  These cases generally involved embedded systems where memory (for the application) is limited.  I worked on such a project where only an 8MB board was available.  On that project, Embedded-C++ standards were used.

---

### Post by abraxas334 on 2008-11-20
> **dwhitney67 said:**
> I agree, even though the OP wanted a 3-dimensional matrix (lattice).  Without knowing more about the intent or the needs of the project being supported by the OP, one can only hypothesize as to why memory had to be allocated from the heap.

P.S.  There are cases where STL (or Boost) are not useful.  These cases generally involved embedded systems where memory (for the application) is limited.  I worked on such a project where only an 8MB board was available.  On that project, Embedded-C++ standards were used.

Thank you for all the suggestions, a STL container in my case here is not very useful, i do use them normally as they give me less of a headache. 
Also the problem is there is always so many different ways of doing something i find it hard to decide which would be the best.

---

