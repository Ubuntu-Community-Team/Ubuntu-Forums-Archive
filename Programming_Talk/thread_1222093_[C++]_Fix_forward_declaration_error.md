---
title: "[C++] Fix forward declaration error"
date: 2009-07-24
forum: Programming Talk
---

### Post by wbest on 2009-07-24
I keep getting errors like :

```
db_column.cpp: In member function ‘RSL_TW::XDBColumn& RSL_TW::XDBColumn::operator=(const RSL_TW::XDBColumn&)’:
db_column.cpp:50: error: invalid use of incomplete type ‘struct XDBColumnImpl’
db_column.h:22: error: forward declaration of ‘struct XDBColumnImpl’
db_column.cpp:51: error: invalid use of incomplete type ‘struct XDBColumnImpl’
db_column.h:22: error: forward declaration of ‘struct XDBColumnImpl’
```

I'd like to get rid of the forward declaration errors.  I'm not really sure why I'm getting the incomplete type errors, though, I'm sure my code is write.
Here's some from db_column.h:

```
//I added this
//-Bill
class XDBColumnImpl;
 
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
 
  X_PRIVATE_PTR_MUTABLE(XDBColumnImpl, impl);

```

Now that line after my comments is the forward declaration error.  The problem is that if I don't have that line, the compiler freaks on the line with X_PRIVATE saying XDBColumnImpl has not been declared.

What X_PRIVATE_PTR_MUTABLE(foo, bar) is set foo as the type for bar.


This is from db_column.cpp

```
XDBColumn& XDBColumn::operator=(const XDBColumn& other) 
{ 
  if (&other == this) 
    return *this; 
 
  REF_RELEASE(ref_impl()); 
  REF_ADD(other.impl()); 
 
  ref_impl() = other.impl(); 
  return *this; 
}
```

REF_RELEASE is line 50 (as noted in the errors).

I already added a lot, and I'm not sure if anyone will even look at this.  But if you want to help, and you would like more info, I'd be happy to provide it.

---

### Post by MadCow108 on 2009-07-24
is XDBColumnImpl defined properly somewhere?

class XDBColumnImpl; is not sufficient hence probably the incomplete type error.

---

### Post by wbest on 2009-07-24
Yeah, I found where it is, and included the header.  So now it works.

But I'm a little wary of doing so, as it is originally windows code, and worked fine there.
So I'll do this, but I may add a conditional like #ifndef WIN32 or something.

---

