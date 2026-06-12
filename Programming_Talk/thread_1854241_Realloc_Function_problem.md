---
title: "Realloc Function problem"
date: 2011-10-04
forum: Programming Talk
---

### Post by Michael-Siu on 2011-10-04
Hi,

I am having trouble with the realloc function.  I wrote this little program and when I try to run it a big error msg is displayed. 

This is what the terminal shows.

```
*** glibc detected *** ./funcion: double free or corruption (fasttop): 0x00000000010e8010 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a8f)[0x7f2afb07ca8f]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x73)[0x7f2afb0808e3]
./funcion[0x4007cb]
./funcion[0x400602]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xff)[0x7f2afb022eff]
./funcion[0x400519]
======= Memory map: ========
00400000-00401000 r-xp 00000000 08:06 11020835                           /home/michael/Desktop/Codigo Fuente/funcion
00600000-00601000 r--p 00000000 08:06 11020835                           /home/michael/Desktop/Codigo Fuente/funcion
00601000-00602000 rw-p 00001000 08:06 11020835                           /home/michael/Desktop/Codigo Fuente/funcion
010e8000-01109000 rw-p 00000000 00:00 0                                  [heap]
7f2af4000000-7f2af4021000 rw-p 00000000 00:00 0 
7f2af4021000-7f2af8000000 ---p 00000000 00:00 0 
7f2afadee000-7f2afae03000 r-xp 00000000 08:06 2887361                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f2afae03000-7f2afb002000 ---p 00015000 08:06 2887361                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f2afb002000-7f2afb003000 r--p 00014000 08:06 2887361                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f2afb003000-7f2afb004000 rw-p 00015000 08:06 2887361                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f2afb004000-7f2afb18e000 r-xp 00000000 08:06 2887333                    /lib/x86_64-linux-gnu/libc-2.13.so
7f2afb18e000-7f2afb38d000 ---p 0018a000 08:06 2887333                    /lib/x86_64-linux-gnu/libc-2.13.so
7f2afb38d000-7f2afb391000 r--p 00189000 08:06 2887333                    /lib/x86_64-linux-gnu/libc-2.13.so
7f2afb391000-7f2afb392000 rw-p 0018d000 08:06 2887333                    /lib/x86_64-linux-gnu/libc-2.13.so
7f2afb392000-7f2afb398000 rw-p 00000000 00:00 0 
7f2afb398000-7f2afb3b9000 r-xp 00000000 08:06 2887320                    /lib/x86_64-linux-gnu/ld-2.13.so
7f2afb58c000-7f2afb58f000 rw-p 00000000 00:00 0 
7f2afb5b6000-7f2afb5b8000 rw-p 00000000 00:00 0 
7f2afb5b8000-7f2afb5b9000 r--p 00020000 08:06 2887320                    /lib/x86_64-linux-gnu/ld-2.13.so
7f2afb5b9000-7f2afb5bb000 rw-p 00021000 08:06 2887320                    /lib/x86_64-linux-gnu/ld-2.13.so
7fffe33d5000-7fffe33f6000 rw-p 00000000 00:00 0                          [stack]
7fffe33ff000-7fffe3400000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

```This is my little code I dont know what am I doing wrong.

```
[COLOR=DeepSkyBlue]#include[/COLOR] [COLOR=Orange]<stdio.h>[/COLOR]
[COLOR=DeepSkyBlue]#include[/COLOR] [COLOR=Orange]<stdarg.h>[/COLOR]
[COLOR=DeepSkyBlue]#include[/COLOR] [COLOR=Orange]<stdlib.h>[/COLOR]

[COLOR=RoyalBlue]int[/COLOR] list([COLOR=RoyalBlue]int[/COLOR] ,...);

[COLOR=RoyalBlue]int[/COLOR] main(){
    
    printf([COLOR=Orange]"%d"[/COLOR],list([COLOR=YellowGreen]5[/COLOR],[COLOR=YellowGreen]4[/COLOR],[COLOR=YellowGreen]3[/COLOR],[COLOR=YellowGreen]2[/COLOR],[COLOR=YellowGreen]1[/COLOR],[COLOR=YellowGreen]7[/COLOR]));
    
[COLOR=RoyalBlue]return[/COLOR] [COLOR=YellowGreen]0[/COLOR];    
}

[COLOR=RoyalBlue]int[/COLOR] list([COLOR=RoyalBlue]int[/COLOR] N,...){
    
   [COLOR=DarkRed] va_list[/COLOR] datos;
    [COLOR=DarkRed]va_start[/COLOR](datos,N);
    
    [COLOR=RoyalBlue]int[/COLOR] *ptr1=[COLOR=RoyalBlue]NULL[/COLOR], *ptr2;
    [COLOR=RoyalBlue]int[/COLOR] num;
    [COLOR=RoyalBlue]int[/COLOR] x;
    
    for(x=0; x<N; x++){
        
        num = [COLOR=DarkRed]va_arg[/COLOR](datos,[COLOR=RoyalBlue]int[/COLOR]);
        ptr2 = ([COLOR=RoyalBlue]int[/COLOR] *)realloc(ptr1,sizeof([COLOR=RoyalBlue]int[/COLOR])* (x+1));
        
        if(ptr2==[COLOR=RoyalBlue]NULL[/COLOR]){
            printf([COLOR=Orange]"Error al realocar la memoria"[/COLOR]);
            exit([COLOR=YellowGreen]1[/COLOR]);
        }
        
        ptr1 = ptr2;
        ptr1[x]    = num;
    
    }
    
free (ptr1);
free (ptr2);
[COLOR=RoyalBlue]return[/COLOR] ptr1[3];    
}

```

---

### Post by Bachstelze on 2011-10-04
```
ptr1 = ptr2;
```

Makes ptr1 and ptr2 the same pointer. Since you then do

```
free(ptr1);
free(ptr2);
```

you try to free() the same pointer twice, hence the error. Also after you free() a pointer, you cannot access its data anymore, so your return will probably cause a segmentation fault.

---

### Post by Michael-Siu on 2011-10-04
^^ yay. thnx buddy that was my noobie mistake.

---

