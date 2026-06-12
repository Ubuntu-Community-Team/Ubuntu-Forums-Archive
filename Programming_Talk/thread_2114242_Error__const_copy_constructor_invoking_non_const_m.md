---
title: "Error : const copy constructor invoking non const methods"
date: 2013-02-09
forum: Programming Talk
---

### Post by dany2704 on 2013-02-09
I have modified the copy constructor as constant in order to fix the compilation error.Again the compiler throws an error,*because  calling a non-const method from a const method.*
```


String.h

class String 
{ 
        private: 
                char *_text; 
                friend class String_Iterator; 
        public: 
                // ctors and dtor 
                explicit String ();                      
                explicit String (char *); 
                explicit String (int ); 
                String (String const & );               
                ~String(); 
 
                ///////////////// 
                // conversions: 
                ///////////////// 
                //  to C-like type char * 
                operator char *() {return _text;} 
 
                ///////////////// 
                // overloads: 
                ///////////////// 
                // assignment String = String 
                String &operator=(String &); 
} 
 
String.c 
 
String::String() 
{ 
        _text = new char[1024]; 
} 
String::String(char *ch) 
{ 
        if (ch == NULL ) 
        { 
                // if input char* is empty - allocate short buffer 
                // and set it to "" 
                _text = new char[2]; 
                strcpy(_text, ""); 
        } 
        else 
        { 
 
                _text = new char[strlen(ch) + 1]; 
 
                if(_text) 
                         strcpy(_text, ch); 
                else 
                { 
                        _text = new char[2]; 
                        strcpy(_text, ""); 
                } 
        } 
 
} 
String::String(int iLen) 
{ 
        _text = new char[iLen+1]; 
} 
String::String(String const& string)//modified copy cons as const 
{ 
       _text = new char[string.length() + 1]; 
 
       strcpy(_text,string); 
} 
String::~String() 
{ 
        delete[] _text; 
} 
String &String::operator=(String &ptrStr) 
{ 
 
        delete[] _text; 
        _text = new char[ptrStr.length() + 1]; 
 
        strcpy(_text, ptrStr); 
        return *this; 
} 
String &String::operator=(char *ch) 
{ 
        delete[] _text; 
        _text = new char[strlen(ch) + 1]; 
 
        strcpy(_text, ch); 
        return *this; 
} 
```**Error: **
String.c: In copy constructor 'String::String(const String&)': 
String.c:49: error: passing 'const String' as 'this' argument of 'int String::length()' discards qualifiers 
String.c:51: error: passing 'const String' as 'this' argument of 'String::operator char*()' discards qualifiers 
String.c:51: error: invalid conversion from 'char*' to 'const char*' 
String.c:51: error:   initializing argument 2 of 'char* strcpy(char*, const char*)' 
make: *** [all] Error 1 
Please check and help me to resolve the issue ..
Thanks for looking into this

---

### Post by spjackson on 2013-02-09
> **dany2704 said:**
> 
String.c: In copy constructor 'String::String(const String&)': 
String.c:49: error: passing 'const String' as 'this' argument of 'int String::length()' discards qualifiers 
String.c:51: error: passing 'const String' as 'this' argument of 'String::operator char*()' discards qualifiers 
String.c:51: error: invalid conversion from 'char*' to 'const char*' 
String.c:51: error:   initializing argument 2 of 'char* strcpy(char*, const char*)' 
make: *** [all] Error 1 

You don't show the declaration of length(). I'm guessing that it's something like:
```

class String {
  public:
    int length();
};

```
You want:
```

class String {
  public:
    int length() const;
};

```
This says that length() does not modify its object, so it can be called on const object.

The conversion operator to char * has probably two faults:
```

class String {
  public:
    operator char *() {return _text;}
};

```
First, again since the function is not declared const, you are saying that the function may change its object. Second, do you really want it to return a pointer to an address that can be written to? I would guess not. So you probably want:
```

class String {
  public:
    operator const char *() const {return _text;}
};

```
Your assignment operator should also have a const parameter.

Finally, what's wrong with std::string?

---

### Post by dany2704 on 2013-02-13
Thank you!!! your solution fix the problem

---

