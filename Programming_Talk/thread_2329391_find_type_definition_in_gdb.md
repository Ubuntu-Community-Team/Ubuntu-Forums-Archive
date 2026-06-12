---
title: "find type definition in gdb"
date: 2016-07-01
forum: Programming Talk
---

### Post by chuchi on 2016-07-01
Hi all!
 

 This is a question regarding the gdb command 'info types', which can tell where a type is defined in source code.
 

 For example, in gdb if I type 'info types mytype' in the following program:
 

 ```

 //main.cpp
 #include <iostream>
 

 struct mytype
 {
   const static bool value = false;
 };
     
 int
 main()
 {
     //mytype tip;    //if I remove this comment, it works
     std::cout << mytype::value << std::endl;
     return 0;
 }
 
```
 

 gdb does not find any matching in the source for type 'mytype'.
 

 But if I remove comment in line 12, gdb finds the type definition and outputs this:
 

 ```

 All types matching regular expression "mytype": 
  
 File main.cpp: 
 mytype; 
 
```  
 

 It seems to me that in order to gdb to find where a type is defined, you have to declare a variable of that type.
 

 Is it possible to find where a type is defined in gdb without declaring a variable of that type?
 

 Thanks a lot!

---

### Post by TheFu on 2016-07-02
Don't think that is how this works.  The compiler should optimize out any unneeded code - like unused code and unused data types.  Right?  Those are simple "wins" for a compiler optimizer.

---

