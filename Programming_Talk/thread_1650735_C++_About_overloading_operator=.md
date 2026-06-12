---
title: "C++: About overloading operator="
date: 2010-12-22
forum: Programming Talk
---

### Post by koala114 on 2010-12-22
```
StringBad & StringBad::operator=(const StringBad & st)
{
if (this == &st)
return *this; 
delete [] str;
len = st.len;
str = new char [len + 1]; 
std::strcpy(str, st.str); // copy the string
return *this; 
}
```

```
StringBad headline1(“Celery Stalks at Midnight”);
StringBad test = headline1
```

Will delete [] str; in overloading operator= free the unallocated memory for test?

---

### Post by worksofcraft on 2010-12-22
> **koala114 said:**
> ```
StringBad & StringBad::operator=(const StringBad & st)
{
if (this == &st)
return *this; 
delete [] str;
len = st.len;
str = new char [len + 1]; 
std::strcpy(str, st.str); // copy the string
return *this; 
}
```

```
StringBad headline1(“Celery Stalks at Midnight”);
StringBad test = headline1
```

Will delete [] str; in overloading operator= free the unallocated memory for test?

You need to make sure that str points to something that was allocated with new in the first place or test it for NULL and also there is no guarantee that st.len accurately refelects the length that strcpy will copy... so I think there are a load of hazards in this code.

---

### Post by koala114 on 2010-12-22
Yes, I understand. The point is that str of test doesn't even point to any location when program runs into ```
StringBad test = headline1
```, but the operator= member function at work.
So delete [] str; will free unallocated memory.

Next, the program proceeds like a copy constructor, allocating enough space for the new string and then copying the string from the right-hand object to the new location.

Anyway, thanks for your reply:p

---

### Post by MadCow108 on 2010-12-22
in this situation the copy constructor is called, not the assignment operator

as this constructs a new object you should not even have to delete str as it does not yet exist.

In the assignment operator you do have to handle it
but when you always initialize str to an empty string (not NULL) in all constructors you can keep the the assigment operator the same for empty and non-empty strings

---

### Post by dwhitney67 on 2010-12-22
Expanding on MadCow's comments, the OP should realize the following:
```

StringBad headline1(&#8220;Celery Stalks at Midnight&#8221;);

StringBad test1 = headline1;   // copy-contructor is called

StringBad test2;               // default constructor is called (if allowed)

test2 = test1;                 // operator=() is called

```

Of course, I do not recommend using char arrays to store strings in C++; you would be better off using the std::string.


P.S.  You default constructor should be something like:
```

#include <algorithm>   // for std::copy()

StringBad(const char* s = 0)
   : len(0),
     str(0)
{
   if (s)
   {
      len = std::strlen(s);
      str = new char[len + 1];
      std::copy(s, s + len, str);
   }
}

```

---

### Post by MadCow108 on 2010-12-22
I would not initialize str to NULL as dwhitney did. 

consider this:
```

class MyString {
  String() : str(0) {}
  size_t Length() { return strlen(str); } //crash when this default constructed

  // correct:
  size_t Length() {
    // this check required for every single member function which uses str!
    if (!s)
      return 0;
    else
     return strlen(str);
  }
};

```

the longer version of Length() can be avoided when you initialize str to a valid buffer in every constructor:
```

class MyString {
  String() { str = new char[MIN_BUF_SIZE]; str[0] = 0; }
  size_t Length() { return strlen(str); } // ok
};

```
as str is now a valid string in any object the member function implementation becomes simpler and less error prone

---

### Post by dwhitney67 on 2010-12-22
Madcow, why not just maintain a 'len' member data object?  Return that value from Length().

You also indicated that you would not initialize str to NULL, but that is exactly what you did.

Also, I do not subscribe to the notion that it is best practice to allocate memory for str if the StringBad object is constructed with a null-string.  That is a waste of memory.

The following is my take on the class:
```

class StringBad
{
public:
   StringBad(const char* s = 0)
      : len(0),
        str(0)
   {
      if (s)
      {
         len = std::strlen(s);
         str = new char[len + 1];
         std::copy(s, s + len, str);
      }
   }

   StringBad(const StringBad& other)
      : len(other.len),
        str(0)
   {
      if (other.str)
      {
         str = new char[len + 1];
         std::copy(other.str, other.str + len, str);
      }
   }

   StringBad& operator=(const StringBad& rhs)
   {
      if (this != &rhs)
      {
         delete [] str;
         len = rhs.len;
         str = new char[len + 1];
         std::copy(rhs.str, rhs.str + len, str);
      }

      return *this;
   }

   ~StringBad()
   {
      delete [] str;
      len = 0;
      str = 0;
   }

   size_t size() const   { return len; }
   size_t length() const { return len; }

   const char* data() const { return str; }

   friend std::ostream& operator<<(std::ostream& os, const StringBad& sb)
   {
      os << (sb.str ? sb.str : "NULL") << " (" << sb.len << ")";
      return os;
   }

private:
   size_t len;
   char*  str;
};


```

---

### Post by worksofcraft on 2010-12-22
> **dwhitney67 said:**
> Madcow, why not just maintain a 'len' member data object?  Return that value from Length().
...
Also, I do not subscribe to the notion that it is best practice to allocate memory for str if the StringBad object is constructed with a null-string.  That is a waste of memory.


I would agree that recording the length of allocated memory would be a good idea as this can be used to guard against string overruns and determine when it is time to reallocate the memory. However if you want to get the strings length keep in mind that a terminating \0 could be inserted in that allocated memory to give a much shorter string.

IMO making sure you always have some valid memory as Madcow suggests is a good idea, because a string with no memory would be a pointless oddity and not worth wasting code memory on initializing and testing for NULL pointers that would be needed to handle it :shock:

ANyway the real reason I replied was to this:

> So delete [] str; will free unallocated memory.

No sadly you can only free memory that was allocated from the heap in the first place :(

Back when computer memory was much more scarce you could create "overlay" segments so that things like code used for initialization could be liberated from memory once they had been used. I wouldn't be surprised if that capability yet languishes deep down in the more arcane command line switches of the loader but I have not bothered to look for it because it's easier to go buy some more memory. :D

---

### Post by MadCow108 on 2010-12-22
> **dwhitney67 said:**
> Madcow, why not just maintain a 'len' member data object?  Return that value from Length().

ok length was a bad example. Say the find member function using strstr internally.
You can't preconstruct the result of this in the constructor.

> 
You also indicated that you would not initialize str to NULL, but that is exactly what you did.

I did it in my do-not example. the lower one is how I would do it

> 
Also, I do not subscribe to the notion that it is best practice to allocate memory for str if the StringBad object is constructed with a null-string.  That is a waste of memory.

1 byte overhead (+ allocator overhead) compared to 4/8 byte and only when I construct loads of empty strings this plays a role.
A classical case of premature optimization.
Worse yet it even downgrade performance as you have to check for NULL on every member function call (but also neglectable)
I'd rather have my program bug free(er) and maintainable instead of using 10%th less memory in the worst case (which rarely happens, construction of null strings is almost always an error)

---

