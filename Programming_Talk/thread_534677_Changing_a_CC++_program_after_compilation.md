---
title: "Changing a C/C++ program after compilation?"
date: 2007-08-25
forum: Programming Talk
---

### Post by bluedalmatian on 2007-08-25
Is there a way to write a c++ program such that the methods called and objects containing those methods can be determined entirely at run time?

 For example a program which is given a pointer to an object, the class of which it has  seen before, therefore it would have to be a null pointer, yes?)  Lets say that pointer is called anObj

it then reads the name of a method from a text file a (say aMethod() ) and calls  anObj->aMethod()

I cant see how to achieve this because the source code would need to be changed and recompiled, yet another part of me thinks it may somehow be possible by poking under the hood a little?

Thanks
Andrew

---

### Post by Wybiral on 2007-08-25
I'm not sure I completely get what you're saying.

I could be wrong, but wouldn't a simple conditional case work for that?

```

switch(which_method)
{
    case "aMethod": anObj.aMethod(); break;
    case "bMethod": anObj.bMethod(); break;
    case "cMethod": anObj.cMethod(); break;
}

```

Aside from that, if you want dynamic code, you could use dynamically linked libraries and just change the "so" when needed, or you could embed a scripting language such as python in your program.

But if you want TRULY dynamic code, a compiled language isn't going to help you too much... Use a more dynamic language.

---

### Post by russell.h on 2007-08-25
You could use an if/then statement to change what it does, but you have to write all the available options into the program. Alternatively you could probably call a script of some sort (python or the like), but I don't know how.

Another neat (but time consuming) option would be to design your own scripting language (which you could make syntactically similar to C/C++), then run the scripts from the text files in question.

---

### Post by pjkoczan on 2007-08-25
I remember a C++-ism when I wrote a project for a databases class where you can simply cast the pointer to the appropriate object-type. If it works, then go with that method. Of course, this assumes two things: (1) that your program knows about the classes and can load the appropriate libraries, and (2) that there are no inheritance issues that.

As an example of #2, suppose ClassA inherits from ClassB, and pointer x is type ClassA. Well, casting x to ClassA works because of its type, but also casting x to ClassB since ClassA inherits from, and therefore can also be used as, ClassB. You can probably work around this by ordering things properly. 

I'm a little rusty on syntax, but I believe something like this will do the trick:

```

void myFunction (void *x) {
  if ((ClassA*)x) {
    x->funcA;
  } else if ((ClassB*)x) {
    x->funcB;
  }

  // etc, etc, etc
}

```

Hope this helps.

---

### Post by DavidBell on 2007-08-25
Bluedalmation what you are asking is roughly what the Windows COM/OLE system does. Windows COM is very contorted, partly because it's a generic system wide service, but you could roll your own that was at least one level less of obfuscation if it was only to serve your application. You might also have a look at how Firefox plugins work, my guess is it is something similar. In a nutshell windows COM sort of works like this (with some shortcuts)

[LIST=1]
[*]To create an instance of a comclass, you call the Windows system function CoCreateInstance (MyClassFactory_Identifier)
[*]MyClassFactory is a class written by you that has to be derived from IClassFactory. CoCreateInstance in turns calls your implementation of MyClassFactory::CreateInstance(IUnknown**) ... which overrides IClassFactory::CreateInstance
[*]MyClass is also written by you, and has to derive from IUnknown, MyClassFactory::CreateInstance(IUnknown**) returns a pointer to a new instance of MyClass, casted to IUnknown*.
[*] You can use MI to derive from other classes as well, typically your class will derive from both IMyClass and IDispatch. You use IUnknown::QueryInterface() to recast to other base classes (interfaces in COM) and thus get access to their functions. CoCreateInstance can also instance a particular interface directly. 
[/LIST]

The interesting thing about COM is if you derive your comclasses from say IMyPluginInterface, you can create a new class deriving from this at any time and basically make an early  bound plugin for something without recompiling .... which is what you were originally asking I think.

Most comclasses also support IDispath interface, which allows late binding of functions, effectively calling them by name.

HTH DB

---

### Post by pmasiar on 2007-08-25
> **bluedalmatian said:**
> Is there a way to write a c++ program such that the methods called and objects containing those methods can be determined entirely at run time?

I am not exactly sure what you want, but "duck typing", or latent typing, used in dynamically typed languages like Python, Ruby or Perl, seems to be close. When you call object's method, it is resolved at runtime.

Obviously it is possible - Python is written in C, after all :-) but not trivial. IIRC Bruce Eckel  demonstrated latent typing in Java, check his blog at mindview.com. Lots of interesting reading there.

---

### Post by ryno519 on 2007-08-25
I don't understand why you would want to do this. Could you explain a possible application which would employ this technique?

---

### Post by Wybiral on 2007-08-26
> **ryno519 said:**
> I don't understand why you would want to do this. Could you explain a possible application which would employ this technique?

I agree... If you explain a situation you have in mind, maybe there is another way that doesn't involve doing this. Maybe not... But it will help us offer suggestions.

---

### Post by bluedalmatian on 2007-08-29
Thanks for the suggestions

Im trying to write a Database Object Relational Mapping system (like Java's Hibernate) which can cope with objects its never seen before simply by reading the method to field mapping from a text file.

---

### Post by aks44 on 2007-08-29
What you're trying to do requires the language to support runtime *introspection* (aka *reflection*). Neither C nor C++ support it out of the box, you need to add lots of boiler-plate code.

There are a few libraries out there that provide the basics for runtime introspection, but right now I can't remember any name from the top of my head.


As far as "hibernation" goes... (de)serialization & registered factories  should do the trick, no need for "field mapping". You should only need 3 fields: object id, class id, and serialized object state. IIRC there are existing libraries for that also.

EDIT: BTW, there is no such thing as "field to method" mapping as far as "hibernation" goes, only "field to data member" mapping (methods do not carry state).

---

### Post by slavik on 2007-08-30
> **aks44 said:**
> What you're trying to do requires the language to support runtime *introspection* (aka *reflection*). Neither C nor C++ support it out of the box, you need to add lots of boiler-plate code.

There are a few libraries out there that provide the basics for runtime introspection, but right now I can't remember any name from the top of my head.


As far as "hibernation" goes... (de)serialization & registered factories  should do the trick, no need for "field mapping". You should only need 3 fields: object id, class id, and serialized object state. IIRC there are existing libraries for that also.

EDIT: BTW, there is no such thing as "field to method" mapping as far as "hibernation" goes, only "field to data member" mapping (methods do not carry state).

he meant hibernate as in [http://en.wikipedia.org/wiki/Hibernate_(Java](http://en.wikipedia.org/wiki/Hibernate_(Java))

my understanding is that if you have any objects that are stiff referenced once your code is done, they are saved. and ocne you run the program again, they are automagically still there ... this is one of those things that tries to take an OO language and turn it into a database (part of the OO database field).

---

### Post by dempl_dempl on 2007-08-31
Wait a minute....

On windows you have:
```

HANDLE DLL = LoadLibraryA(""some dlll");
MyFuncPtrType* MyFuncPrt = (MyFuncPtrType*)GetProcAddressA(DLL,"yourFunction");

```

There has to be something like that on Linux.

I've never did something like that on our system, because Linux programs are usually made in other ways..

Google-ing it....
```
#include <stdlib.h>
    #include <stdio.h>
    #include <dlfcn.h>

    int main(int argc, char **argv) {
        void *handle;
        double (*cosine)(double);
        char *error;

        handle = dlopen ("/lib/libm.so.6", RTLD_LAZY);
        if (!handle) {
            fputs (dlerror(), stderr);
            exit(1);
        }

        cosine = dlsym(handle, "cos");
        if ((error = dlerror()) != NULL)  {
            fputs(error, stderr);
            exit(1);
        }

        printf ("%f\n", (*cosine)(2.0));
        dlclose(handle);
    }
```

If you like dynamic loading of classes:
go to this link:
[http://www.linuxjournal.com/article/3687](http://www.linuxjournal.com/article/3687)


Cheers!8-)

---

### Post by Ramses de Norre on 2007-08-31
Is it an option to use Java? The reflection API does exactly what you want (I think, I'm not sure I completely understand what you're after).

---

### Post by pmasiar on 2007-08-31
> **bluedalmatian said:**
> Im trying to write a Database Object Relational Mapping system (like Java's Hibernate) which can cope with objects its never seen before simply by reading the method to field mapping from a text file.

Is it for a web-based app? Can you use dynamic language like Python or Ruby, which already have it? Or is it more like exercise in reinventing the wheel to find out what makes it round?

---

### Post by aks44 on 2007-08-31
> **slavik said:**
> he meant hibernate as in [http://en.wikipedia.org/wiki/Hibernate_(Java](http://en.wikipedia.org/wiki/Hibernate_(Java))

my understanding is that if you have any objects that are stiff referenced once your code is done, they are saved. and ocne you run the program again, they are automagically still there ...

That's exactly what I said... "hibernation" (maybe that term confused you in my post? I should have said "persistence") is all about preserving state (ie. data), and does not relate in any way with methods.

IOW the serialized contents is useless if you don't have the corresponding classes available, at least in statically typed languages ; dynamic languages are another whole story since you could store some (p)code that could be eval'ed after deserialization. But C++ doesn't provide this kind of services, and neither does Java's Hibernate AFAIK.


Back on topic, in C++ context, the bare minimum to provide persistence is:
- a single DB table with 2-3 fields: object id for (cross-) references, class id, serialized state
- a pure interface that provides de/serialization services to the persistence library, wannabe persistent classes have to derive from this interface
- registered factories, to allow the library to correctly dispatch state streams at deserialization so the corresponding objects can be instanciated

Granted, such a design does not provide one to one mapping between data members and DB fields, so it's not as powerful as Hibernate. But depending on the goals it can be enough (ie. if persistence is the only goal).
If one needs finer mapping, more boiler-plate code is required (specifically an abstraction layer, part of the persistence library, that isolates wannabe persistent classes from the DB engine).

Anyway the catch with either C or C++ is that those languages don't support introspection natively, so they need *cooperation* from the classes that are willing to be serialized. I believe those are not the best languages to implement persistence, although it can be (and has been) done...

---

### Post by PaulFr on 2007-08-31
1. In response to dempl_dempl, **dlopen** works for dynamic (shared) libraries, and has a problem with C++ due to name mangling. Presumably you could generate the mapping between mangled and unmangled names, since **nm** can do that.

2. In response to OP, perhaps you could start with **[http://en.wikipedia.org/wiki/Reflection_(computer_science](http://en.wikipedia.org/wiki/Reflection_(computer_science))** in your search. Perhaps **[http://sourceforge.net/projects/crd](http://sourceforge.net/projects/crd)** is what you seek :-) That uses template metaprogramming; another approach is compile time info generation (see **[http://seal-reflex.web.cern.ch/seal-reflex/index.html](http://seal-reflex.web.cern.ch/seal-reflex/index.html)** for an example).

---

### Post by bluedalmatian on 2007-09-01
> cise in reinventing the wheel to find out what makes it round?

lol partly yes, and partly because it needs to be C++ and AFAIK there are no cheap or free equivalents to Hibernate out there for C++, so I started looking into building one.

Introspection - thats the phrase I couldnt remember!!! :lolflag:

---

### Post by bluedalmatian on 2007-09-01
> BTW, there is no such thing as "field to method" mapping as far as "hibernation" goes, only "field to data member" mapping (methods do not carry state).


There is if your design assumes each data member has a getter & setter method through which it is always accessed  :)

---

### Post by aks44 on 2007-09-01
> **bluedalmatian said:**
> There is if your design assumes each data member has a getter & setter method through which it is always accessed  :)

This is very bad design IMO... Access specifiers are there (amongst other things) to shield the class' internals from the "outside world".


Using such a design, you'll probably end up:
- either having all data members public (be it through accessor methods, the result is the same), which totally denies sane OO practices
- or loosing private state during the storage/retrieval process

---

