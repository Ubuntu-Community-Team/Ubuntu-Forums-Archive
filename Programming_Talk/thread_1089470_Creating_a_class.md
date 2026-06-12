---
title: "Creating a class?"
date: 2009-03-07
forum: Programming Talk
---

### Post by Vandorin on 2009-03-07
I'm creating a class, and I get some strange errors when compiling, such as "Need a ; before { old style maybe?" and a few other ones telling me i can't re-define my variables. Here is my code, can anyone spot an error?

In my book.h file

```



#include <iostream>
#include <string>
using namespace std;
class Book
{
public:
       // operators

       friend ostream& operator << (ostream& os, const Book& aBook );
       friend istream& operator >> (istream& is, Book& aBook );

       // accessors
       string get_title() const;
       int get_chapter() const;
       int get_pagenumb() const;

       // Mutators

       void set_title (string title);
       void set_chapter (int chapter);
       void set_pagenumb (int pagenumb);
       void set (string title,int chapter,int pagenumb);

       // Constructors

       Book();
       Book( string title, int chapter, int pagenumb);

private:
       int m_chapter,m_pagenumb;
       string m_title;
};


```

In book.cpp

```



#include <iostream>
#include <string>
#include "book.h"
using namespace std;

// Default Values

Book::Book()
{
       set_title( "Please enter a Book name" );
       set_chapter (0);
       set_pagenumb (0);
}

// Constructors

Book::Book( string title, int chapter, int pagenumb )
{
       set_title (title);
       set_chapter (chapter);
       set_pagenumb (pagenumb);
}

// Accessors

string Book::get_title()
{
       return m_title;
}
int Book::get_chapter();
{
       return m_chapter;
}
int Book::get_pagenumb();
{
       return m_pagenumb;
}

// Mutators

void Book::set_title ( string title )
{
       m_title = title;
}
void Book::set_chapter ( int chapter )
{
       m_chapter = chapter;
}
void Book::set_pagenumb ( int pagenumb )
{
       m_pagenumb = pagenumb;
}


// Operators

ostream& operator << (ostream& os, const Book& aBook )
{
       cout << " Name of the book you are reading :";
       os << aBook.get_title() << endl;
       cout << " The last chapter you were on was :";
       os << aBook.get_chapter() << endl;
       cout << " The last page you were on was :";
       os << aBook.get_pagenumb() << endl;
       return os;
}

istream& operator >> (istream is, Book& aBook )
{
       string t;
       int c,pn;
       cout << "Please enter The name of the book you are reading, The last
chapter you were on, and the Page number you stopped at " << endl;
       is >> t >> c >> pn;
       aBook.set_title(t);
       aBook.set_chapter(c);
       aBook.set_pagenumb(pn);
       return is;
}


```

and in my main

```



#include <iostream>
#include <string>
#include "book.h"
using namespace std;
void main()
{
       Book one;

       cin >> one;
       cout << one;
       system("pause");


}


```

---

### Post by Ferrat on 2009-03-07
first of main function is a int not a void and should return. 

also doesn't your error say what file and line??? would help knowing where to look

---

### Post by Vandorin on 2009-03-07
> **Ferrat said:**
> first of main function is a int not a void and should return. 

also doesn't your error say what file and line??? would help knowing where to look

Ok, I've got 5 errors, and they are all in the .cpp file.

errors

```


book.cpp(27) : error C2511: 'std::string Book::get_title(void)' : overloaded member function not found in 'Book'


book.h(5) : see declaration of 'Book' <=== not an error, but Im not sure what it means.


\book.cpp(30) : error C2761: 'int Book::get_chapter(void) const' : member function redeclaration not allowed


book.cpp(31) : error C2447: '{' : missing function header (old-style formal list?)



book.cpp(34) : error C2761: 'int Book::get_pagenumb(void) const' : member function redeclaration not allowed




book.cpp(35) : error C2447: '{' : missing function header (old-style formal list?)





```

---

### Post by dwhitney67 on 2009-03-07
A few of your compile errors are due to inconsistencies between your book.h and your book.cpp.

When declaring a method to be a const method in your header file, you need to do the same in the definition file.

For example in the header file:
```

...
string get_title() const;
...

```
In the .cpp file:
```

string get_title()
{
  ...
}

```
The method above is missing the const.

A couple of other notes:

1)  Never specify a "using namespace" directive in a header file.

2)  Only include header files within a .h or .cpp file which are necessary for that component to be compilable.  Avoid redundant includes (e.g. see Book.cpp) or includes which are not necessary (e.g. see Main.cpp).

3)  Always include your project's header files _first_, then followed by the system header files (e.g. iostream, string, etc.).

I could spend over an hour discussing the rationale for these recommendations, but my daughters just woke up and I need to tend to them.  For note 1, you can find gobs of articles thru Googling on the subject.


P.S.  If you are working with M$ VC++, then the "stdafx.h" file should be considered a project file.  I detest M$ for creating that damn file.  It's a thorn.

P.S.S.  Concerning note 3 above, when implementing the class defined in a header file, the first #include statement in the file (following stdafx.h), should be the header file for the class that you are implementing.

---

### Post by dwhitney67 on 2009-03-07
Also, you have semi-colons after some of the method definitions in your book.cpp file.

---

### Post by Vandorin on 2009-03-08
Now I'm getting these errors, it looks like they are the same two errors, just in different places.

```


c:\users\aaron\documents\visual studio 2008\projects\book\book\book.cpp(26) : error C2761: 'std::string Book::get_title(void) const' : member function redeclaration not allowed

c:\users\aaron\documents\visual studio 2008\projects\book\book\book.cpp(27) : error C2447: '{' : missing function header (old-style formal list?)

c:\users\aaron\documents\visual studio 2008\projects\book\book\book.cpp(30) : error C2761: 'int Book::get_chapter(void) const' : member function redeclaration not allowed

c:\users\aaron\documents\visual studio 2008\projects\book\book\book.cpp(31) : error C2447: '{' : missing function header (old-style formal list?)

c:\users\aaron\documents\visual studio 2008\projects\book\book\book.cpp(34) : error C2761: 'int Book::get_pagenumb(void) const' : member function redeclaration not allowed

c:\users\aaron\documents\visual studio 2008\projects\book\book\book.cpp(35) : error C2447: '{' : missing function header (old-style formal list?)

c:\users\aaron\documents\visual studio 2008\projects\book\book\book.cpp(77) : warning C4172: returning address of local variable or temporary

```

---

### Post by dwhitney67 on 2009-03-08
> **dwhitney67 said:**
> Also, you have semi-colons after some of the method definitions in your book.cpp file.

Did you read this?

---

### Post by Vandorin on 2009-03-08
> **dwhitney67 said:**
> Did you read this?
edit: ok i found the extra semi colons, but now I get this error, and it's one I've never gotten before.

```

bookmain.obj : error LNK2019: unresolved external symbol "class std::basic_istream<char,struct std::char_traits<char> > & __cdecl operator>>(class std::basic_istream<char,struct std::char_traits<char> > &,class Book &)" (??5@YAAAV?$basic_istream@DU?$char_traits@D@std@@@std@@AAV01@AAVBook@@@Z) referenced in function _main
C:\Users\Aaron\Documents\Visual Studio 2008\Projects\book\Debug\book.exe : fatal error LNK1120: 1 unresolved externals

```

---

### Post by dwhitney67 on 2009-03-08
Well, at least your code compiles now.  The issue you are having is with the linking of the object file(s) to produce the executable.

Please post your final code so that I can attempt to compile it on my system.

---

### Post by Vandorin on 2009-03-08
> **dwhitney67 said:**
> Well, at least your code compiles now.  The issue you are having is with the linking of the object file(s) to produce the executable.

Please post your final code so that I can attempt to compile it on my system.


Ok, here is my code

Book.h

```


#include <iostream>
#include <string>
using namespace std;
class Book
{
public:
       // operators

       friend ostream& operator << (ostream& os, const Book& aBook );
       friend istream& operator >> (istream& is, Book& aBook );

       // accessors
       string get_title() const;
       int get_chapter() const;
       int get_pagenumb() const;

       // Mutators

       void set_title (string title);
       void set_chapter (int chapter);
       void set_pagenumb (int pagenumb);
       void set (string title,int chapter,int pagenumb);

       // Constructors

       Book();
       Book( string title, int chapter, int pagenumb);

private:
       int m_chapter,m_pagenumb;
       string m_title;
};


```


Book.cpp

```


#include "book.h"
#include <iostream>
#include <string>
using namespace std;

// Default Values

Book::Book()
{
       set_title( "Please enter a Book name" );
       set_chapter (0);
       set_pagenumb (0);
}

// Constructors

Book::Book( string title, int chapter, int pagenumb )
{
       set_title (title);
       set_chapter (chapter);
       set_pagenumb (pagenumb);
}

// Accessors

string Book::get_title() const
{
       return m_title;
}
int Book::get_chapter() const
{
       return m_chapter;
}
int Book::get_pagenumb() const
{
       return m_pagenumb;
}

// Mutators

void Book::set_title ( string title )
{
       m_title = title;
}
void Book::set_chapter ( int chapter )
{
       m_chapter = chapter;
}
void Book::set_pagenumb ( int pagenumb )
{
       m_pagenumb = pagenumb;
}


// Operators

ostream& operator << (ostream& os, const Book& aBook )
{
       cout << " Name of the book you are reading :";
       os << aBook.get_title() << endl;
       cout << " The last chapter you were on was :";
       os << aBook.get_chapter() << endl;
       cout << " The last page you were on was :";
       os << aBook.get_pagenumb() << endl;
       return os;
}

istream& operator >> (istream is, Book& aBook )
{
       string t;
       int c,pn;
       cout << "Please enter The name of the book you are reading, The last chapter you were on, and the Page number you stopped at " << endl;
       is >> t >> c >> pn;
       aBook.set_title(t);
       aBook.set_chapter(c);
       aBook.set_pagenumb(pn);
       return is;
}


```

and 

bookmain.cpp

```


#include <iostream>
#include <string>
#include "book.h"
using namespace std;
int main()
{
       Book one;

       cin >> one;
       cout << one;
       system("pause");

	return 0;
}


```

---

### Post by dwhitney67 on 2009-03-08
Nothing in life is free, except perhaps the air you breathe.

Here's your code again, in a working fashion.  I stripped out the "using namespace" directives, cleaned up your header #include statements, added multiple-inclusion guard to your header file... and most importantly, I fixed your operator>> method.  You declared a local variable 'is', when in fact it should have been passed by reference.

Anyhow, avoid retyping your class definitions.  After you create a header file, copy its contents to the .cpp file.  Then remove the include guards, insert the #include for the header file you are implementing.  Then at the end of each method, remove the semi-colon and insert a pair of {} braces.  Don't forget to add the class scope operator (ie Book::) to all class members.

This approach will prevent you from having basic errors that you have experienced.

book.h
```

#ifndef BOOK_H
#define BOOK_H

#include <iostream>
#include <string>

class Book
{
public:
       // operators

       friend std::ostream& operator << (std::ostream& os, const Book& aBook );
       friend std::istream& operator >> (std::istream& is, Book& aBook );

       // accessors
       std::string get_title() const;
       int get_chapter() const;
       int get_pagenumb() const;

       // Mutators

       void set_title (std::string title);
       void set_chapter (int chapter);
       void set_pagenumb (int pagenumb);
       void set (std::string title,int chapter,int pagenumb);

       // Constructors

       Book();
       Book( std::string title, int chapter, int pagenumb);

private:
       int m_chapter,m_pagenumb;
       std::string m_title;
};

#endif

```

book.cpp:
```

#include "book.h"

// Default Values

Book::Book()
{
       set_title( "Please enter a Book name" );
       set_chapter (0);
       set_pagenumb (0);
}

// Constructors

Book::Book( std::string title, int chapter, int pagenumb )
{
       set_title (title);
       set_chapter (chapter);
       set_pagenumb (pagenumb);
}

// Accessors

std::string Book::get_title() const
{
       return m_title;
}
int Book::get_chapter() const
{
       return m_chapter;
}
int Book::get_pagenumb() const
{
       return m_pagenumb;
}

// Mutators

void Book::set_title ( std::string title )
{
       m_title = title;
}
void Book::set_chapter ( int chapter )
{
       m_chapter = chapter;
}
void Book::set_pagenumb ( int pagenumb )
{
       m_pagenumb = pagenumb;
}


// Operators

std::ostream& operator << (std::ostream& os, const Book& aBook )
{
       std::cout << " Name of the book you are reading :";
       os << aBook.get_title() << std::endl;
       std::cout << " The last chapter you were on was :";
       os << aBook.get_chapter() << std::endl;
       std::cout << " The last page you were on was :";
       os << aBook.get_pagenumb() << std::endl;
       return os;
}

std::istream& operator >> (std::istream& is, Book& aBook )
{
       std::string t;
       int c,pn;
       std::cout << "Please enter The name of the book you are reading, The last chapter you were on, and the Page number you stopped at " << std::endl;
       is >> t >> c >> pn;
       aBook.set_title(t);
       aBook.set_chapter(c);
       aBook.set_pagenumb(pn);
       return is;
}

```

bookmain.cpp:
```

#include "book.h"
#include <iostream>

int main()
{
  Book one;

  std::cin  >> one;
  std::cout << one;
  return 0;
}

```

P.S.  Now clean up the prompts in the code for user information; avoid prompting for more than one piece of information at a time.

---

### Post by Vandorin on 2009-03-08
Is there any way to make it work with using the "using namespace std;"? Because I don't really understand the method you're using. I get that you're putting, std:: in places, but simply copying your code won't help me learn :\

---

### Post by dwhitney67 on 2009-03-08
Use the "using namespace std;" if you want, but ONLY in the .cpp files.  Never specify a "using namespace" directive in a header file.

Read the information at this [link]("http://nepsweb.co.uk/pgtcpp/namespace.htm"), and conduct some other research on your own to understand what I am stating above.

---

### Post by Vandorin on 2009-03-08
> **dwhitney67 said:**
> Use the "using namespace std;" if you want, but ONLY in the .cpp files.  Never specify a "using namespace" directive in a header file.

Read the information at this [link]("http://nepsweb.co.uk/pgtcpp/namespace.htm"), and conduct some other research on your own to understand what I am stating above.

Great, thanks for all the help :D

---

### Post by Can+~ on 2009-03-08
Learn how to use a debugger and read the errors properly, most of those mistakes are pretty common, and copying them into google also helps.

---

