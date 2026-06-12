---
title: "question on boost shared_ptr"
date: 2011-04-22
forum: Programming Talk
---

### Post by jebsector on 2011-04-22
Why does code like the following later cause segmentation faults?  It doesn't if i switch the shared_ptr to a regular pointer and code that way..

```

boost::shared_ptr<somevar> var = boost::shared_ptr<somevar>(new somevar());
vector<somevar> vec = vector<somevar>();

void doSomething() {
   var.reset(new somevar());
   var.one = 10;
   var.two = 42;
   var.three = 82;
   addToVector(*var);  
}

void addToVector(somevar v) {
   vec.push_back(v);
}

```

then if you wrote a main method to use the two functions and then iterate and use the variables in the vector, you get the segmentation fault due to dereferencing..  but i don't know why that would happen if you pass in a reference to the function instead of the pointer - shouldn't it be a copy of the data?

---

### Post by MadCow108 on 2011-04-22
please provide a working example reproducing your problem or describe it better
the code you provided works fine if you fix the syntax error.

---

### Post by dwhitney67 on 2011-04-22
> **jebsector said:**
> Why does code like the following later cause segmentation faults?  It doesn't if i switch the shared_ptr to a regular pointer and code that way..

```

boost::shared_ptr<somevar> var = boost::shared_ptr<somevar>(new somevar());
vector<somevar> vec = vector<somevar>();

void doSomething() {
   var.reset(new somevar());
   var.one = 10;
   var.two = 42;
   var.three = 82;
   addToVector(*var);  
}

void addToVector(somevar v) {
   vec.push_back(v);
}

```

then if you wrote a main method to use the two functions and then iterate and use the variables in the vector, you get the segmentation fault due to dereferencing..  but i don't know why that would happen if you pass in a reference to the function instead of the pointer - shouldn't it be a copy of the data?

I don't quite understand why you are using a shared pointer, if it is a *copy* of the object contained within the shared pointer that you wish to store within the vector.

Perhaps you meant to store shared-pointers within the vector??

And as far as assigning to fields 'one', 'two', and 'three' of var... what is that??  Perhaps you mean to dereference the shared-pointer rather than use a '.'?

Consider the following:
```

struct SomeType
{
   int one, two, three;
};

typedef boost::shared_ptr<SomeType> SomeTypePtr;

...
std::vector<SomeTypePtr> vec;
SomeTypePtr              var(new SomeType);

var->one   = 10;
var->two   = 20;
var->three = 30;

vec.push_back(var);

```

---

### Post by jebsector on 2011-04-22
Sorry - I'll clarify.  I'm fiddling around in c++, and so in part of doing that I'm parsing out source code of another language.

Originally I was storing pointers in the vectors.  That changed to shared_ptr.  when i finished the portion of the code i wanted to test with shared_ptr stored in the vectors, i later wound up with segfault on output at the end, to validate it parsed ok.  I tried storing just objects in the vectors, I tried copy constructors (which has an interesting detail), operator overloading, and passing in shared_ptr to methods in different ways.  They all seem to produce the same end.  Here's the important parts of the code so I'm not drowning you in source:

main.cpp
```

#include <cstdlib>
#include <string>
#include <fstream>
#include <iostream>
#include <boost/regex.hpp>
#include <boost/regex.h>
#include <boost/regex_fwd.hpp>
#include <boost/algorithm/string/trim.hpp>
#include <boost/shared_ptr.hpp>
#include "class_struct.h"
#include "method.h"
#include "params.h"
#include "var.h"

class translator {
  private:
int CLASS_LINE;
    int END_OF_CLASS_LINE;
    boost::shared_ptr<class_struct> map;
    //boost::shared_ptr<method> m;
    int currentLine;
    bool withinComment;
    bool withinClassVars;
    bool withinClass;
    bool withinMethod;
    bool withinMethodDeclaration;


    int validate(std::string line);
    int check_include_section(std::string line);
    int check_end_comment(std::string line);
    int check_class_vars_section(std::string line);
    int check_method_signature(std::string line);
    int parse_next_method_signature(std::string line);
    std::string parse_method_modifier(std::string line, boost::shared_ptr<method> m);
    std::string parse_method_parameters(std::string line, boost::shared_ptr<method> m);
    std::string parse_return_type(std::string line, boost::shared_ptr<method> m);
    int finish_method_signature(std::string line);
    int parse_method_code(std::string line);
public:
    translator();
    void parseFile(char** argv);
};

using namespace std;

int main(int argc, char** argv) {
   translator *trans = new translator();
   trans->parseFile(argv);
   return 0;
}

//...parseFile loops over lines and parses incrementally via regex and string searching
//here's what it does at the end
cout << "output.txt" << endl;
cout << map->output() << endl;
cout << endl;

//...validate is a control structure, it passes control to methods based on where we are at in parsing..

//...check include section works fine, already tested.

//...check class vars section isn't fully implemented yet and is ignored by the process

//...check method signature:
  //checks that it is a valid method signature
  //does the following:
  boost::shared_ptr<method> m1 = boost::shared_ptr<method>(new method());
  //the above used to be a class-level variable, just moved it to see if it would make a difference.  it didn't.
  //..calls parse_method_modifier(line)
  //..calls parse_method_parameters(line)
  //..calls parse_return_type(line)
  //..sets a couple of control variables
  map->add_method(*m1); //remember i've changed these around to try and resolve..
  return 1;
//...

//method parse_method_modifier(string line, boost::shared_ptr<method> m) 
//just sets a public/private modifier
m->setPublicModifier(true);
//or throws an exception if it encounters any errors in parsing

//parse_method_parameters(string line, boost::shared_ptr<method> m)
/* this is where the difficulty i'm having starts.. */
//it parses through the line correctly, and basically does the following:
c = line.find("(");
//...
m->setName(line.substr(0, c));
line = line.substr(c+1);
boost::algorithm::trim(line);
while (line.find(",") != -1) {
   c = line.find(",");
   int w = line.find(" ");
   string param_type = line.substr(0, w);
   string param_var = line.substr(w, c-w);
   boost::algorithm::trim(param_var);
   boost::shared_ptr<var> v(new var());
   if (param_var.find("$") == -1) {
      //...
      v->setVariableIsPointer(true);
   }
   else {
      v->setVariableIsPointer(false);
   }
   v->setVariableName(param_var);
   v->setVariableClassname(param_type);
   boost::shared_ptr<params> p(new params());
   p->setType(param_type);
   p->setVar(*v); //changed due to tinkering with getting rid of segfault
   m->addParameter(*p); //diddo
   line = line.substr(c+1);
   boost::algorithm::trim(line);
}
c = line.find(")");
//...
int w = line.find(" ");
if (w > c) { /* empty (void) parameters. do nothing for default */ }
else {
   string param_type = line.substr(0, w);
   string param_var = line.substr(w, c-w);
   boost::algorithm::trim(param_var);
   if (param_var.find("$") == -1) {
      //...
      v->setVariableIsPointer(true);
   }
   else {
      v->setVariableIsPointer(false);
   }
   v->setVariableName(param_var);
   v->setVariableClassname(param_type);
   boost::shared_ptr<params> p(new params());
   p->setType(param_type);
   p->setVar(*v); //changed
   m->addParameter(*p); //used to be m->addParameter(p);
}
line = line.substr(c+1);
boost::algorithm::trim(line);
return line;

//...rest of class..

```

class_struct.cpp.  The segfault occurs here, when main.cpp calls the output method down towards the bottom.  I don't know at what point the memory gets dereferenced, though; and worse, which memory is getting dereferenced and why.
```

#include "class_struct.h"

using namespace std;

class_struct::class_struct() {
    classname = "";
    extends = "";
    implements = vector<string>();
    includes = vector<string>();
    errors = vector<boost::shared_ptr<error_line> >();
    methods = vector<method>();
}

void class_struct::update_classname(string name) {
    classname = name;
}

void class_struct::update_extends(string name) {
    extends = name;
}

void class_struct::update_implements(vector<string> impl) {
    implements = vector<string>(impl);
}

void class_struct::add_implements(string name) {
    implements.push_back(name);
}

void class_struct::remove_implements(string name) {
    int i;
    for (i = 0; i < implements.size(); i++) {
        string a = implements[i];
        if (a.compare(name) == 0)  {
            break;
        }
    }
    implements.erase(implements.begin()+i);
}

void class_struct::add_includes(string name) {
    includes.push_back(name);
}

void class_struct::remove_includes(string name) {
    int i;
    for (i = 0; i < includes.size(); i++) {
        string a = includes[i];
        if (a.compare(name) == 0) {
            break;
        }
    }
    includes.erase(includes.begin()+i);
}

void class_struct::add_error(int line, string msg) {
    boost::shared_ptr<error_line> e(new error_line(line, msg));
    errors.push_back(e);
}

std::vector<boost::shared_ptr<error_line> > class_struct::get_errors() {
    return errors;
}

void class_struct::remove_error(int line) {
    int i;
    for (i = 0; i < errors.size(); i++) {
        boost::shared_ptr<error_line> a = errors[i];
        if (a->line == line) {
            break;
        }
    }
    errors.erase(errors.begin()+i);
}

void class_struct::add_method(const method& m) {
    cout << "pushing back.." << endl;
    methods.push_back(m);
}

void class_struct::remove_method(const method& m) {
    //TODO: remove a method from list
}

vector<method> class_struct::get_methods() {
    return methods;
}

string class_struct::output() {
    string a = "";
    int i;
    for (i = 0; i < includes.size(); i++) {
        a.append("#include \""+includes[i]+"\"\n");
    }
    a.append("\n");
    a.append("class "+classname+" extends "+extends+" ");
    for (i = 0; i < implements.size(); i++) {
        a.append(implements[i]);
        if (i+1 < implements.size()) {
            a.append(",");
        }
    }
    a.append(" { ");
    a.append("\n");
    //cout << "getting methods.." << endl;
    for (i = 0; i < methods.size(); i++) {
        //cout << "one";
        method m = methods[i];
        //cout << "two";
        a.append("method: name->");
        a.append(m.name);
        //cout << "three"<< endl;
        a.append(" , start->");
        a.append(""+m.startLine);
        a.append(", end->");
        a.append(""+m.endLine);
        a.append(", modifier->");
        a.append(m.public_modifier == 1 ? "public" : "private");
        a.append(", return type->");
        a.append(m.return_type);
        a.append(", pointer->");
        a.append(m.return_ispointer == 1 ? "*" : "$");
        a.append("\n");

/* this is where the seg fault happens, after it tries to get parameters that have been somehow dereferenced.. */

        //cout << "segmentation spot.." << a << endl;
        for (int c = 0; c < m.parameters.size(); c++) {
            params p = m.parameters[i];
            a.append("method param->");
            a.append(p.type);
            a.append(", ");
            var v = *(p.variable);
            a.append("var->");
            a.append(v.varClassname);
            a.append(",");
            a.append(v.varName);
            a.append(",");
            a.append(v.varIsPointer == 1 ? "*" : "$");
            a.append("\n");
        }
        a.append("\n");
    }
    a.append("}");
    a.append("\n\n");

    for (i = 0; i < errors.size(); i++) {
        a.append("error->");
        int j = errors[i]->line;
        a.append(boost::lexical_cast<string, int>(errors[i]->line));
        a.append(": ");
        a.append(errors[i]->msg);
        a.append("\n");
    }
    return a;
}

class_struct::~class_struct() {
    errors.clear();
    implements.clear();
    includes.clear();
    methods.clear();
}

```

method.cpp (started fiddling around with copy constructors and such.  was interesting to see when things are getting copied, at least..)
This is where i can get the segfault to either happen or not happen..
```

#include "method.h"

using namespace std;

method::method() {
    startLine = 0;
    endLine = 0;
    closeLine = 0;
    name = "";
    parameters = vector<params>();
    return_type = "void";
    return_ispointer = false;
    public_modifier = false;
}

method::method(const method& m) {
    cout << "copying method &.." << endl;
    startLine = m.startLine;
    endLine = m.endLine;
    closeLine = m.closeLine;
    name = m.name;
    //parameters = vector<params>(m.parameters); 
    //uncomment above line to get segfault to occur
    
    //just debugging junk
    for (int i = 0; i < m.parameters.size(); i++) {
        cout << m.parameters[i].type << ", name-"<< m.parameters[i].variable->varName << endl;
    }
    return_type = m.return_type;
    return_ispointer = m.return_ispointer;
    public_modifier = m.public_modifier;
}

void method::setStart(int l) {
    startLine = l;
}

void method::setEnd(int l) {
    endLine = l;
}

void method::setName(string n) {
    name = n;
}

void method::addParameter(const params& p) {
    cout << "adding parameter.." << p.type << endl;
    parameters.push_back(p);
}

void method::removeParameter(const params& p) {
    //todo: implement
}

void method::setReturnType(string n) {
    return_type = n;
}

void method::setReturnIsPointer(bool ip) {
    return_ispointer = ip;
}

void method::setPublicModifier(bool p) {
    public_modifier = p;
}

method::~method() {
    parameters.clear();
}

```

params.cpp:
```

#include "params.h"

using namespace std;

params::params() {
    type = "";
    variable = boost::shared_ptr<var>(new var());
}

params::params(const params& p) {
    cout << "copying params &..";
    type = p.type;
    variable = boost::shared_ptr<var>(new var());
    variable->varClassname = p.variable->varClassname;
    variable->varIsPointer = p.variable->varIsPointer;
    variable->varName = p.variable->varName;
}

params& params::operator =(const params& p) {
    cout << "overriding equals in params..";
    type = p.type;
    variable = boost::shared_ptr<var>(new var());
    variable->varClassname = p.variable->varClassname;
    variable->varIsPointer = p.variable->varIsPointer;
    variable->varName = p.variable->varName;
}

void params::setType(string n) {
    type = n;
}

void params::setVar(const var& v) {
    variable = boost::shared_ptr<var>(new var(v));
}

params::~params() {
}

```

var.cpp:
```

#include "var.h"

using namespace std;

var::var() {
    varName = "";
    varClassname = "";
    varIsPointer = false;
}

var::var(const var& v) {
    varName = v.varName;
    varClassname = v.varClassname;
    varIsPointer = v.varIsPointer;
}

var& var::operator =(const var& v) {
    varName = v.varName;
    varClassname = v.varClassname;
    varIsPointer = v.varIsPointer;
}

void var::setVariableName(string n) {
    varName = n;
}

void var::setVariableClassname(string n) {
    varClassname = n;
}

void var::setVariableIsPointer(bool p) {
    varIsPointer = p;
}

var::~var() {
}

```

Uh, sorry for the long post and regards, not wishing this was java or anything it's a c++ learning curve.

I'll probably have some additional general questions on shared_ptr usage.  Pointers by themselves weren't so bad, just the worry about memory leaks and dangling pointers and such...

Thanks for the help.

---

### Post by MadCow108 on 2011-04-22
have you tried debugging with valgrind and gdb?

---

### Post by dwhitney67 on 2011-04-22
> **jebsector said:**
> 
Thanks for the help.

The whole point of using a shared pointer is not to reap the benefits of automatic deletion when the pointer usage is complete; the main benefit is that it is SHARED.  (sorry to shout).

In some of your classes, you have implemented copy-constructors and overloaded operator=() methods that make a copy of the shared pointer.  Why?

If you want to ensure your pointers are properly disposed of, then implemented something in your class destructors in lieu of using the shared pointer.

And to further your knowledge of C++, the initialization of member data of a class is done before entering the constructor's body.  For example:
```

class Foo
{
public:
   Foo(const int val1, const int val2);

   ...
private:
   int value1;
   int value2;
};

Foo:Foo(const int val1, const int val2) :
   value1(val1),      // this is where you begin initializing member data
   value2(val2)
{
   // body of constructor

   // by the time the flow of execution is here, the object should be constructed.
   // of course, there are always cases where data may need to be configured,
   // or set up to a certain state.
}

```


P.S.
```

typedef boost::shared_ptr<SomeType> SomeTypePtr;
...
SomeTypePtr p1;
...
{
   SomeTypePtr p2(new SomeType);
   ...
   p1 = p2; // voila!  p2 is being shared with p1.
}

// by the time we're here, p2 falls out of scope, and thus is destroyed;
// but alas, the pointer contained within still lives because it is
// referenced by p1.

```

---

### Post by jebsector on 2011-04-22
this is what i get out of ddd (i couldn't get gdb to work with arguments from netbeans, don't know how to use it effectively from the command-line)

[HTML]
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff7b74423 in std::basic_string<char, std::char_traits<char>, std::allocator<char> >::assign(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) () from /usr/lib/libstdc++.so.6
(gdb)
[/HTML]

What i really needed was a better understanding of shared_ptr.  I'll do like you said tomorrow and see where that gets me.

---

### Post by dwhitney67 on 2011-04-22
> **jebsector said:**
> this is what i get out of ddd (i couldn't get gdb to work with arguments from netbeans, don't know how to use it effectively from the command-line)

[HTML]
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff7b74423 in std::basic_string<char, std::char_traits<char>, std::allocator<char> >::assign(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) () from /usr/lib/libstdc++.so.6
(gdb)
[/HTML]

There's not much to go on there, other than you have a problem assigning to an std::string.

If you don't know how to use the debugger in NetBeans, then perhaps you shouldn't be using NB.  Use vim or gedit to develop your app, and then ddd (which btw, is a GUI front-end to gdb) to debug it.

What transpired before the seg-fault?

---

### Post by jebsector on 2011-04-22
It's printing an output statement at the end of the main loop.  The string is built in class_struct.  Right before the seg fault, it copies over method, then the params.  In this case, it has one param, so it copies that over.  Then when i access it in the class_struct output sequence, i get the seg fault..

I thought I was getting it from improperly copying a vector.  If it's from copying a string that may get me a little closer - i was putting all my attention to the vectors. 

I have a couple of other questions too though - you already tought me quite a bit in just one post that i didn't see from online tutorials - what allows me to create an object without using the new keyword?  it's all over the place in boost, i don't know if that's a static constructor or what.  And should that be used in place of a regular constructor and using new to create an object or does it really matter?

And, when should i use typedef?  looks useful for places where i'm repetitively using namespaces and such, are there other situations?  Also, is every class in c++ effectively public?

Thanks a bunch for your input..

---

### Post by MadCow108 on 2011-04-23
after the crash type *backtrace full* into ddd/gdb to get more information
(if its multi threaded *thread apply all bt*)

also use valgrind:
```
valgrind ./executable arg1 arg2
```
for memory leak checking
```
valgrind --leakcheck=full ./executable arg1 arg2
```

it could give more information on where the problem really is.

---

### Post by dwhitney67 on 2011-04-23
Within params.h (and .cpp), I do not see the necessity to use a boost shared_ptr.  But perhaps I'm missing something.

What I did see through your code is a blatant disregard for efficiency.  In a lot of places, you are making copies of objects, without taking advantage of relying on references.  Perhaps you come from a Java background?

For example, look at the following:
```

void class_struct::update_classname(string name) {
    classname = name;
}

```
This would be better written as the following, to avoid making a deep-copy of the input parameter:
```

void class_struct::update_classname(**const string&** name) {
    classname = name;
}

```
Consider the following random code I pulled from your code listings; each performs a copy:
```

includes = vector<string>();

string a = implements[i];

method m = methods[i];

```
In the last statement above, is it safe to assume that the "method" copy-constructor is implemented properly?  Regardless, I would question why the necessity to make a copy.

As for your incessant use of assign() in the output method, consider using a stringstream object; for example:
```

#include <sstream>
...

std::stringstream ss;

for (size_t i = 0; i < includes.size(); ++i)
{
   ss << "#include \"" << includes[i] << "\"\n";
}

ss << "\n"
   << "class " << classname << " extends " << extends << " ";

for (size_t i = 0; i < implements.size(); ++i)
{
   ss << implements[i]);

   if (i + 1 < implements.size())
   {
      ss << ","
   }
}

...

return ss.str();   // return the string contained with the stringstream

```
Note that I used size_t above; that is the data type returned by the size() method.  Compile your program with the -Wall compiler option to see the warnings!

And to answer your questions...
> 
what allows me to create an object without using the new keyword?

Objects can be created on the stack (ie without using new), or on the heap (using new).  When you are creating large and/or copious amounts of objects that will reside in a container, it is best to allocate them on the heap.

Two examples:
```

class Foo
{
   ...
};
...
Foo foo1;    // created on the stack
Foo* foo2 = new Foo;   // created on the heap
...
delete foo2;   // objects on the heap *should* be destroyed/freed

```

> 
... i don't know if that's a static constructor or what. And should that be used in place of a regular constructor and using new to create an object or does it really matter...?

One can have a default constructor that accepts no parameters, another that accepts parameters, and a copy-constructor.  These are never declared static.  Sometimes a constructor that accepts parameters may default the parameters to some value, thus offering the user the ability to treat that constructor as if it where the default constructor.  For example:
```

Foo:Foo(int value = 0)
  : val(value)
{
}
...
Foo foo1(10);   // passing 10 as the value
Foo foo2;       // using default value of zero

```

> 
when should i use typedef?

I personally use typedef to define a new data type, so that I do not have to continue typing over and over again the same lengthy type definitions.  For example, the following is a lot to type, and thus I would rather do it only once!
```

typedef std::map<std::string, boost::shared_ptr<SomeClassName> > ReferenceMap;

ReferenceMap myMap;

...

void someMethod(ReferenceMap& refMap)
{
}

```

> 
is every class in c++ effectively public?

No.  In C++, there are class and struct; with a class, all attributes are by default defined as private, unless otherwise noted, and with a struct, all attributes are by default defined as public, unless otherwise noted.  Aside from these minor differences, a class and a struct are identical in every other way.


P.S.  My suggestion to you is to re-write your project to take advantage of what I discussed above.  Try to program a little, and then test your assumptions.  Don't develop a 1000 lines of code, and then test.

---

### Post by jebsector on 2011-04-23
I reprogrammed it with proper initialization and shared_ptr usage.

Here's the segfault err with backtrace from ddd:

[HTML]
Program received signal SIGSEGV, Segmentation fault.
0x0000000000404ba0 in boost::detail::atomic_increment (pw=0x29) at ../../boost_1_46_1/boost/smart_ptr/detail/sp_counted_base_gcc_x86.hpp:66
(gdb) backtrace full
#0  0x0000000000404ba0 in boost::detail::atomic_increment (pw=0x29) at ../../boost_1_46_1/boost/smart_ptr/detail/sp_counted_base_gcc_x86.hpp:66
No locals.
#1  0x0000000000404bc2 in boost::detail::sp_counted_base::add_ref_copy (this=0x21) at ../../boost_1_46_1/boost/smart_ptr/detail/sp_counted_base_gcc_x86.hpp:133
No locals.
#2  0x0000000000404cbb in boost::detail::shared_count::shared_count (this=0x7fffffffe368, r=...) at ../../boost_1_46_1/boost/smart_ptr/detail/shared_count.hpp:228
No locals.
#3  0x0000000000404f71 in boost::shared_ptr<params>::shared_ptr (this=0x7fffffffe360) at ../../boost_1_46_1/boost/smart_ptr/shared_ptr.hpp:169
No locals.
#4  0x000000000041b5b6 in class_struct::output (this=0x67efa0) at class_struct.cpp:145
        p = {px = 0x6a5980, pn = {pi_ = 0x21}}
        v = {varName = {static npos = <optimized out>, _M_dataplus = {<std::allocator<char>> = {<__gnu_cxx::new_allocator<char>> = {<No data fields>}, <No data fields>}, _M_p = 0x6a5fe8 "!"}}, varClassname = {static npos = <optimized out>, _M_dataplus = {<std::allocator<char>> = {<__gnu_cxx::new_allocator<char>> = {<No data fields>}, <No data fields>}, _M_p = 0x6a62d8 ""}}, varIsPointer = 216}
        c = 0
        m = {px = 0x6a51f0, pn = {pi_ = 0x6a57b0}}
        a = {static npos = <optimized out>, _M_dataplus = {<std::allocator<char>> = {<__gnu_cxx::new_allocator<char>> = {<No data fields>}, <No data fields>}, _M_p = 0x43d401 "*\\.[0-9]+"}}
        i = 1
        a = <error reading variable a (DWARF-2 expression error: DW_OP_reg operations must be used either alone or in conjuction with DW_OP_piece or DW_OP_bit_piece.)>
#5  0x0000000000408c26 in translator::parseFile (this=0x65a010, argv=0x7fffffffe7f8) at main.cpp:324
        line = {static npos = <optimized out>, _M_dataplus = {<std::allocator<char>> = {<__gnu_cxx::new_allocator<char>> = {<No data fields>}, <No data fields>}, _M_p = 0x6a62d8 ""}}
        source = <incomplete type>
        lines = {<std::_Vector_base<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >> = {_M_impl = {<std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >> = {<__gnu_cxx::new_allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >> = {<No data fields>}, <No data fields>}, _M_start = 0x6a6180, _M_finish = 0x6a6278, _M_end_of_storage = 0x6a6280}}, <No data fields>}
        hasErrors = true
#6  0x0000000000405ab9 in main (argc=2, argv=0x7fffffffe7f8) at main.cpp:174
        trans = 0x65a010
(gdb) 
[/HTML]

---

### Post by jebsector on 2011-04-23
here's the output() method in class_struct.cpp:

```

string class_struct::output() {
    string a = "";
    int i;
    for (i = 0; i < includes.size(); i++) {
        a.append("#include \""+includes[i]+"\"\n");
    }
    a.append("\n");
    a.append("class "+classname+" extends "+extends+" ");
    for (i = 0; i < implements.size(); i++) {
        a.append(implements[i]);
        if (i+1 < implements.size()) {
            a.append(",");
        }
    }
    a.append(" { ");
    a.append("\n");
    //cout << "getting methods.." << endl;
    for (i = 0; i < methods.size(); i++) {
        //cout << "one";
        _method m = methods[i];
        //cout << "two";
        a.append("method: name->");
        a.append(m->name);
        //cout << "three"<< endl;
        a.append(" , start->");
        a.append(""+m->startLine);
        a.append(", end->");
        a.append(""+m->endLine);
        a.append(", modifier->");
        a.append(m->public_modifier == 1 ? "public" : "private");
        a.append(", return type->");
        a.append(m->return_type);
        a.append(", pointer->");
        a.append(m->return_ispointer == 1 ? "*" : "$");
        a.append("\n");
        //cout << "segmentation spot.." << a << endl;
        for (int c = 0; c < m->parameters.size(); c++) {
            _params p = m->parameters[i];
            a.append("method param->");
            a.append(p->type);
            a.append(", ");
            var v = *(p->variable);
            a.append("var->");
            a.append(v.varClassname);
            a.append(",");
            a.append(v.varName);
            a.append(",");
            a.append(v.varIsPointer == 1 ? "*" : "$");
            a.append("\n");
        }
        a.append("\n");
    }
    a.append("}");
    a.append("\n\n");

    for (i = 0; i < errors.size(); i++) {
        a.append("error->");
        int j = errors[i]->line;
        a.append(boost::lexical_cast<string, int>(errors[i]->line));
        a.append(": ");
        a.append(errors[i]->msg);
        a.append("\n");
    }
    return a;
}

```

---

### Post by jebsector on 2011-04-23
geez....

it was actually caused by _params p = m->parameters[i] instead of _params p = m->parameters[c].  I was using the wrong loop's int and so parameters was out of bounds..

Makes me feel stupid enough.  Why the seg fault instead of some exception?j

---

### Post by MadCow108 on 2011-04-23
> **jebsector said:**
> geez....

it was actually caused by _params p = m->parameters[i] instead of _params p = m->parameters[c].  I was using the wrong loop's int and so parameters was out of bounds..

Makes me feel stupid enough.  Why the seg fault instead of some exception?j

the [] operator does not do any boundary checkout.
you have to use the at() method for that

(btw with valgrind would have found this bug immediately)

---

### Post by jebsector on 2011-04-23
dwhitney:

yeah, i come from a java/php background.  i'm picking up c++ do do what i should have done to start with (switched from cs to cis in college due to needing a business background)

I'll change around the code today as per your last post, and repost the results.  btw - the code still seems to run faster than java even with the inefficiencies.  

so far the changes i've made were to fix the vector out of bounds that was causing the seg fault, instantiating classes correctly, and switching back to using shared_ptr like i was before the seg fault mess.  I also started using typedef in places where i was using a long namespace'd object.  

be back in a while.  thanks for all the info so far..

---

### Post by jebsector on 2011-04-23
Here's the updated code for feedback..

class_struct.cpp:
```

#include <sstream>
#include "class_struct.h"

using namespace std;

class_struct::class_struct() :
        classname(""),
        extends(""),
        implements(vector<string>()),
        includes(vector<string>()),
        errors(vector<_error_line>()),
        methods(vector<_method>())
{
    //empty
}

class_struct::class_struct(const class_struct& c) {
    classname = c.classname;
    extends = c.extends;
    includes = c.includes;
    implements = c.implements;
    errors = c.errors;
    methods = c.methods;
}

void class_struct::update_classname(const string& name) {
    classname = name;
}

void class_struct::update_extends(const string& name) {
    extends = name;
}

void class_struct::update_implements(const vector<string>& impl) {
    implements = vector<string>(impl);
}

void class_struct::add_implements(const string& name) {
    implements.push_back(name);
}

void class_struct::remove_implements(const string& name) {
    int i;
    for (i = 0; i < implements.size(); i++) {
        string a = implements[i];
        if (a.compare(name) == 0)  {
            break;
        }
    }
    implements.erase(implements.begin()+i);
}

void class_struct::add_includes(const string& name) {
    includes.push_back(name);
}

void class_struct::remove_includes(const string& name) {
    int i;
    for (i = 0; i < includes.size(); i++) {
        string a = includes[i];
        if (a.compare(name) == 0) {
            break;
        }
    }
    includes.erase(includes.begin()+i);
}

void class_struct::add_error(int line, const string& msg) {
    boost::shared_ptr<error_line> e(new error_line(line, msg));
    errors.push_back(e);
}

const std::vector<_error_line>& class_struct::get_errors() {
    return errors;
}

void class_struct::remove_error(int line) {
    int i;
    for (i = 0; i < errors.size(); i++) {
        boost::shared_ptr<error_line> a = errors[i];
        if (a->line == line) {
            break;
        }
    }
    errors.erase(errors.begin()+i);
}

void class_struct::add_method(const _method& m) {
    cout << "pushing back.." << endl;
    methods.push_back(m);
}

void class_struct::remove_method(const _method& m) {
    //TODO: remove a method from list
}

vector<_method> class_struct::get_methods() {
    return methods;
}

string class_struct::output() {
    stringstream ss;
    for (size_t i = 0; i < includes.size(); i++) {
        ss << "#include \"" << includes.at(i) << "\"\n";
    }
    ss << "\n" << "class " << classname << " extends " << extends << " ";
    for (size_t i = 0; i < implements.size(); i++) {
        ss << implements.at(i);
        if (i+1 < implements.size()) {
            ss << ", ";
        }
    }
    ss << " { " << "\n";
    for (size_t i = 0; i < methods.size(); i++) {
        _method m = methods.at(i);
        ss << "method: name->" << m->name << " , start->" << m->startLine << ", end->";
        ss << m->endLine << ", modifier->";
        m->public_modifier == 1 ? ss << "public" : ss << "private";
        ss << ", return type->" << m->return_type << ", pointer->";
        m->return_ispointer == 1 ? ss << "*" : ss << "$";
        ss << "\n";
        for (size_t c = 0; c < m->parameters.size(); c++) {
            _params p = m->parameters.at(c);
            ss << "method param->" << p->type << ", var->" << p->variable->varClassname;
            ss << " name->" << p->variable->varName << ", ";
            p->variable->varIsPointer == 1 ? ss << "*" : ss << "$";
            ss << "\n";
        }
        ss << "\n";
    }
    ss << "}" << "\n\n";

    for (size_t i = 0; i < errors.size(); i++) {
        _error_line e = errors.at(i);
        ss << "error->" << e->line << ": " << e->msg << "\n";
    }

    return ss.str();
}

class_struct::~class_struct() {
    errors.clear();
    implements.clear();
    includes.clear();
    methods.clear();
}

```

class_struct.h:
```

#ifndef CLASS_STRUCT_H
#define	CLASS_STRUCT_H

#include <string>
#include <vector>
#include <boost/shared_ptr.hpp>
#include "error_line.h"
#include "method.h"

typedef boost::shared_ptr<error_line> _error_line;
typedef boost::shared_ptr<method> _method;
typedef boost::shared_ptr<params> _params;
typedef boost::shared_ptr<var> _var;

class class_struct {
private:
    std::string classname;
    std::string extends;
    std::vector<std::string> implements;
    std::vector<std::string> includes;
    std::vector<_error_line> errors;
    std::vector<_method> methods;
public:
    class_struct();
    class_struct(const class_struct& c);
    ~class_struct();
    void update_classname(const std::string& name);
    void update_extends(const std::string& name);
    void update_implements(const std::vector<std::string>& impl);
    void add_implements(const std::string& name);
    void remove_implements(const std::string& name);
    void add_includes(const std::string& name);
    void remove_includes(const std::string& name);
    void add_error(int line, const std::string& msg);
    const std::vector<_error_line>& get_errors();
    void remove_error(int line);
    void add_method(const _method& m);
    void remove_method(const _method& m);
    std::vector<_method> get_methods();

    std::string output();
};

#endif	/* CLASS_STRUCT_H */

```

method.cpp:
```

#include "method.h"

using namespace std;

method::method() :
startLine(0),
endLine(0),
closeLine(0),
name(""),
parameters(vector<param>()),
return_type("void"),
return_ispointer(false),
public_modifier(false)
{

}

method::method(const method& m) {
    cout << "copying method &.." << endl;
    startLine = m.startLine;
    endLine = m.endLine;
    closeLine = m.closeLine;
    name = m.name;
    //parameters = vector<params>(m.parameters);
    return_type = m.return_type;
    return_ispointer = m.return_ispointer;
    public_modifier = m.public_modifier;
}

void method::setStart(int l) {
    startLine = l;
}

void method::setEnd(int l) {
    endLine = l;
}

void method::setName(const string& n) {
    name = n;
}

void method::addParameter(param p) {
    parameters.push_back(p);
}

void method::removeParameter(param p) {
    //todo: implement
}

void method::setReturnType(const string& n) {
    return_type = n;
}

void method::setReturnIsPointer(bool ip) {
    return_ispointer = ip;
}

void method::setPublicModifier(bool p) {
    public_modifier = p;
}

method::~method() {
    parameters.clear();
}

```

params.cpp:
```

#include "params.h"

using namespace std;

params::params() {
    type = "";
    variable = boost::shared_ptr<var>(new var());
}

params::params(const params& p) {
    cout << "copying params &..";
    type = p.type;
    variable = boost::shared_ptr<var>(new var());
    variable->varClassname = p.variable->varClassname;
    variable->varIsPointer = p.variable->varIsPointer;
    variable->varName = p.variable->varName;
}

void params::setType(const string& n) {
    type = n;
}

void params::setVar(_var v) {
    variable = v;
}

params::~params() {
}

```

var.cpp:
```

#include "var.h"

using namespace std;

var::var() {
    varName = "";
    varClassname = "";
    varIsPointer = false;
}

var::var(const var& v) {
    varName = v.varName;
    varClassname = v.varClassname;
    varIsPointer = v.varIsPointer;
}

void var::setVariableName(const string& n) {
    varName = n;
}

void var::setVariableClassname(const string& n) {
    varClassname = n;
}

void var::setVariableIsPointer(bool p) {
    varIsPointer = p;
}

var::~var() {
}

```

Thanks,

---

