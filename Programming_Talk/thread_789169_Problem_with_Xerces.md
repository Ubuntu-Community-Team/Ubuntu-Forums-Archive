---
title: "Problem with Xerces"
date: 2008-05-10
forum: Programming Talk
---

### Post by denny577 on 2008-05-10
I installed the libxerces27-dev package, but something goes wrong when I try to compile this:
```
#include <xercesc/util/PlatformUtils.hpp>
// Other include files, declarations, and non-Xerces-C++ initializations.
XERCES_CPP_NAMESPACE_USE 
  
int main(int argc, char* argv[])
{
  try {
    XMLPlatformUtils::Initialize();
  }
  catch (const XMLException& toCatch) {
    // Do your failure processing here
    return 1;
  }

  // Do your actual work with Xerces-C++ here.

  XMLPlatformUtils::Terminate();

  // Other terminations and cleanup.
  return 0;
}

(From http://xerces.apache.org/xerces-c/program.html)
```
I get all weird output from g++:
```
dennis@fhssws12:~/Documents/C(++)$ g++ XercesTest.cpp -o XERCES
/tmp/ccJOBvGP.o: In function `main':
XercesTest.cpp:(.text+0x12): undefined reference to `xercesc_2_7::XMLUni::fgXercescDefaultLocale'
XercesTest.cpp:(.text+0x3a): undefined reference to `xercesc_2_7::XMLPlatformUtils::Initialize(char const*, char const*, xercesc_2_7::PanicHandler*, xercesc_2_7::MemoryManager*, bool)'
XercesTest.cpp:(.text+0x3f): undefined reference to `xercesc_2_7::XMLPlatformUtils::Terminate()'
/tmp/ccJOBvGP.o:(.gcc_except_table+0x10): undefined reference to `typeinfo for xercesc_2_7::XMLException'
collect2: ld returned 1 exit status
dennis@fhssws12:~/Documents/C(++)$
```

Normally, if there are errors, g++ tells me the line number, not .text+0x##
Is there anyone that can tell me what is going wrong or what I'm doing wrong?

Regards, Dennis

---

### Post by nvteighen on 2008-05-10
You must tell the compiler to link to any library (except C++ Standard Lib) using -l[library] argument. Normally, you drop the "lib-" from name, so I guess you need -lxerces.

---

### Post by denny577 on 2008-05-10
It worked indeed with -lxerces-c

Thanks :)

---

