---
title: "C++: Position of private user-defined classes within user-defined classes"
date: 2010-04-02
forum: Programming Talk
---

### Post by gnometorule on 2010-04-02
I'm still digging into the innards of C++, but I am sure one of the usual pros will probably be able to explain what's wrong below. Thanks much for helping me out.

For those with the book, example at end of post is the longish "class String" example from Stroustrup, "The C++ Programming Language", end of chapter 11, as entered by me. There is also a main.cpp/String.cpp file, with which g++ compilation as in

g++ -ansi -pedantic main.cpp String.hpp String.cpp -o string

succeeds fine.

As you see, class String is organized as:

class String{
     class Cref; (defined)
public:
     (declarations and inlined membed functions, accessing
       public members of Srep; and private members of Cref)
private:
struct Srep; (defined)
     Srep* rep;
};

If you re-order the file as in:

class String{
public:
     (declarations and inlined membed functions, accessing
       public members of Srep; and private members of Cref)
private:
     class Cref; (defined)
struct Srep; (defined)
     Srep* rep;
};

g++ compilation results in these error messages:

String.hpp:55: error: ISO C++ forbids declaration of &#8216;Cref&#8217; with no type
String.hpp:55: error: expected &#8216;;&#8217; before &#8216;operator&#8217;
String.hpp:56: error: expected &#8216;;&#8217; before &#8216;char&#8217;
String.hpp:55: error: ISO C++ forbids declaration of &#8216;Cref&#8217; with no type
String.hpp:55: error: expected &#8216;;&#8217; before &#8216;operator&#8217;
String.hpp:56: error: expected &#8216;;&#8217; before &#8216;char&#8217;
In file included from String.cpp:3:
String.hpp:55: error: ISO C++ forbids declaration of &#8216;Cref&#8217; with no type
String.hpp:55: error: expected &#8216;;&#8217; before &#8216;operator&#8217;
String.hpp:56: error: expected &#8216;;&#8217; before &#8216;char&#8217;

The error messages relate to the line defining the inlined "Cref..." member function; commenting that line out compiles fine. The actual error is of course

String.hpp:55: error: ISO C++ forbids declaration of &#8216;Cref&#8217; with no type;

the other errors are ancilliary to this problem. I am confused by this. I thought the position/order of private and public classes was irrelelant, aka, a public member can access private members defined later. It works fine for struct Srep, which has all public members; making members public in class Cref though has no effect, so that is probably not it.

```

#ifndef STRING_HPP_
#define STRING_HPP_

#include <cstring>

class String{

        class Cref{

        friend class String;
                // defining vars
                String& s;
                int i;

                // constructors
                Cref(String& ss, int ii): s(ss), i(ii) {}
                Cref(const Cref& r): s(r.s), i(r.i) {}
                Cref();         // never used so not defined

        public:
                operator char() const { s.check(i); return s.read(i); }
                void operator=(char c) { s.write(i, c); }
        };  // **** end definition class Cref

public:
        // exception class
        class Range {};
        // constructors & destructor
        String();
        String(const char*);
        String(const String&);
        String& operator=(const char*);
        String& operator=(const String&);
        ~String();

        // member queries
        int size() const { return rep->sz; }

        // overloading the operator[] & helper functions
        void check(int i) const { if (i<0 || rep->sz<=i) throw Range(); }

        char read(int i) const { return rep->s[i]; }
        char write(int i, char c) { rep = rep->get_own_copy(); rep->s[i]=c; }

        Cref operator[](int i) { check(i); return Cref(*this, i); }
        char operator[](int i) const { check(i); return rep->s[i]; }


private:
        struct Srep{
                char* s;        // pointer to elements
                int sz;         // number of elements
                int n;          // reference count

                Srep(int nsz, const char* p)
                {
                        n = 1;
                        sz = nsz;
                        s = new char[sz+1];
                        std::strcpy(s,p);
                }

                ~Srep() { delete[] s; }

                Srep* get_own_copy()   // clone as necessary
                {
                        if (n==1) return this;
                        n--;
                        return new Srep(sz,s);
                }

                void assign(int nsz, const char* p)
                {
                        if (sz != nsz){
                                delete[] s;
                                sz = nsz;
                                s = new char[sz+1];
                        }
                        strcpy(s,p);
                }

        private:   // restrict copy/copy assignment
                Srep(const Srep&);
                Srep& operator=(const Srep&);
        };
        // ***** end definition of Srep *****************************

        Srep* rep;

}; // ***** end declaration of class String

#endif


```

---

### Post by dwhitney67 on 2010-04-02
All you need to do is tell the compiler to expect a class named Cref to be defined shortly.  You can do this with a forward declaration.  Without the declaration, the only way to satisfy the compiler is to fully define Cref before attempting to use it.

Something like:
```

...

class String
{
   class Cref;

public:
   String();

   // ...

   Cref operator[](int i) { check(); return Cref(*this, i); }

private:
   class Cref
   {
   public:
      Cref(String& ss, int ii) : s(ss), i(ii) {}
      Cref(const Cref& other) : s(other.s), i(other.i) {}

   private:
      Cref();   // declared, but not implemented

      friend class String;
      String& s;
      int     i;
   };

   // ...

   void check() const {}

   // ...
};

```

Btw, for private classes, I personally do not see the need to make the parent class a "friend".  Defining public member data (a la struct) is fine.

P.S.  I defined check() as a private method; I don't see why it would need to be publicly accessible.

---

### Post by gnometorule on 2010-04-02
Thanks much. Yes, forward declaration works. But why is that not necessary for Srep - this compiles fine too:

class String{
class Cref; (declaration only)
public:
(other)
private:
class Cref (defined)
struct Srep (defined)
Srep rep*
};

---

### Post by gnometorule on 2010-04-02
**** REPLY REMOVED by author. My apologies for not testing hard enough (was a typo in my code) **********

---

### Post by gnometorule on 2010-04-02
...answer is: because Srep also declares a pointer to a variable of its type (rep), so space is allocated etc, which is then used; while Cref doesn't. 

Gonna take a brown bag and close this thread...again, thanks. :)

---

