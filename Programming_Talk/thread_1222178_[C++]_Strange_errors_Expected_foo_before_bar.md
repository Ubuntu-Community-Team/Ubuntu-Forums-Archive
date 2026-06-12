---
title: "[C++] Strange errors Expected foo before bar"
date: 2009-07-24
forum: Programming Talk
---

### Post by wbest on 2009-07-24
I'm getting the following error:

> db_column.h:45: error: expected ‘;’ before ‘*’ token
db_column.h:45: error: expected `;' before ‘XDBColumnImpl’
db_column.h:45: error: expected ‘;’ before ‘*’ token
db_column.h:45: error: expected `;' before ‘XDBColumnImpl’
db_column.h:45: error: expected ‘;’ before ‘*’ token
db_column.h:45: error: expected `;' before ‘private’
db_column.h:45: error: expected ‘;’ before ‘*’ token
db_column.h:46: error: expected ‘;’ before ‘*’ token
db_column.h:46: error: expected `;' before ‘XDBColumnImpl’
db_column.h:46: error: expected ‘;’ before ‘*’ token
db_column.h:52: error: expected `)' before ‘*’ token


But I don't see what it has to do with the code (line 45 is high lighted)
```
class DBCORE_API XDBColumn 
#ifdef USE_COMPAT 
    : public XCompatColumn 
#endif 
{ 
  friend class XDBColumnImpl; 
 
  X_PRIVATE_PTR_MUTABLE(XDBColumnImpl, impl); 
  DB_GET_IMPL(XDBColumnImpl, impl); 
 
  friend DBCORE_API std::ostream& operator<<(std::ostream& os, const XDBColumn& col); 
```

XDBColumnImpl is defined in db_column_impl.h, which I have included.

X_PRIVATE_PTR_MUTABLE(foo, bar) is supposed to set foo as the type for bar.

Now, this code all works on windows, so why am I getting these errors?

---

### Post by dwhitney67 on 2009-07-24
You are getting these errors because GCC is probably a stricter compiler than windows.  Who knows?

Anyhow, it would most helpful if you would post the contents of db_column.h, up to line 45, including all header files it may include.

P.S.  I am not a big fan of macros.  It warps a language.

---

### Post by wbest on 2009-07-24
Here's the code to line 48, 45 is again bolded:

```
 // ---------------------------------------------------------------------------- 
// Richard Lee 
// 10/2002 
// ---------------------------------------------------------------------------- 
// 01.16.03 : RSL : Added Variable 
// ---------------------------------------------------------------------------- 
#ifndef __RSL_TW_DB_COLUMN_H_ 
#define __RSL_TW_DB_COLUMN_H_ 
 
// ---------------------------------------------------------------------------- 
// ---------------------------------------------------------------------------- 
#include <core/variant.h> 
#include <ostream> 
#include "db_core.h" 
#include "db_mac.h" 
#include "db_status.h" 
#include "compat_column.h"
//This needs to be added in Linux
//Not sure why it worked in Windows without it
//But I need to add it to define XDBColumnImpl
//-bill
#ifndef WIN32 
#    include "db_column_impl.h"
#endif
 
// ---------------------------------------------------------------------------- 
// ---------------------------------------------------------------------------- 
START_NAMESPACE(_SYSNAME_SPACE_) 
 
// ---------------------------------------------------------------------------- 
// ---------------------------------------------------------------------------- 
class XDBColumn; 
DBCORE_API std::ostream& operator<<(std::ostream& os, const XDBColumn& col); 
 
//! \brief User interface to column object 
//!  
//! Assignment or copy ctor creates shared implementation. 
class DBCORE_API XDBColumn 
#ifdef USE_COMPAT 
    : public XCompatColumn 
#endif 
{ 
  friend class XDBColumnImpl; 
 
**  X_PRIVATE_PTR_MUTABLE(XDBColumnImpl, impl); **
  DB_GET_IMPL(XDBColumnImpl, impl); 
 
  friend DBCORE_API std::ostream& operator<<(std::ostream& os, const XDBColumn& col); 
```

---

### Post by dwhitney67 on 2009-07-24
You last post is most unhelpful.

Pretend I you a question, and I tell you my problem is with this line of code:
```

...
SOME_SILLY_MACRO(myObject);   // g++ complains about this line... WHY???
...

```
What would be your reaction to this query?

I bet you would want to see where SOME_SILLY_MACRO is defined.  You probably would want to also see what other definitions are defined before it.

Now, with this in mind, can you repost your code?

---

### Post by MadCow108 on 2009-07-24
it could help if we knew what the X_PRIVATE_PTR_MUTABLE macro acctualy does (I mean code no description)

also as a missing include solved the last problem I would search for further missing headers

---

### Post by wbest on 2009-07-24
Well, you did only ask for db_column.h up to line 45.

Plus the code for X_PRIVATE_PTR_MUTABLE hasn't failed yet.
Anyway, here it is, for the approval of the midnight society...

```
#define X_PRIVATE_PTR_MUTABLE(T,A)                          \ 
    protected:                                              \ 
            T*& ref_##A() const         { return pv_##A;  } \ 
            T*& A() const               { return pv_##A;  } \ 
            T*& A(REF_PARAM) const      { return pv_##A;  } \ 
    private:                                                \ 
      mutable T*   pv_##A;
```

X_PRIVATE_PTR_MUTABLE is from an included file.

---

### Post by dwhitney67 on 2009-07-24
> **wbest said:**
> Well, you did only ask for db_column.h up to line 45.

And for a listing of the include files!

> **wbest said:**
> 
```
#define X_PRIVATE_PTR_MUTABLE(T,A)                          \ 
    protected:                                              \ 
            T*& ref_##A() const         { return pv_##A;  } \ 
            T*& A() const               { return pv_##A;  } \ 
            T*& A(REF_PARAM) const      { return pv_##A;  } \ 
    private:                                                \ 
      mutable T*   pv_##A;
```

Your error might be because you have a semi-colon after the macro usage.  Remove it, and hopefully all will be well.

```

  X_PRIVATE_PTR_MUTABLE(XDBColumnImpl, impl);   // <--- Take out that semi-colon.

```

> **wbest said:**
> 
X_PRIVATE_PTR_MUTABLE is from an included file.
Exactly my point!  In the future, show the include file where these type of things are defined.

Remember, you have the code at your fingertips, we don't.

---

### Post by wbest on 2009-07-24
> **dwhitney67 said:**
> And for a listing of the include files!
Apologies.  I thought the list at the beginning of my first posted code was sufficient.

There are a lot of included files that include other files, and I was afraid it may get too long so I only noted those.

> 
Your error might be because you have a semi-colon after the macro usage.  Remove it, and hopefully all will be well.

```

  X_PRIVATE_PTR_MUTABLE(XDBColumnImpl, impl);   // <--- Take out that semi-colon.

```
That solved my problem.  Lets hope that doesn't kill the rest of it.

I don't really understand why that fixed it, but it did.

---

### Post by dwhitney67 on 2009-07-24
> **wbest said:**
> ...

I don't really understand why that fixed it, but it did.

I think the fix worked because otherwise you would have a statement ending with a double semi-colon.

I just finished working on a project where one of the developers had a nasty habit of placing a semi-colon in methods that had no implementation (see example below).  Using the -ansi, or perhaps, -pedantic, cause an error to surface
```

class Foo
{
public:
   ...

   virtual void someMethod() {;}   // to be implemented by sub-class(es)

   ...
};

```

---

### Post by wbest on 2009-07-24
No wait, I think I was compiling the wrong file!
I'm an idiot.

Anyway, I'm still getting the error.

Sorry, about that.  I must have slipped up in the backtrack in Terminal or mis wrote my notes.

No, its still broke.

---

### Post by dwhitney67 on 2009-07-24
What is REF_PARAM defined to be??  I am wagering that your problem lies with it.

The following compiles fine:
```

#define X_PRIVATE_PTR_MUTABLE(T,A)                         \
    protected:                                             \
            T*& ref_##A() const         { return pv_##A; } \
            T*& A() const               { return pv_##A; } \
            /* T*& A(REF_PARAM) const      { return pv_##A; } */ \
    private:                                               \
      mutable T*   pv_##A;


class FriendClass;

class Foo
{
   friend class FriendClass;

   X_PRIVATE_PTR_MUTABLE(FriendClass, impl)
};

int main(){}

```

Btw, when you compile, use the -E option so that you can see what code the preprocessor is generating.
```

g++ -E YourSource.cpp

```

---

### Post by mdurham on 2009-07-24
Although the semicolon may not cause a problem here, I agree with dwhitney67. I think that there should not be a semicolon at the end of the macro. This could cause a problem in future code.
Cheers, Mike

---

