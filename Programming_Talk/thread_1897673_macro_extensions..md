---
title: "macro extensions."
date: 2011-12-19
forum: Programming Talk
---

### Post by ufuser01 on 2011-12-19
**[B]Hi,**[/B]

I intend to a functionality as given at the end of this message, for printing debug statements. This works when I have variables to print. However, when there are no variables [ printf("Hello world"); ], I am unable to use this macro. Any suggestions?

Thanks.




source: [http://publib.boulder.ibm.com/infocenter/comphelp/v8v101/index.jsp?topic=%2Fcom.ibm.xlcpp8a.doc%2Flanguage%2Fref%2Fdefine.htm]("http://publib.boulder.ibm.com/infocenter/comphelp/v8v101/index.jsp?topic=%2Fcom.ibm.xlcpp8a.doc%2Flanguage%2Fref%2Fdefine.htm")

**Variadic macro extensions**

#define debug1(format, ...)  printf(format, __VA_ARGS__)
#define debug2(format, args ...)  printf(format, args)     

Invocation Result of Macro Expansion     
debug1("Hello %s\n","World"); printf("Hello %s\n","World");   
debug2("Hello %s\n","World"); printf("Hello %s\n","World");

---

### Post by dwhitney67 on 2011-12-19
You're debug2 macro generates a warning when compiling with -Wall:
```

warning: ISO C does not permit named variadic macros [-Wvariadic-macros]

```
As for cases where you have no args to pass, try defining a debug0 macro:
```

#define debug0(format) printf(format);

```
I do not program in C often enough to know if there is a compiler option that can be enabled that allows you to merely use debug1 in cases where all you have is a "format", but no args.

---

