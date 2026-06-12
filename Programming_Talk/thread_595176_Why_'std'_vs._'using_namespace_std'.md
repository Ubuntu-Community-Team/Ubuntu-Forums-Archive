---
title: "Why 'std::' vs. 'using namespace std'?"
date: 2007-10-28
forum: Programming Talk
---

### Post by JupiterV2 on 2007-10-28
Another WHY question. I've read conflicting reports but it is generally agreed that...

```
using namespace std;
```

...is bad practice and you should use the std:: prefix whenever invoking a std namespace function like cout or the string class. Example:

```

std::string str = "Some string.";

std::cout << str << std::endl;
```

My question is, why? What are the advantages of the 'std::' prefix or the pitfalls of 'using namespace std'?

---

### Post by Spruce Moose on 2007-10-28
I think it's more a matter of personal preference rather than a rule or good/bad practice.  Typing std:: all the time gets pretty boring though.  Wouldn't you rather type "using namespace std" once rather than sprinking std:: everywhere?  That's what I like to do anyway.


SM.

---

### Post by aks44 on 2007-10-28
[The C++ FAQ lite covers this topic]("http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5").

Additionnaly, prefixing with std:: allows one to distinguish at a glance what parts of the program use the standard library, and what parts use "custom" code.

---

### Post by dumbsnake on 2007-10-28
There are many different styles here that are all valid, but there is one RULE:

Do NOT put "using namespace xxxx" in a header file.  PERIOD.

I personally like to always be explicit and put std::string instead of string, but it is perfectly fine to have "using namespace std;" in an implementation file.  While I don't do it myself, it is not bad style at all in my opinion.

The reason you shouldn't ever put using namespace xxx in a header file is that it makes a conflict later much more likely.  If you use a namespace and then another header file after that uses a namespace with some of the same names and references one of those functions then the code might not compile, but only when including both headers.... which is obviously a really unfortunate bug.  This is why you don't use a namespace in a header.  Implementation is different though because you don't include implementation files (.cpp, etc...)

I'm sure there are varying opinions, but these guidelines are certainly not wrong.

---

### Post by smartbei on 2007-10-28
The idea is to not overrun your global function namespace with functions. If you don't care, you can use "using namespace std;". That is really all there is to it as far as I know.

---

### Post by samjh on 2007-10-28
You can also use```
using namespace_name::member;
```to specify which member of that namespace to use.

Example:
```
using std::cout;
using std::cin;
using std::endl;
```

Will allow you to use cout, cin, and endl, without specifying std:: in front of every usage.

---

### Post by dwhitney67 on 2007-10-28
Since this post is on the topic of namespaces, can someone refresh my memory on how to forward-declare an std:: object (within a header file) in lieu of including the header file that defines it?

I want to believe it's something like this, but I'm not sure:

```

#ifndef FOO_H
#define FOO_H
namespace std
{
  class string;
};

...
#endif
```

---

### Post by hod139 on 2007-10-28
You can't.  The problem is they are not classes, but [FONT=Arial, Arial, Helvetica]typedefs of templates.  [http://www.gotw.ca/gotw/034.htm](http://www.gotw.ca/gotw/034.htm)

The STL writers do provide [/FONT]<iosfwd>, but that is only for iostream.  No others.

---

