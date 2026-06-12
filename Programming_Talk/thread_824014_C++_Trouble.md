---
title: "C++ Trouble"
date: 2008-06-09
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-06-09
I am having trouble with some code i wrote in C++. It is mainly the CString class. Sometimes when i print the classes content to a file it writes strange symbols, like in the uploaded picture, to the file name???

These are the commands i ran once in the codes local directory
[PHP]
$ g++ -Wall ./test.cc `pkg-config --cflags --libs libcurl` -o test
$ ./test "http://www.sparknotes.com/drama/antigone/" "/home/aidan/test.txt"
/home/aidan/test.txt
20

$ 
[/PHP]

as shown i am using g++ and including the libcurl into the compilation

(i uploaded a croped screen shot of the file and the code and executable in a Bz2)

So ...

---

### Post by dwhitney67 on 2008-06-09
The need for the CString class is questionable; why did you not use the STL string class?  It would have been a lot easier to manage the data you want.

Anyhow, I looked at the code you presented, and was confused with a lot of it.  One thing that you need to get a handle on is memory allocation and deletion.  Your code did not manage memory that well.  Plus, you perform cyclic operations to copy character by character of one string to another, when you should have just relied on the available C libraries.  (Or as mentioned earlier, just use STL string).

Without much to go on (i.e. lack of requirements), I patched your code as best as possible so that it extracts the section beginning with the "<!-- BEGIN CONTENT -->".

You may not recognize the code below because I gracefully added much needed white-space... both horizontal and vertical... so that the code is more readable.  I also removed the methods that were either not called, or had bugs in them.

Once you learn more about memory allocation, then perhaps you can add the missing methods back into your code (if they are needed).

Here's the code:
[PHP]
#include <curl/curl.h>

#include <fstream>
#include <string>
#include <iostream>
#include <cstring>
#include <cassert>


class CString
{
  public:
    CString()
    {
      m_array = 0;
      m_length = 0;
    }

    CString( const char *a )
    {
      m_length = strlen(a);
      m_array  = strndup( a, m_length );
    }

    CString( const char *a, const size_t len )
    {
      assert( strlen(a) == len );

      m_length = strlen(a);
      m_array  = strndup( a, m_length );
    }

    CString( const std::string &s )
    {
      m_length = s.length();
      m_array  = strndup( s.c_str(), m_length );
    }

    CString( const CString &other )
    {
      m_length = other.m_length;
      m_array  = strndup( other.m_array, m_length );
    }

    ~CString()
    {
      if ( m_length > 0 )
      {
        delete []m_array;

        m_length = 0;
        m_array  = 0;
      }
    }

    CString slice( const int start, const int end ) const
    {
      if ( start < 0 || end < 0 )
      {
        return CString( "" );
      }

      char *txt = new char[ end - start + 1 ];

      for ( int i = 0; i < (end - start); ++i )
      {
        txt[i] = m_array[ start + i ];
      }
      txt[ end - start ] = '\0';

      CString rtn( txt );

      delete []txt;
      return rtn;
    }

    int find( const CString &needle ) const
    {
      if ( m_length == 0 ) return -1;

      char *pos = strstr( m_array, needle.m_array );

      if ( pos == 0 ) return -1;

      return pos - m_array;
    }

    const char* text() const
    {
      return m_array;
    }

    size_t length() const
    {
      return m_length;
    }

    CString operator+( const CString &s )
    {
      char *tmp = new char[ this->m_length + s.m_length + 1 ];

      strncpy( tmp, this->m_array, this->m_length );
      tmp[ this->m_length ] = '\0';
      strncat( tmp, s.m_array, s.m_length );

      return CString( tmp );
    }

    CString operator+=( const CString &s )
    {
      CString tmp = (*this + s);

      if ( this->m_length > 0 )
      {
        delete []this->m_array;
      }

      this->m_array  = strndup( tmp.m_array, tmp.m_length );
      this->m_length = tmp.m_length;

      return tmp;
    }

    friend std::ostream& operator<<( std::ostream &os, const CString &str )
    {
      if ( str.m_length > 0 )
      {
        os << str.m_array;
      }
      return os;
    }

  private:
    char * m_array;
    size_t m_length;
};


class ParseSpark
{
  public:
    static void init()
    {
      s_contents.~CString();
    }

    static size_t handle( void *ptr, size_t size, size_t nmemb, void *stream )
    {
      size_t numbytes = size * nmemb;
      CString data ( (char*) ptr, numbytes );
      s_contents += data;
      return numbytes;
    }

    static CString filter()
    {
      return s_contents.slice( s_contents.find( CString("<!-- BEGIN CONTENT -->") ),
                               s_contents.find( CString("<!-- END CONTENT -->") ) );
    }

  private:
    static CString s_contents;
};


// Initialize static variables
CString ParseSpark::s_contents;


int main( int argc, char **argv )
{
  if ( argc != 3 )
  {
    std::cout << "Arguments include Website and Out File" << std::endl;
    return -1;
  }

  CString site( argv[1] );
  CString fname( argv[2] );
  CString context( "content.html" );

  ////////////////////////

  CURL *curl = curl_easy_init();

  curl_easy_setopt( curl, CURLOPT_WRITEFUNCTION, ParseSpark::handle );
  curl_easy_setopt( curl, CURLOPT_URL, (site + context).text() );
  curl_easy_perform( curl );
  curl_easy_cleanup( curl );

  ////////////////////////

  std::ofstream fs( fname.text() );
  fs << ParseSpark::filter();
  fs.close();

  return 0;
}
[/PHP]

---

### Post by public_void on 2008-06-10
Memory management is still incorrect because delete[] is used to free memory allocated with strndup(). strndup() uses malloc internally and therefore free() should be used to deallocate memory.

---

### Post by moma on 2008-06-10
I also urge you to use the **std::string** class from the STL (Standard Template Library).
Study: [http://www.cplusplus.com/reference/string/string](http://www.cplusplus.com/reference/string/string)
and [http://cppreference.com](http://cppreference.com)

If you do not like the std::string, feel free to study and use this home_made **dstring** class.
[http://www.futuredesktop.org/adt/utils/](http://home.online.no/~osmoma//adt/utils) 

More [opportunities...]("http://www.futuredesktop.org/opportunities.html")

---

### Post by dwhitney67 on 2008-06-10
> **public_void said:**
> Memory management is still incorrect because delete[] is used to free memory allocated with strndup(). strndup() uses malloc internally and therefore free() should be used to deallocate memory.
Yep, I think you are right about this.  My bad.

Btw, what tools are available for me to verify whether the application has a memory leak or not.  I ask because the code I submitted, even though it works, must undoubtedly have memory leaks based on your comment.

---

### Post by JupiterV2 on 2008-06-10
I use Valgrind. Its available in the repositories.

---

### Post by dwhitney67 on 2008-06-10
If I install valgrind, does it include documentation?  Is it easy to use?  Perhaps an example may help!

---

### Post by geirha on 2008-06-10
I usually only use it the simple way, using no options whatsoever:
```
valgrind ./a.out
```

for help, just run "valgrind --help" and/or "man valgrind"

---

### Post by public_void on 2008-06-10
Typically I invoke Valgrind memcheck as followed.
```
valgrind --tool=memcheck --leak-check=full --show-reachable=yes [executable] [args]

```Have a read of the [Valgrind Quick Start Guide]("http://valgrind.org/docs/manual/quick-start.html") or [Memcheck User Manual]("http://valgrind.org/docs/manual/mc-manual.html") for more details.

---

### Post by Mr.Macdonald on 2008-06-10
First of all what is "size_t", this is the reason i didn't use the string class.

Also Strings didn't have a slice function and i needed that


but i guess i will use the string class. and is their a more in depth tutorial than cplusplus.com. Or one about memory management, I am used to Java (don't rant cause i have heard it before) and know nothing about memory management and very little on pointers and referancing.


a side question:

in c++ is there a basic data object like the Java Object, that can hold anything in it?

---

### Post by dwhitney67 on 2008-06-10
> **Mr.Macdonald said:**
> First of all what is "size_t", this is the reason i didn't use the string class.

Also Strings didn't have a slice function and i needed that


but i guess i will use the string class. and is their a more in depth tutorial than cplusplus.com. Or one about memory management, I am used to Java (don't rant cause i have heard it before) and know nothing about memory management and very little on pointers and referancing.


a side question:

in c++ is there a basic data object like the Java Object, that can hold anything in it?

The size_t is essentially an unsigned int(eger).  It is useful to use when it is implied that the variable can never hold a negative value.

Concerning slice(), if the STL string object doesn't have it (which I was too lazy to investigate), then just add it (that is, extend std::string's capabilities).

Here's how:
[PHP]#include <string>
#include <iostream>


class CString : public std::string
{
  public:
    CString( const char *str )
    {
      this->assign( str );
    }
    CString( const std::string &str )
    {
      this->assign( str );
    }
    CString slice( const size_t start, const size_t end ) const
    {
      if ( start == npos || end == npos )
      {
        return CString("");
      }

      return this->substr( start, end - start );
    }
};


int main( int argc, char **argv )
{
  CString fromURL = CString( "This is the contents of a webpage\n"
                             "<!-- BEGIN CONTENT -->\n"
                             "Blah blah blah.\n"
                             "<!-- END CONTENT -->\n" );

  CString sliceStr = fromURL.slice( fromURL.find( "<!-- BEGIN CONTENT -->" ),
                                    fromURL.find( "<!-- END CONTENT -->" ) );

  std::cout << "sliceStr =\n" << sliceStr << std::endl;

  return 0;
}[/PHP]

---

### Post by Mr.Macdonald on 2008-06-10
> Concerning slice(), if the STL string object doesn't have it (which I was too lazy to investigate), then just add it (that is, extend std::string's capabilities).

Man, I wish i thought of that

---

### Post by geirha on 2008-06-11
In this case, since CString's constructors should do the exact same thing as std::string's, you might as well call std::string's constructors
[php]
class CString : public std::string
{
  public:
    CString( const char *str ) : std::string(str) {}
    CString( const std::string &str ) : std::string(str) {}
    CString slice( const size_t start, const size_t end ) const
       ...
[/php]

BTW, from the way slice() was used in that example, wouldn't it make more sense for the slice() to take two strings as arguments instead?

---

### Post by Mr.Macdonald on 2008-06-11
> BTW, from the way slice() was used in that example, wouldn't it make more sense for the slice() to take two strings as arguments instead?

how would that work

what slice does is:

a = "hello world"

cout << a.slice(0, 5)

prints

"hello" (without quotes)


maybe you mean a merge or combine ??


but .. can anyone point me to a c++ memory, pointer, memory leak tutorial??

---

