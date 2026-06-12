---
title: "boost liberies"
date: 2008-05-02
forum: Programming Talk
---

### Post by StOoZ on 2008-05-02
I would like to install the boost libraries from the repositories, now when I did the following:
> aptitude search boost
p   boost-build                                           - Build system
p   libboost-date-time-dev                                - set of date-time libraries based on generic programming concept
p   libboost-date-time1.34.1                              - set of date-time libraries based on generic programming concept
p   libboost-dbg                                          - Boost C++ Libraries with debug symbols
p   libboost-dev                                          - Boost C++ Libraries development files
p   libboost-doc                                          - Boost.org libraries documentation
p   libboost-filesystem-dev                               - filesystem operations (portable paths, iteration over directori
p   libboost-filesystem1.34.1                             - filesystem operations (portable paths, iteration over directori
p   libboost-graph-dev                                    - generic graph components and algorithms in C++
p   libboost-graph1.34.1                                  - generic graph components and algorithms in C++
p   libboost-iostreams-dev                                - Boost.Iostreams Library development files
p   libboost-iostreams1.34.1                              - Boost.Iostreams Library
p   libboost-program-options-dev                          - program options library for C++
p   libboost-program-options1.34.1                        - program options library for C++
p   libboost-python-dev                                   - Boost.Python Library development files
p   libboost-python1.34.1                                 - Boost.Python Library
p   libboost-regex-dev                                    - regular expression library for C++
p   libboost-regex1.34.1                                  - regular expression library for C++
p   libboost-serialization-dev                            - serialization library for C++
p   libboost-serialization1.34.1                          - serialization library for C++
p   libboost-signals-dev                                  - managed signals and slots library for C++
p   libboost-signals1.34.1                                - managed signals and slots library for C++
p   libboost-test-dev                                     - components for writing and executing test suites
p   libboost-test1.34.1                                   - components for writing and executing test suites
p   libboost-thread-dev                                   - portable C++ multi-threading
p   libboost-thread1.34.1                                 - portable C++ multi-threading
p   libboost-wave-dev                                     - C99/C++ preprocessor library
p   libboost-wave1.34.1    


now I cant understand exactly which one to install, my guess is "libboost-dev  " , but its only a guess.
any idea?

---

### Post by mike_g on 2008-05-02
That should be it.

---

### Post by StOoZ on 2008-05-02
but I guess its better to install everything that is listed right?

---

### Post by mike_g on 2008-05-02
I wouldent do that, or you will end up with a load of crap you dont want. I'd just install the development files for now, and maybe the docs. But at the end of the day its up to you what you want to do.

---

### Post by dwhitney67 on 2008-05-02
The -dev stuff is all you need.  The docs are available online.  No need to install on your system.

---

### Post by StOoZ on 2008-05-03
first of all thanks for the help, I have another little question in mine :
does using *ONLY* the boost libraries means that my program will be cross-platform?

---

### Post by LaRoza on 2008-05-03
> **StOoZ said:**
> first of all thanks for the help, I have another little question in mine :
does using *ONLY* the boost libraries means that my program will be cross-platform?

C++ is cross platform. If you use the boost libraries, your program will run where the boost libraries are implemented. I don't know anything about boost.

---

### Post by dwhitney67 on 2008-05-03
AFAIK, the Boost libraries are available for *nix and Windows.

---

