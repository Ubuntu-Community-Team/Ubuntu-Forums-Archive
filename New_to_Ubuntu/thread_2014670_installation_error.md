---
title: "installation error"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by tripti56 on 2012-07-02
hello,
I am trying to install shallow parser.And when i use the make install command it gives me error:
**I**n file included from node.h:13:0,
                 from node.cpp:9:
path.h:26:52: error: 'size_t' has not been declared
make[2]: *** [node.lo] Error 1
make[2]: Leaving directory `/home/tripti/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/tripti/sampark/shallow_parser_hin/bin/sl/CRF++-0.51'
make: *** [install] Error 2
:confused:

can anyone help me in this matter.
Thanks in advance:)

---

### Post by NikTh on 2012-07-02
imo i don't think this is a Thread for "Absolute Beginners" . This want further configuration , maybe make file , or try to read README file . (it must be included). 
I don't know exactly how to help you , but someone else knows .. so be patient. 
I think you must specify this 
> path.h:26:52: error: 'size_t' has not been declared

---

