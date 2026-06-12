---
title: "How to install boost_date_time-gcc-mt-d-1_33_1 library?"
date: 2007-06-02
forum: Programming Talk
---

### Post by yinglcs2 on 2007-06-02
Hi, 

Can you please tell me how to install 'boost_date_time-gcc-mt-d-1_33_1' library on ubuntu?

I get the following linking error:
```
/usr/bin/ld: cannot find -lboost_date_time-gcc-mt-d-1_33_1
collect2: ld returned 1 exit status
make[2]: *** [libgnashbase.la] Error 1
make[2]: Leaving directory `/home/scheung/src/gnash-trunk/gnash/libbase'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/scheung/src/gnash-trunk/gnash'
make: *** [all] Error 2

```

Thank you.

---

### Post by yabbadabbadont on 2007-06-02
```
/home/daffy $ aptitude search boost
p   boost-build                                             - Build system                                                     
p   libboost-date-time-dev                                  - set of date-time libraries based on generic programming concepts 
p   libboost-date-time1.33.1                                - set of date-time libraries based on generic programming concepts 
p   libboost-dbg                                            - Boost C++ Libraries with debug symbols                           
p   libboost-dev                                            - Boost C++ Libraries development files                            
p   libboost-doc                                            - Boost.org libraries documentation                                
p   libboost-filesystem-dev                                 - filesystem operations (portable paths, iteration over directories
p   libboost-filesystem1.33.1                               - filesystem operations (portable paths, iteration over directories
p   libboost-graph-dev                                      - generic graph components and algorithms in C++                   
p   libboost-graph1.33.1                                    - generic graph components and algorithms in C++                   
p   libboost-iostreams-dev                                  - Boost.Iostreams Library development files                        
p   libboost-iostreams1.33.1                                - Boost.Iostreams Library                                          
p   libboost-program-options-dev                            - program options library for C++                                  
p   libboost-program-options1.33.1                          - program options library for C++                                  
p   libboost-python-dev                                     - Boost.Python Library development files                           
p   libboost-python1.33.1                                   - Boost.Python Library                                             
p   libboost-regex-dev                                      - regular expression library for C++                               
p   libboost-regex1.33.1                                    - regular expression library for C++                               
p   libboost-serialization-dev                              - serialization library for C++                                    
p   libboost-signals-dev                                    - managed signals and slots library for C++                        
p   libboost-signals1.33.1                                  - managed signals and slots library for C++                        
p   libboost-test-dev                                       - components for writing and executing test suites                 
p   libboost-test1.33.1                                     - components for writing and executing test suites                 
p   libboost-thread-dev                                     - portable C++ multi-threading                                     
p   libboost-thread1.33.1                                   - portable C++ multi-threading                                     
p   libboost-wave-dev                                       - C99/C++ preprocessor library                                     

```
I would guess that one of those packages provides what you need.  Do you have all the boost*-dev libraries installed?

Edit: especially libboost-date-time-dev

---

### Post by WW on 2007-06-02
If you are going to be doing a lot of compiling, I recommend learning how to find the packages that provide the libraries that you need. Here are two methods that I often use:

1. Open up Synaptic, click on the Search button, enter **boost** and click on Search.  Take a look at the packages found. Do any of them look like they might provide the appropriate library?

OR

2. Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), and scroll down to the section with the heading "Searches".  At the "Keyword:" prompt, enter **boost**, and click on the Search button.  Then look at the packages found--do any of the package names look like they might provide the library that you want?  To be sure, click on the **feisty** link (if you didn't changed the Distribution option in the search) to see the details of the package.  Scroll down to the section that begins with the heading "Download [package name here]", and click on the **list of files** link in the table.  Look for the file usr/lib/libboost_date_time_gcc-mt-d-1_33_1.so.[numbers here].  If it is there, then you have found your package.  Install it with Synaptic, or with the apt-get command.

OR

3. See the post by yabbadabbadont that precedes this post. :)

---

### Post by yinglcs2 on 2007-06-02
Thanks. That solves my problem.

---

