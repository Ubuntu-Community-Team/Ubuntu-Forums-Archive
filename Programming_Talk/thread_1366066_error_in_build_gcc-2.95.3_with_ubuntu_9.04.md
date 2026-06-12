---
title: "error in build gcc-2.95.3 with ubuntu 9.04"
date: 2009-12-28
forum: Programming Talk
---

### Post by e2rwin on 2009-12-28
i'm still build an embedded linux system on embedded pc csb625 (arm architecture) with ubuntu 9.04 as host pc. now i still build gnu arm toolchain, but i have problems in my project. 
i'm using binutils 2.16.1, gcc-2.95.3, glibc 2.2.2 and linux kernel 2.6.11.3. 

binutils configuration succed, but i have problem at build bootsrap gcc compiler. problem in my terminal like this :

    inlined from ‘collect_execute’ at /home/erwin/ikhwan-project-2/build-tools/gcc-2.95.3/gcc/collect2.c:1762:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [collect2.o] Error 1
make[1]: Leaving directory `/home/erwin/ikhwan-project-2/build-tools/gcc'
make: *** [all-gcc] Error 2

        	  	 		  
	   	   
     
 	
at make all-gcc.

i need help for my problems, thanks a lot for all.

---

### Post by lloyd_b on 2009-12-28
That's a bug in the program code.  If open() is called with "O_CREATE", then it requires that the third parameter (the mode settings for the file) be present.

Try looking in the file /home/erwin/ikhwan-project-2/build-tools/gcc-2.95.3/gcc/collect2.c at line 1672, and see if there's an open() call with no third parameter.  You can try adding a mode of "0600" this, and see if that resolves the problem (though it may need 0700 for an executable - without knowing what file it's creating, it's hard to tell what mode to use).

Lloyd B.

---

### Post by e2rwin on 2010-01-03
Thanks for your help. the problem was solved, but now i have another problem like this 

   Aborted
  
  rm -f libgcc1.S
  
  mv tmplibgcc1.a libgcc1-asm.a
  
  make[3]: Leaving directory `/home/erwin/ikhwan-project-2/build-tools/build-boot-gcc/gcc'
  
  rm -rf tmplibgcc.a tmpcopy
  
  mkdir tmpcopy
  
  if [ xlibgcc1-asm.a != x ]; \
  
              then (cd tmpcopy; arm-linux-ar x ../libgcc1-asm.a); \
  
              else true; \
  
              fi
  
  (cd tmpcopy; chmod +w * > /dev/null 2>&1)
  
  make[2]: [stmp-multilib-sub] Error 1 (ignored)
  
  (cd tmpcopy; arm-linux-ar x ../libgcc2.a)
  
  (cd tmpcopy; arm-linux-ar rc ../tmplibgcc.a *.o)
  
  arm-linux-ar: *.o: No such file or directory
  
  make[2]: *** [stmp-multilib-sub] Error 1
  
  make[2]: Leaving directory `/home/erwin/ikhwan-project-2/build-tools/build-boot-gcc/gcc'
  
  make[1]: *** [stmp-multilib] Error 1
  
  make[1]: Leaving directory `/home/erwin/ikhwan-project-2/build-tools/build-boot-gcc/gcc'
  
  make: *** [all-gcc] Error 2


can you help me what must i do to solve this problem? thanks a lot for all.



Erwin A

---

