---
title: "basic c++ compile error : copy is not a member of std"
date: 2010-07-26
forum: Packaging and Compiling Programs
---

### Post by tuantu.t on 2010-07-26
Hi,

It's gonna sound stupid but I'm desperate...

I can't compile a c++ program:

```
#include<iostream>
int main(){}

```then simply g++ test.cpp gives:
```
In file included from /usr/include/c++/4.4/vector:64,
                 from ./debug/debug.h:5,
                 from /usr/include/c++/4.4/bits/stl_algobase.h:71,
                 from /usr/include/c++/4.4/bits/char_traits.h:41,
                 from /usr/include/c++/4.4/ios:41,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from test.cpp:1:
/usr/include/c++/4.4/bits/stl_uninitialized.h: In static member function ‘static _ForwardIterator std::__uninitialized_copy<true>::uninitialized_copy(_InputIterator, _InputIterator, _ForwardIterator)’:
/usr/include/c++/4.4/bits/stl_uninitialized.h:93: error: ‘copy’ is not a member of ‘std’
/usr/include/c++/4.4/bits/stl_uninitialized.h: In static member function ‘static void std::__uninitialized_fill<true>::uninitialized_fill(_ForwardIterator, _ForwardIterator, const _Tp&)’:
/usr/include/c++/4.4/bits/stl_uninitialized.h:150: error: ‘fill’ is not a member of ‘std’
/usr/include/c++/4.4/bits/stl_uninitialized.h: In static member function ‘static void std::__uninitialized_fill_n<true>::uninitialized_fill_n(_ForwardIterator, _Size, const _Tp&)’:
/usr/include/c++/4.4/bits/stl_uninitialized.h:204: error: ‘fill_n’ is not a member of ‘std’
[...]

```About my config:
```

lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid

dpkg -l 'libstdc++*'
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom                                                      Version                                         Description
+++-========================================================-===============================================-============================================
un  libstdc++-dev                                            <néant>                                        (aucune description n'est disponible)
un  libstdc++2.10-dev                                        <néant>                                        (aucune description n'est disponible)
un  libstdc++2.8-dev                                         <néant>                                        (aucune description n'est disponible)
un  libstdc++2.9-dev                                         <néant>                                        (aucune description n'est disponible)
un  libstdc++2.9-glibc2.1-dev                                <néant>                                        (aucune description n'est disponible)
un  libstdc++3.0-dev                                         <néant>                                        (aucune description n'est disponible)
ii  libstdc++6                                               4.4.3-4ubuntu5                                  The GNU Standard C++ Library v3
un  libstdc++6-4.4-dbg                                       <néant>                                        (aucune description n'est disponible)
ii  libstdc++6-4.4-dev                                       4.4.3-4ubuntu5                                  The GNU Standard C++ Library v3 (development
un  libstdc++6-4.4-doc                                       <néant>                                        (aucune description n'est disponible)

```If you have any idea what's wrong, please help ... I really have no clue ...

Thanks

---

### Post by tuantu.t on 2010-07-26
Ok just in case someone runs into the same problem

I had the environment variable CPLUS_INCLUDE_PATH=:/home/username/usr/lib

It's the : at the begining that messed up everything ... 

AND the fact that I had a directory debug/ with a file debug.h in it, in the directory from which i was working...

So this file was included instead of the standard /usr/include/c++/4.4/debug/debug.h


I feel so silly ...

---

