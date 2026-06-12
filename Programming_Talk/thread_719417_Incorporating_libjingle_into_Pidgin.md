---
title: "Incorporating libjingle into Pidgin"
date: 2008-03-09
forum: Programming Talk
---

### Post by ELiz on 2008-03-09
Hiii
I am doing a project to incorporate libjingle into pidgin....But libjingle is CPP and pidgin is C... How can we call libjingle from a C program...Will there be some language independent interface for pidgin to do this????... If I a write a plugin in cpp how can i convert into .so format so that i can directly add it to plugin list of Pidgin???... What are the commands that are used for converting a library into .so format???
Eliz..:)

---

### Post by pneves on 2009-07-21
I think what your looking for is the extern "C" directive in C++. 

You encapsulate any code you want to access through C in the directive as follows 

extern "C"  
     { 
     // place your code here. 
     }


This will allow you to call those functions encapsulated in the brackets in a C program by turning off name mangling.

---

