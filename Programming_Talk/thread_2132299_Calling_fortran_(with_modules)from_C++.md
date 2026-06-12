---
title: "Calling fortran (with modules)from C++"
date: 2013-04-04
forum: Programming Talk
---

### Post by jerome12345 on 2013-04-04
Hi

I have my FORTRAN code as below

```
MODULE ARRAY_STORAGE 
      
      REAL*8, ALLOCATABLE :: ARRAY(:) 
      
      END MODULE ARRAY_STORAGE 

      
      function ffunc(n1,n2) 
      
      USE ARRAY_STORAGE 

      integer ffunc 
      character*256 filename 
      integer n1,n2,iret 
      integer*4 stat 
      
      ALLOCATE (ARRAY(10),stat=stat) 
      if (stat/=0) then 
         write (*,*) 'problem allocating array : stat=',stat 
      else 
         write (*,*) 'array allocated as size', size(array)*8./(2.**20), 
     +' mb at LOC',loc(array) 
      end if 

      
      ffunc = n1+n2 
      
      return 
      
      end

```

I am calling from C++

#include <iostream> 
extern "C" 
{ 
   //int __stdcall  ffunc(int*, int*); 
   float ARRAY_STORAGE_mp_ARRAY(); 
   //int ffunc(int*, int*); 
    
    
} 

extern "C" 
{ 
   //int __stdcall  ffunc(int*, int*); 
   //float ARRAY_STORAGE_mp_ARRAY(); 
   int ffunc(int*, int*); 
    
    
} 

```
int main() 
{ 
    int n1 = 1; 
    int n2 = 2; 
    
   std::cout << "Calling from C++ to Fortran, arguments: " << n1 << ", " << n2 << '\n'; 
    
   int r = ffunc(&n1,&n2); 
    
   //std::cout << "THe return value from fortran was " << r << '\n'; 


    

}
```

It is not working-anyone can please help?

---

### Post by spjackson on 2013-04-04
How are you trying to compile and link? What error(s) are you encountering?

I don't know Fortran. However, if I rename ffunc to ffunc_ in the C++ source, I can build and run your code using the following Makefile.
```

f:    main.o ff.o
    g++ -o ff main.o ff.o -L/usr/lib/gcc/x86_64-linux-gnu/4.6 -lgfortran

```

---

### Post by jerome12345 on 2013-04-04
Thanks alot, I'm using Visual Studo environemnt-is it possible to try there?

---

### Post by jerome12345 on 2013-04-04
These are the erros I get

Error 1 error LNK2005: __CrtSetCheckCount already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 2 error LNK2005: _exit already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 3 error LNK2005: __exit already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 4 error LNK2005: __cexit already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 5 error LNK2005: __amsg_exit already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 6 error LNK2005: __initterm_e already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 7 error LNK2005: __crt_debugger_hook already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 8 error LNK2005: __invoke_watson already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 9 error LNK2005: __configthreadlocale already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 10 error LNK2005: __encode_pointer already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 11 error LNK2005: __decode_pointer already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 12 error LNK2005: __XcptFilter already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 13 error LNK2005: ___xi_a already defined in MSVCRTD.lib(cinitexe.obj) LIBCMTD.lib cpptest
Error 14 error LNK2005: ___xi_z already defined in MSVCRTD.lib(cinitexe.obj) LIBCMTD.lib cpptest
Error 15 error LNK2005: ___xc_a already defined in MSVCRTD.lib(cinitexe.obj) LIBCMTD.lib cpptest
Error 16 error LNK2005: ___xc_z already defined in MSVCRTD.lib(cinitexe.obj) LIBCMTD.lib cpptest
Error 17 error LNK2005: "void __cdecl terminate(void)" ([EMAIL="?terminate@@YAXXZ"]?terminate@@YAXXZ[/EMAIL]) already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 18 error LNK2005: __lock already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 19 error LNK2005: __unlock already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 20 error LNK2005: _mainCRTStartup already defined in MSVCRTD.lib(crtexe.obj) LIBCMTD.lib cpptest
Error 21 error LNK2005: ___set_app_type already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Error 22 error LNK2005: __CrtDbgReportW already defined in MSVCRTD.lib(MSVCR90D.dll) LIBCMTD.lib cpptest
Warning 23 warning LNK4098: defaultlib 'MSVCRTD' conflicts with use of other libs; use /NODEFAULTLIB:library cpptest cpptest
Warning 24 warning LNK4098: defaultlib 'LIBCMTD' conflicts with use of other libs; use /NODEFAULTLIB:library cpptest cpptest
Error 25 fatal error LNK1169: one or more multiply defined symbols found D:\ajay_2012\FFES\fortran_to_cpp\cpptest\Debug\cpptest.exe cpptest

---

### Post by spjackson on 2013-04-04
I don't have a Fortran compiler for Windows installed, so I can't try it. However, those errors you are getting are because you are including both the static and dynamic versions of the C runtime library. You must choose one or the other. See [http://msdn.microsoft.com/en-gb/library/abx4dbyh(v=vs.80).aspx](http://msdn.microsoft.com/en-gb/library/abx4dbyh(v=vs.80).aspx)

---

### Post by jerome12345 on 2013-04-04
Sorry-I do ot get it. 

How to specify which one I should use?

---

### Post by jerome12345 on 2013-04-04
Pls see above
I was also thinking if I missed soemthing [http://ubuntuforums.org/showthread.php?t=804846](http://ubuntuforums.org/showthread.php?t=804846). IS there a difference in syntax?

---

