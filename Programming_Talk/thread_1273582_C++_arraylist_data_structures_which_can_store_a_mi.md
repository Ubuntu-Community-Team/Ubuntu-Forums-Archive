---
title: "C++ array/list data structures which can store a mixture of any data type"
date: 2009-09-23
forum: Programming Talk
---

### Post by hessiess on 2009-09-23
I need a way to create a array or list data structure in C++ which can store variables of any data type, the data structures are for storing runtime created `variables' in a tree of nodes. A variable can be created on one node, and is automatically accessible from all of the nodes above it in the tree.

I have a simple one dimensional solution to this problem by casting to pointers to void, however this is not ideal as the situation it is being used in leaves a lot of room for the deletion of pointers which are needed, the creation of dangling pointers and the introduction of memory leeks. The larger the tree of scene nodes gets, the more places a dangling pointer could be created.

[php]
#include <iostream>
#include <string.h>
#include <vector>

// struct to store a var with its name
struct var_node
{
    char *name;
    void *var;
};

// var storage array
std::vector<var_node> vars;

void* get_var(const char *name);

// new var
void new_var(const char *name, void *var)
{
    if(get_var(name) == NULL)
    {
        var_node new_node;
        new_node.name = (char*) name;
        new_node.var  = var;
        vars.push_back(new_node);
    }
}

// get var
void* get_var(const char *name)
{
    for(int i = 0; i < vars.size(); i ++)
    {
        if(!strcmp(name, vars[i].name))
            return vars[i].var;
    }
    return NULL;
}

int main()
{
// create some vars
    int  *var1 = new int(5);
    char *var2 = new char('c');
    bool *var3 = new bool(false);

// Add to vars array
    new_var("int_var",  (void*) var1);
    new_var("char_var", (void*) var2);
    new_var("bool_var", (void*) var3);

// get out of var array
    int  *var_get1 = (int*)  get_var("int_var");
    char *var_get2 = (char*) get_var("char_var");
    bool *var_get3 = (bool*) get_var("bool_var");

// display
    std::cout<<*(var_get1)<<" "<<var_get2<<" "<<*(var_get3)<<"\n";

// Clean up memory
    delete var1;
    delete var2;
    delete var3;
}
[/php]

It could also be solved by creating a base class, then deriving classes for every data type, however this breaks the `store anything' principle which I am trying to implement as classes would need to be created for user created classes.

This is part of my Quad-Ren project, currently theare is no way to move data between scene nodes besides using global variables, by changing the node structure into a tree and allowing scoped variables to be created within this tree I am trying to find a controaled way of managing data passing between nodes, if anyone has a better idea of how to solve this problem please tell me.

---

### Post by MadCow108 on 2009-09-23
you could use reference counting pointers instead of returning the raw pointers
this would forbid dangling pointers as reference counting pointers guarantee that as long at least one reference exists the memory will not be freed.
boost:shared_ptr is such a pointer

---

### Post by johnl on 2009-09-23
The "C" way to do this is with a union:

```

struct variable {
  int type;
  union {
    int i;
    char c;
    bool b;
  } value;
};

value v;

v.type = TYPE_INT;
v.value.i = 123;

```

Check out [boost::variant](http://www.boost.org/doc/libs/1_40_0/doc/html/variant.html) which is a more robust implementation of the above.

---

### Post by A_Fiachra on 2009-09-23
Dynamic type storage is available in Boost:

[http://www.boost.org/doc/libs/1_40_0/libs/ptr_container/doc/ptr_array.html](http://www.boost.org/doc/libs/1_40_0/libs/ptr_container/doc/ptr_array.html)

In general, container types are associated to a type, but you can override a template class to allow type allocation -- that, pointer types.  The problem of allocating, reference counting and destroying the pointers in storage is part of the generic storage class.

Of course you could use a loosely typed language like Perl to accomplish your task  :-)

---

### Post by johnl on 2009-09-23
Reading your question again I'm not sure a boost::variant will do this for you; the below might be able to do what you need:

```

template <typename T> variable_destroy(T* var) 
{
    delete static_cast<T*>(var);
}

class variable
{
protected:
    struct variable_data
    {
        void* data;
        void (*destructor)(void*);
        const std::type_info* info;
    }
    
    variable_data data;

public:
    template <typename T>
    void set(T* value) :
    {
        data.data = value;
        data.destructor = variable_destroy<T>;
        data.info = &(typeid(T));
    }

    template <typename T>
    T* get()
    {
        if (!is<T>())
        {
            // wrong type, throw exception
        }
        return static_cast<T*>(data.data);
    }

    template <typename T>
    is()
    {
        return (typeid(T) == *data.info);
    }
    ~variable() 
    {
        data.destructor(data.data);
    }
}

// usage:
variable v;
int*  i = new int;
*i = 120;
v.set(i);

if (v.is<int>()) {
    int* p = v.get<int>();
    
}

```

This will call the correct destructor for any classes that it stores when it goes out of scope.

---

### Post by dwhitney67 on 2009-09-23
Here's another thought, although I must admit it is not generic enough to hold any data type.  But for holding "popular" data types, as say, found in a database, it can work quite well.
```

#include <iostream>
#include <string>
#include <sstream>
#include <vector>

class GenericData
{
public:
   GenericData(const char* data) : m_data(data) {}
   GenericData(const std::string& data) : m_data(data) {}
   GenericData(char ch) : m_data(1, ch) {}
   GenericData(int val) { std::stringstream ss; ss << val; m_data = ss.str(); }

   operator std::string () const { return m_data; }
   operator char () const { return m_data[0]; }
   operator int () const { int val = 0; std::stringstream ss(m_data); ss >> val; return val; }

private:
   std::string m_data;
};

int main()
{
   std::vector<GenericData> vec;

   vec.push_back(10);
   vec.push_back("ten");
   vec.push_back("X");

   char        ch  = vec[2];
   std::string str = vec[1];
   int         val = vec[0];

   std::cout << "ch  = " << ch  << "\n"
             << "str = " << str << "\n"
             << "val = " << val
             << std::endl;
}

```

---

### Post by MadCow108 on 2009-09-23
johnl's solution seems quite nice
when you return references instead of pointer you also solve the problem with the dangling pointers

here's the fixed code:
```

template <typename T> void variable_destroy(void* var) 
{
    delete static_cast<T*>(var);
}

class variable
{
protected:
    struct variable_data
    {
        void* data;
        void (*destructor)(void*);
        const std::type_info* info;
    };
    
    variable_data data;

public:
    template <typename T>
    void set(T* value)
    {
        data.data = value;
        data.destructor = variable_destroy<T>;
        data.info = &(typeid(T));
    }

    template <typename T>
    T& get()
    {
        if (!is<T>())
        {
            // wrong type, throw exception
        }
        return *(static_cast<T*>(data.data));
    }

    template <typename T>
    bool is()
    {
        return (typeid(T) == *data.info);
    }
    ~variable() 
    {
        data.destructor(data.data);
    }
};

int main()
{
	variable v;
	int*  i = new int();
	*i = 120;
	v.set(i);

	if (v.is<int>()) {
	 int& p = v.get<int>();
	 std::cout << p << std::endl;
	}
	return 0;
}

```

of course this is just a bad reimplementation of a part of boost ptr_array what A_Fiachra already suggested

---

### Post by hessiess on 2009-09-23
Thanks, lots of code to try out:)

---

### Post by johnl on 2009-09-23
> **MadCow108 said:**
> johnl's solution seems quite nice
when you return references instead of pointer you also solve the problem with the dangling pointers

here's the fixed code:


```

return *(dynamic_cast<T&>(data.data));

```

Can you cast from a pointer to a reference like that? (data.data is a void*).  Additionally, I'm not sure you can even use dynamic_cast<> on a void* and expect a correct result.

Edit: I see you've fixed this :) Nevermind.

---

### Post by MadCow108 on 2009-09-23
yes sorry I forgot that you can only use dynamic cast on polymorphic types not basic types :)

if your using that version you should also copy the value in the set function instead of just saving the pointer to avoid that people can delete the data after they put it into the variable

---

### Post by dribeas on 2009-09-23
The implementation provided by john reminds me of boost::any, in case you want to take a look at it. There are two type of variants, with[ some differences]("http://www.boost.org/doc/libs/1_40_0/doc/html/variant/misc.html#variant.versus-any").

---

### Post by hessiess on 2009-09-24
> **MadCow108 said:**
> johnl's solution seems quite nice
when you return references instead of pointer you also solve the problem with the dangling pointers

here's the fixed code:
```

template <typename T> void variable_destroy(void* var) 
{
    delete static_cast<T*>(var);
}

class variable
{
protected:
    struct variable_data
    {
        void* data;
        void (*destructor)(void*);
        const std::type_info* info;
    };
    
    variable_data data;

public:
    template <typename T>
    void set(T* value)
    {
        data.data = value;
        data.destructor = variable_destroy<T>;
        data.info = &(typeid(T));
    }

    template <typename T>
    T& get()
    {
        if (!is<T>())
        {
            // wrong type, throw exception
        }
        return *(static_cast<T*>(data.data));
    }

    template <typename T>
    bool is()
    {
        return (typeid(T) == *data.info);
    }
    ~variable() 
    {
        data.destructor(data.data);
    }
};

int main()
{
	variable v;
	int*  i = new int();
	*i = 120;
	v.set(i);

	if (v.is<int>()) {
	 int& p = v.get<int>();
	 std::cout << p << std::endl;
	}
	return 0;
}

```

of course this is just a bad reimplementation of a part of boost ptr_array what A_Fiachra already suggested

Is theare any way to implement this so that it isn't necessary to pas the type to the get method(like set)?

---

### Post by MadCow108 on 2009-09-24
yes you pass the the parameter to the get method as reference:
```

void get(T & value)
    {
        if (!is<T>())
        {
            // wrong type, throw exception
        }
        
        value = *(static_cast<T*>(data.data));
    }

```
but its basically the same as you still need to know the type when using get, it just looks like this now:
```

int p;
v.get(p);

```
i find this less natural than the other method

---

### Post by pepperphd on 2009-09-25
> **hessiess said:**
> Is theare any way to implement this so that it isn't necessary to pas the type to the get method(like set)?

No. You're going to want to know the type of the variable you're getting back anyway aren't you?

---

### Post by nvteighen on 2009-09-25
Doing this in C or C++ implies to recreate a whole dynamic typed system on top of the language so you could store and retrieve stuff in a sane way... In some way, you'll probably be recreating a part of Python or Perl.

Another possibility would be to create a single-root class hierarchy from which you derive classes that should act as wrappers for the primitive types. There, inheritance and polymorphism would do the trick. In C, inheritance can be done through structs by using some casting tricks... if you've used GTK+, you know what I mean.

---

### Post by hessiess on 2009-09-25
> **pepperphd said:**
> No. You're going to want to know the type of the variable you're getting back anyway aren't you?

I am trying to make these variables behave as closely to `native' variables as possible, you don't have to pass the type when you use a variable you defined earlier, though it looks like i'm going to be stuck with a few macros to `pretty up' the syntax.

> 
Doing this in C or C++ implies to recreate a whole dynamic typed system on top of the language so you could store and retrieve stuff in a sane way... In some way, you'll probably be recreating a part of Python or Perl.


Exactly, I have a prototype implementation of this in Common Lisp, its trivial in comparison to whats required to emulate the behaviour in C++.

> 
Another possibility would be to create a single-root class hierarchy from which you derive classes that should act as wrappers for the primitive types. There, inheritance and polymorphism would do the trick. In C, inheritance can be done through structs by using some casting tricks... if you've used GTK+, you know what I mean.


I did mention this technique in the OP and its something that I'm trying to avoid doing as it would add a substantial amount of code which dousen't actually do anything besides wrap primitive types. If the primitive types were objects it would be a lot easier.

---

### Post by MadCow108 on 2009-09-25
> **hessiess said:**
> I am trying to make these variables behave as closely to `native' variables as possible, you don't have to pass the type when you use a variable you defined earlier

Isn't that exactly what my earlier suggestion with passing a reference to the get method does?

and I wouldn't say using macros "pretty up the syntax".
They more obfuscate what really goes on. The template syntax is normal c++ syntax and every programmers should be familiar enough with it.

---

### Post by issih on 2009-09-25
I am confused by all this...its interesting as a technical exercise, but under what circumstances is a list that can store "anything" actually useful? On retrieval of item x in a list you'll have no idea what methods it supports, so given the lack of duck typing within c++ what are you going to do with it.

If you DO know what type it is ahead of retrieval, then why not just store each different type in its own array?

I just don't get how this kind of data structure is useful in 99% of circumstances

That said perhaps this is the 1% where it is required, I don't know, but personally I'd spend 30 minutes working out if redesigning the code could avoid the need for something the language doesn't really support

Hope that helps

---

### Post by MadCow108 on 2009-09-25
> **issih said:**
> I am confused by all this...its interesting as a technical exercise, but under what circumstances is a list that can store "anything" actually useful? On retrieval of item x in a list you'll have no idea what methods it supports, so given the lack of duck typing within c++ what are you going to do with it.

you can solve this by using reflection techniques.
here an example reflection framework:
[http://root.cern.ch/drupal/content/reflex](http://root.cern.ch/drupal/content/reflex)

---

### Post by hessiess on 2009-09-25
> **issih said:**
> I am confused by all this...its interesting as a technical exercise, but under what circumstances is a list that can store "anything" actually useful? On retrieval of item x in a list you'll have no idea what methods it supports, so given the lack of duck typing within c++ what are you going to do with it.

If you DO know what type it is ahead of retrieval, then why not just store each different type in its own array?

I just don't get how this kind of data structure is useful in 99% of circumstances

That said perhaps this is the 1% where it is required, I don't know, but personally I'd spend 30 minutes working out if redesigning the code could avoid the need for something the language doesn't really support

Hope that helps


As stated in the Op, it is going to be used as part of my Graphics engine, Quad-Ren. It is a object oriented, scene node based graphics engine. To controal how a scene node reacts to user input an event receiver can be attached to it, howaever theare is currently no way of moveing data from one node to another. I am implementing a system which alows runtime created `variables' to be attached to a node in the node tree, and will be lexically scoped to be readable and writeable only from the nodes above the node where the variable is registered in the scene node tree. Because its a generic libuary, the system neads to be able to store values of any type.

---

### Post by nvteighen on 2009-09-25
> **hessiess said:**
> 
I did mention this technique in the OP and its something that I'm trying to avoid doing as it would add a substantial amount of code which dousen't actually do anything besides wrap primitive types. If the primitive types were objects it would be a lot easier.

Hm... but you can make them objects! Wrap them into a class hierarchy and you'll get it. I don't see why that solution will be worse. And then you could even use a thin wrapper for std::vector to use those "types" in a better fashion.

> **hessiess said:**
> As stated in the Op, it is going to be used as part of my Graphics engine, Quad-Ren. It is a object oriented, scene node based graphics engine. To controal how a scene node reacts to user input an event receiver can be attached to it, howaever theare is currently no way of moveing data from one node to another. I am implementing a system which alows runtime created `variables' to be attached to a node in the node tree, and will be lexically scoped to be readable and writeable only from the nodes above the node where the variable is registered in the scene node tree. Because its a generic libuary, the system neads to be able to store values of any type.

If that's what you seek... you're one step into developing a new programming language (Domain Specific, it seems). And there you should be careful: One thing is implementing a language in another... another thing is then to have the result-language be embedded into the source-language. That, which is incredibly simple to do in Lisp (and which is mainly the universal path to development "in/on" Lisp), in C or C++ may be a real nightmere because of lack of symbolic analysis.

---

### Post by hessiess on 2009-09-25
> **nvteighen said:**
> If that's what you seek... you're one step into developing a new programming language (Domain Specific, it seems). And there you should be careful: One thing is implementing a language in another... another thing is then to have the result-language be embedded into the source-language. That, which is incredibly simple to do in Lisp (and which is mainly the universal path to development "in/on" Lisp), in C or C++ may be a real nightmere because of lack of symbolic analysis.

I never thought of it as being a domain specific language... thanks for the warning.

What I currently have as a test implementation isn't too bad, one macro to hide the pointer creation (to prevent it being edited directly, deleted etc), if the pointer creation could be moved inside the class the macro could go too.

[php]
#include<typeinfo>
#include<iostream>
#include<vector>
#include<string.h>

namespace qr_internal
{
    template <typename T> void variable_destroy(void* var) 
    {
        delete static_cast<T*>(var);
    }
}

namespace qr
{
    class variable
    {
    protected:
        struct variable_data
        {
            void* data;
            void (*destructor)(void*);
            const std::type_info* info;
            const char *name;
        };
        
        std::vector<variable_data> data;

    public:
        template <typename T>
        void create(T* value, const char *name)
        {
            // check if var already exists here
            variable_data new_data;
            new_data.data = value;
            new_data.destructor = qr_internal::variable_destroy<T>;
            new_data.info = &(typeid(T));
            new_data.name=name;
            this->data.push_back(new_data);
        }

        template <typename T>
        void set(T value, const char *name)
        {
            for(int i = 0; i < data.size(); i++)
            {
            // Re-Add type check
                if(!strcmp(name, data[i].name))
                {
                    T* pointer = static_cast<T*>(data[i].data);
                    *pointer = value;
                }
            }
        }

        template <typename T>
        T& get(const char *name)
        {
            for(int i = 0; i < data.size(); i++)
            {
                if(!strcmp(name, data[i].name))
                    return *(static_cast<T*>(data[i].data));
            }
        }

    // clean up
        ~variable() 
        {
            for(int i = 0; i < data.size(); i++)
            {
                data[i].destructor(data[i].data);
            }
        }
    };
}

#define qr_new_var(type, name) type* name__ = new type();\
            v.create(name__, #name)

int main()
{
    qr::variable v;

// create var i and set to 45
    qr_new_var(int, i);
    v.set(45, "i");

// display
    std::cout<<v.get<int>("i")<<std::endl;

// increment i
    int f = v.get<int>("i");
    v.set(f + 1, "i");

// display
    std::cout<<v.get<int>("i")<<std::endl;
}
[/php]

---

### Post by MadCow108 on 2009-09-25
this will not work:[PHP]
  void create(T* value, const char *name) 
        { 
            // check if var already exists here 
            variable_data new_data; 
            new_data.data = value; 
            new_data.destructor = qr_internal::variable_destroy<T>; 
            new_data.info = &(typeid(T)); 
//here
            new_data.name=name; 
//here
            this->data.push_back(new_data); 
        }[/PHP]

you are only copying the pointer not the string, use strcpy (or better strings)

also it seems your building an inefficient associative container out of a vector
why not use maps maps instead? their associative container from begin with (also sorted, meaning efficient retrieval instead of your O(N) )

also its missing the type check in the get method.
if its all set at compile time it should at least be activated in debugging mode.

---

