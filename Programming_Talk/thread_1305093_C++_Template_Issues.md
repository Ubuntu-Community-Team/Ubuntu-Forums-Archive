---
title: "C++ Template Issues"
date: 2009-10-29
forum: Programming Talk
---

### Post by shynthriir on 2009-10-29
I'm messing around with C++ templates and everything compiles fine, but when my compiler is linking, I get this error:

```
../objs/database_class.o: In function `Database_Class::Delete_Entry(unsigned int)':
database_class.cpp:(.text+0x43): undefined reference to `Linked_List_Class<Entry_List_Type>::Delete_Item(unsigned int)'
../objs/database_class.o: In function `Database_Class::Add_New_Entry()':
database_class.cpp:(.text+0x6c): undefined reference to `Linked_List_Class<Entry_List_Type>::Add_New_Item()'
```

Code Snippets are as follows:

```
template <typename Generic_Item_Type>
int Linked_List_Class<Generic_Item_Type>::Add_New_Item()
{
  if (Current == NULL)
  {
    Current = new Generic_Item_Type;
    Current -> Previous = NULL;
  }
  else
  {
    Current -> Next = new Generic_Item_Type;
    Current -> Next -> Previous = Current;
    Current = Current -> Next;
  }

  Current -> Next = NULL;

  return 0;
}
```

```
template <typename Generic_Item_Type>
class Linked_List_Class
{
private:
  Generic_Item_Type *Current;

  int Goto_First_Item();
  int Goto_Last_Item();

public:

  Linked_List_Class()
  {
    Current = NULL;
  }

  int Add_New_Item();
  int Delete_Item(unsigned int Item_Index);
  Generic_Item_Type* Get_Current();

};

```

```
Linked_List_Class <Entry_List_Type> List;
```

Other functions in the header are also in my code, but this should be enough to give you a gist of it all. I feel like my function definitions are not properly set up, but I'm not sure why.

---

### Post by dwhitney67 on 2009-10-29
It is hard to tell from the code snippets where you have actually implemented the templated class functions.

These, believe it or not, need to be implemented within the header file, or via a "trick", included within the header file.

In a nutshell...

MyTemplate.h:
```

template <class T>
class MyTemplate
{
public:
   MyTemplate();

   void myFunction();
};

#include "MyTemplate.impl"

```

MyTemplate.impl:
```

template <class T>
MyTemplate<T>::MyTemplate()
{
   ...
}

template <class T>
void MyTemplate<T>::myFunction()
{
   ...
}

```
If you do not want to employ the ".impl" way, then merely implement the template constructor(s), destructor, and method(s) within the header file itself... either within the class declaration or below the class declaration.

---

### Post by shynthriir on 2009-10-29
Okay, that is something I didn't know.

Because it is implimented this way, I am guessing that the .impl file does not get compiled by itself, but more like it get piled along with the files the header file is #included in.

Is my assumption correct?

---

### Post by dwhitney67 on 2009-10-30
> **shynthriir said:**
> Okay, that is something I didn't know.

Because it is implimented this way, I am guessing that the .impl file does not get compiled by itself, but more like it get piled along with the files the header file is #included in.

Is my assumption correct?
You're right; it does not get compiled directly.  The only place the impl file is included is within the header file that declares the templated class.

The impl file itself does *not* include its respective header file either!  If it requires other header files (eg iostream), then it is ok to include them within the impl file.

---

### Post by dribeas on 2009-10-30
> **shynthriir said:**
> Okay, that is something I didn't know.

Because it is implimented this way, I am guessing that the .impl file does not get compiled by itself, but more like it get piled along with the files the header file is #included in.

Is my assumption correct?

Not quite. Templates are compiled at the place of instantiation, that is when it is first used for each given type within the current compilation unit. Even if you include the whole template, if you do not use it it won't get compiled.

And that goes into a higher level of detail, if you instantiate a given class template with a type and you only use part of the interface, only that part of the code will be compiled and the rest of the methods will not be compiled.

---

