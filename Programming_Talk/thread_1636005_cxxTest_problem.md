---
title: "cxxTest problem"
date: 2010-12-02
forum: Programming Talk
---

### Post by ddmn on 2010-12-02
Hi all,

I've installed CxxTest plug-ins for eclipse.
When I create my new project **Project w/ CxxTest**, I get the following error messages:
```

cast from ‘void*’ to ‘unsigned int’ loses precision
make: *** [runAllTests.o] Error 1

```when I click on the first line it takes me to the file **cxxtest_listener.cpp **and highlight the following line:
```

bool cxxtest_xml_listener::should_report_leak(
    const Dereferee::allocation_info& leak)
{
   ** unsigned int tag = (unsigned int) leak.user_info();  **  
    return (tag & 0x80000000) == 0;
}
```what may be causing this problem?

Kind Regards & Thank you.

---

### Post by MadCow108 on 2010-12-02
the cause is probably that leak.user_info returns a pointer which can be 8 byte on 64 bit platforms whereas unsigned int is mostly 32 bit.
So you lose precision and the compiler warns about this.
If you compile with -Werror the compilation will fail instead.

Is this error in your own code? then fix it by using e.g. uintptr_t from stdint.h
if not and you can't fix it you have to disable Werror and ignore it (+ file a bugreport against cxxtest)

---

### Post by ddmn on 2010-12-02
This happens after i create a new project. i.e. thats just before i even write a single line of code.
How do i disable Werror? wouldn't it cause some problems later on if i ignore it?

**Edit:** In fact thats an error not a warning.

Kind Regards & Thank you.

> **MadCow108 said:**
> the cause is probably that leak.user_info returns a pointer which can be 8 byte on 64 bit platforms whereas unsigned int is mostly 32 bit.
So you lose precision and the compiler warns about this.
If you compile with -Werror the compilation will fail instead.

Is this error in your own code? then fix it by using e.g. uintptr_t from stdint.h
if not and you can't fix it you have to disable Werror and ignore it (+ file a bugreport against cxxtest)

---

### Post by MadCow108 on 2010-12-02
hm yes it seems to be an error and no warning. so you can't disable it without Werror

unfortunately I do not know how to disable the error except fixing the source or compiling in 32 bit mode (-m32).

In this case the unfixed source should be unproblematic as integer truncation happens on the most significant 32 bits and the rest of the code only checks the least significant 32 bits
(assuming the check also makes sense in the 64 bit case, which might not be the case as it has something to do with leak detection :/)

---

