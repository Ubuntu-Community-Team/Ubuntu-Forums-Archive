---
title: "how do I connect functions in different files with C++?"
date: 2007-12-22
forum: Programming Talk
---

### Post by speedingbullet on 2007-12-22
I just started my first C++ program today, not 100% from scratch, I do have a small foundation on C.

I decided to convert a simple text game that I was working on in C to a new C++ version:
```

cybernetic_reality.c:
/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/


#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <iostream>
#include <cstdlib>
#include <unistd.h>
#include "story.cpp"


unsigned int sleep(unsigned int seconds);

using namespace std;

int choosegame ()
{
  int gamechoose;
  cin >> gamechoose;

if (gamechoose == 1)
{
  prolouge();
}

if (gamechoose == 2)
{
  cout <<"soon... man, soon.\n";
  return 0;
}

if (gamechoose == 3)
{
  return 0;
}

if (gamechoose == 4)
{
  cout <<"CYBER REALITY: ANARCHY CHRONICLES\n";
  cout <<"Made by Richard B.\n";
  cout <<"The stories of cyber reality are C 2007 Richard Belken & Icepick studios\n";
  cout <<"The game engine however, is free to modify & redistribute.\n";
  sleep(10);
  return 0;
}
}
//------------------------------------------


//--------------------------------------------------------------------------------

int main ()
{
  cout << "Welcome! This is not even the foundation of this program! 0.01!\n";
  sleep(4);
  cout << "Welcome Friend, This is cybernetic reality: Anarchy chronicles\n";
  cout <<"______________________________________________________________\n";
  cout <<"                                                              \n";
  cout <<"            1. NEW GAME                                       \n";
  cout <<"            2. CONTINUE                                       \n";
  cout <<"            3. QUIT GAME                                      \n";
  cout <<"            4. About game                                     \n";
  
  choosegame ();
}


```


```

story.cpp:
/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/

//Filename: story.c
//This file includes the entire, effing storyline. Major spoiler warning if you havent beaten the game.

#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <iostream>
#include <cstdlib>
#include <unistd.h>

unsigned int sleep(unsigned int seconds);

using namespace std;

int prolouge ()
{
cout <<"_______PROLOUGE__________\n";
sleep(5);
cout <<"Our story doesnt occur too long after our present day.\n";
cout <<"                                                      \n";
sleep(5);
cout <<" In the year 2030, mankind is no better off then what it is now";
sleep(5);
cout <<" But something ground breaking happens";
sleep(5);
cout <<" One man, inspired by a 31 year old anime series";
sleep(5);
cout <<" Invents a long eries of somewhat harmless commandable robots";
sleep(5);
cout <<" These are aimed at the public, so he makes sure that everything\n";
cout <<" Goes safely.\n";
sleep(5);
cout <<" The robots are quite a big hit, as the concept is to battle other";
cout <<" robots commanded by other people, usually 2 VS 2\n";
sleep(5);
cout <<" But his greatest mistake was the fact that he left himself \n";
cout <<" Off guard.";
sleep(5);
cout <<" It was christmas eve, at the robots factory\n";
cout <<" The factory workers were finally leaving for christmas night\n";
cout <<" And this man was leaving too.\n";
sleep(5);
cout <<" But then... THEY came...";
sleep(5);
cout <<" THEY slaughtered the factory workers";
sleep(5);
cout <<" THEY slaughtered this man";
sleep(5);
cout <<" THEY took over.\n";
sleep(5);
cout <<".------.  ____   ___  ______   _____   ______   ";
sleep(5);
cout <<"| .____|  '  '  '  '  | || |  |  __ |  | ___ |  ";
sleep(5);
cout <<"| |        '  ''  '   | --.'  |  ___'  | ._ '   ";
sleep(5);
cout <<"| |____.    '    '    | ||'.  | |___   | | ' '  ";
sleep(5);
cout <<"|______|     |__|     |____|  |_____|  |_|  '_' ";
sleep(5);
cout <<"      | _RE_      _AL_     _I_      _TY_ |      ";
sleep(5);
cout <<"______________________________________________  ";
cout <<"           ANARCHY CHRONICLES                   ";
cout <<"______________________________________________  ";
sleep(5);
cout <<"This will be coming soon!";
}

```

don't mind the copyright thing, its not official since I'll probably have to change the name of the game to something else.

Anyways, according to the results that Kdevelop gave me when I tried to compile this, I'm apparently connecting the choosegame() function to the prolouge() function the wrong way... how would I do this right?

---

### Post by slavik on 2007-12-22
```
gcc -o game story.c cybernetic_reality.c
```

but if it is really C++, then change the extensions to cpp and change the command to use g++ instead of gcc.

---

### Post by speedingbullet on 2007-12-22
that corrupted the story.cpp file....

---

### Post by LaRoza on 2007-12-22
Use code tags also, or php tags so we can read it.

---

### Post by speedingbullet on 2007-12-22
sorry about that

---

### Post by LaRoza on 2007-12-22
> **speedingbullet said:**
> that corrupted the story.cpp file....

What do you mean "corrupted"? Did you get an error? What was the result?

---

### Post by speedingbullet on 2007-12-22
I didnt get a resulting binary, so I compiled it with Kdevelop to see if it would do anything different:
it turned the code into this:

```
ELF              ?4   ?      4    ( % "    4   4?4?               4  4?4?                    ? ??  ?           ?  ????@  ?               ? ??   ?            H  H?H?              P?td?  ????<   <         Q?td                          /lib/ld-linux.so.2           GNU                    
                 
                                   	      
         (!
         s??K???CyIk?                ?       W                                    u       ?           ?     ?       ?      =       k      ?       I            ?     ?   @??     ?   ??     3   ???     ?   ??      libstdc++.so.6 __gmon_start__ _Jv_RegisterClasses _ZSt4cout _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc _ZNSt8ios_base4InitC1Ev _ZSt3cin _ZNSt8ios_base4InitD1Ev _ZNSirsERi __gxx_personality_v0 libm.so.6 libgcc_s.so.1 libc.so.6 _IO_stdin_used __cxa_atexit sleep __libc_start_main GLIBC_2.0 GLIBC_2.1.3 CXXABI_1.3 GLIBCXX_3.4                       ?      0   ii
   $     si	   .                  ?k   :     t)?   E      ??  @?
  ??  ??  ??   ?  ?  ?  ?  ?  ?	  ?
  U??S???    [???!  ????????t?.   ?  ?   X[???5???%??    ?%??h    ??????%??h   ??????% ?h   ??????%?h   ??????%?h    ??????%?h(   ??????%?h0   ??????%?h8   ?p????%?h@   ?`???            1?^?????PTRh?h??QVh???s????????????????U?????=l? t????$???$????u??l??ÐU?????????t?    ??t	?$?????ÐU?????E??U??}?u1?}???  u(?$p???????D$ ??D$    ?$????????ÐU???????  ?   ??????ÐU?????$p????????U?????D$???$????????$   ??????D$???$????????D$???$???p????$   ??????D$??$???P????$   ?d????D$X??$???0????$   ?D????D$???$???????$   ?$????D$???$????????$   ?????D$???$????????D$6??$????????$   ??????D$H??$????????D$???$????????$   ??????D$??$???h????D$???$???T????$   ?h????D$??$???4????D$<??$??? ????D$|??$???????$   ? ????D$???$????????$   ? ????D$???$????????$   ??????D$??$????????$   ??????D$???$????????$   ??????D$??$???l????$   ??????D$@??$???L????$   ?`????D$t??$???,????$   ?@????D$???$???????$   ? ????D$??$????????$   ? ????D$??$????????$   ??????D$D??$????????D$x??$????????D$D??$????????$   ??????D$???$???d?????U????(?E??D$?$@??Y????E???u?~????E???u ?D$Ñ?$??? ????E?    ??   ?E???u	?E?    ?o?E???ue?D$??$????????D$???$????????D$??$????????D$\??$????????$
   ??????E?    ???E??E??E??Ð?L$????q?U??Q???D$???$???c????$   ?w????D$??$???C????D$??$???/????D$\??$???????D$???$???????D$??$????????D$??$????????D$\??$????????d????    ??Y]?a?Ð???U??]Ít& ??'    U??WVS?O   ??  ???????????????????)?????t$1??E?D$?E?D$?E?$?????????9?u??[^_]Ë$Ð?U??S???????????t???????u???[]?U??S???    [??x  ?????Y[??     _______PROLOUGE__________
  Our story doesnt occur too long after our present day.
                                                       
  In the year 2030, mankind is no better off then what it is now  But something ground breaking happens   One man, inspired by a 31 year old anime series     Invents a long eries of somewhat harmless commandable robots    These are aimed at the public, so he makes sure that everything
  Goes safely.
     The robots are quite a big hit, as the concept is to battle other   robots commanded by other people, usually 2 VS 2
   But his greatest mistake was the fact that he left himself 
  Off guard.    It was christmas eve, at the robots factory
    The factory workers were finally leaving for christmas night
   And this man was leaving too.
  But then... THEY came...    THEY slaughtered the factory workers  THEY slaughtered this man  THEY took over.
  .------.  ____   ___  ______   _____   ______       | .____|  '  '  '  '  | || |  |  __ |  | ___ |      | |        '  ''  '   | --.'  |  ___'  | ._ '       | |____.    '    '    | ||'.  | |___   | | ' '      |______|     |__|     |____|  |_____|  |_|  '_'           | _RE_      _AL_     _I_      _TY_ |          ______________________________________________                 ANARCHY CHRONICLES                    This will be coming soon! soon... man, soon.
  CYBER REALITY: ANARCHY CHRONICLES
 Made by Richard B.
  The stories of cyber reality is C 2007 Richard Belken & Icepick studios
    The game engine however, is free to modify & redistribute.
 Welcome! This is not even the foundation of this program! 0.01!
    Welcome Friend, This is cybernetic reality: Anarchy chronicles
 ______________________________________________________________
                                                               
             1. NEW GAME                                       
             2. CONTINUE                                       
             3. QUIT GAME                                      
             4. About game                                     
 ;8      ????X   ????|   ????   *????   ?????   `???         zP | ???          T?E       ?   
       D   ??       ?   
       h   ??       ?   
       ?   ?\      ?   
       ?   "??       ?   
   8   ?   ???        	      ?   
   ?     ??????    ????                 ?      ?      ?      ??
   h?   h????o??   ?   ??
   Q                  ??   H            ??   ??            ???o4????o   ???o?                                                     ?        :?J?Z?j?z?????????        ?? GCC: (GNU) 4.2.1 (Ubuntu 4.2.1-5ubuntu4)  GCC: (GNU) 4.2.1 (Ubuntu 4.2.1-5ubuntu4)  GCC: (GNU) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)  GCC: (GNU) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)  GCC: (GNU) 4.2.1 (Ubuntu 4.2.1-5ubuntu4)  GCC: (GNU) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)  GCC: (GNU) 4.2.1 (Ubuntu 4.2.1-5ubuntu4)      $    ?        ??"   h?           $            ?   ??           !        ?   u   _IO_stdin_used     ?        5   ?       ????    ?   ?   Y   ?   ?   l   int ?   ?   ?   ?   v   ?   ??O    ?    K   '       /build/buildd/glibc-2.6.1/build-tree/i386-libc/csu/crti.S /build/buildd/glibc-2.6.1/build-tree/glibc-2.6.1/csu GNU AS 2.18 ??    ]   ?       /build/buildd/glibc-2.6.1/build-tree/i386-libc/csu/crtn.S /build/buildd/glibc-2.6.1/build-tree/glibc-2.6.1/csu GNU AS 2.18 ?%  $ >  $ >  $ >  4 :;I?
  & I    U%    U%   #       ?
       init.c     ?    P   ?
      /build/buildd/glibc-2.6.1/build-tree/i386-libc/csu  crti.S     ??!/!=Z!gg//  h?(!/!=Z! z    P   ?
      /build/buildd/glibc-2.6.1/build-tree/i386-libc/csu  crtn.S      ?	!!!  ??!!! /build/buildd/glibc-2.6.1/build-tree/glibc-2.6.1/csu GNU C 4.2.1 (Ubuntu 4.2.1-5ubuntu4) short unsigned int short int _IO_stdin_used long long unsigned int unsigned char init.c long long int  ????    ???h?{?        ????     ?$?????         .symtab .strtab .shstrtab .interp .note.ABI-tag .gnu.hash .dynsym .dynstr .gnu.version .gnu.version_r .rel.dyn .rel.plt .init .text .fini .rodata .eh_frame_hdr .eh_frame .ctors .dtors .jcr .dynamic .got .got.plt .data .bss .comment .debug_aranges .debug_pubnames .debug_info .debug_abbrev .debug_line .debug_str .debug_ranges                                                   4?4                    #         H?H                     5         h?h  L                1   ???o   ???  0                ;         ???  ?               C         ??  Q                 K   ???o   ?                  X   ???o   4?4  `                g   	      ???                  p   	      ???  H               y         ???  0                  t         $?$  ?                          ??  ?                 ?         h?h                    ?         ???                   ?         ???  <                  ?         ??                   ?         ???                    ?         ???                    ?         ???                    ?          ?   ?                ?         ???                   ?         ???  0                 ?         ?                    ?         @?(  4                  ?              (  k                 ?              ?  P                  ?              ?  %                               
  ?                              ?  o                  "             +  -                 .     0       X  ?                 9               @                                X  G                               h$  ?  $   <         	              ?)  ?                                     4?          H?          h?          ??          ??          ?          ?          4?          ??     	     ??     
     ??          $?          ?     
     h?          ??          ??          ?          ??          ??          ??           ?          ??          ??          ?          @?                                                                                                                      !             ??            ??            ??   ??      ,   ??      :   ??      G   l?     V   $?      ]    ?     
 s   0?     
             ??   ??      ?   ??      ?   ??      ?   ??      ?   @?     
             ???            ???   ??    
 ?   T?E    
 (  p?     6  ??    
 >  ??     T  ??      e  ??      x   ?     ?  ?       ?  @??     ?      W      ?  ?    
 ?  ?     
 ?  "??    
 ?              ?                ??     
  h?            ?     8      ?     U  ?\   
 b      ?      ?      k      ?  ??     ?  ?      ?  ???     ?   ?       ??Z    
   (?     ??(      I      @      ?     Q  t?     ??V  (?     ??]  ??     ~  :?    
 ?  ???    
 ?  ??       init.c initfini.c crtstuff.c __CTOR_LIST__ __DTOR_LIST__ __JCR_LIST__ completed.5982 p.5980 __do_global_dtors_aux frame_dummy __CTOR_END__ __DTOR_END__ __FRAME_END__ __JCR_END__ __do_global_ctors_aux cybernetic_reality.cpp _GLOBAL__I__Z8prolougev _Z41__static_initialization_and_destruction_0ii _ZSt8__ioinit __tcf_0 _GLOBAL_OFFSET_TABLE_ __init_array_end __init_array_start _DYNAMIC data_start _ZSt3cin@@GLIBCXX_3.4 __cxa_atexit@@GLIBC_2.1.3 __libc_csu_fini _start _Z10choosegamev __gmon_start__ _Jv_RegisterClasses _fp_hw _fini _ZNSt8ios_base4InitC1Ev@@GLIBCXX_3.4 __libc_start_main@@GLIBC_2.0 _Z8prolougev _ZNSt8ios_base4InitD1Ev@@GLIBCXX_3.4 _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@@GLIBCXX_3.4 _IO_stdin_used __data_start _ZSt4cout@@GLIBCXX_3.4 __dso_handle __libc_csu_init __bss_start _ZNSirsERi@@GLIBCXX_3.4 sleep@@GLIBC_2.0 _end _edata __gxx_personality_v0@@CXXABI_1.3 __i686.get_pc_thunk.bx main _init 
```

---

### Post by speedingbullet on 2007-12-22
also, I didnt want them combined as in fused, I just wanted the main file to connect to a function in story.cpp

---

### Post by kool_kat_os on 2007-12-22
what program do you use to write c++ apps?

---

### Post by speedingbullet on 2007-12-22
kdevelop

---

### Post by dwhitney67 on 2007-12-22
```
mv story.c story.cpp
mv cybernetic_reality.c cybernetic_reality.cpp
```

```
g++ story.cpp cybernetic_reality.cpp -o game
```

Then fix this problem:

```
/tmp/ccFJniSC.o: In function `prolouge()':
cyber.cpp:(.text+0x72): multiple definition of `prolouge()'
/tmp/ccQjHTWU.o:story.cpp:(.text+0x72): first defined here
collect2: ld returned 1 exit status
```

Step1:
From cybernetic_reality.cpp, remove the #include for story.cpp

Step 2:
Add the following statement to cybernetic_reality.cpp:
[FONT="Courier New"]extern int prolouge();[/FONT]

Step 3:
Recompile.

There are other issues with your program, but I leave this for you to discover.

P.S.  Did you mean to name the function prologue?  If so, your spelling within the code is incorrect.

P.S.S. I recommend that you learn to use the command line before learning or relying on graphical tools.

---

### Post by kool_kat_os on 2007-12-22
> kdevelop
thanks

---

### Post by kool_kat_os on 2007-12-22
is it easy to write c++ apps?

---

### Post by dwhitney67 on 2007-12-22
> **kool_kat_os said:**
> is it easy to write c++ apps?

No.  Many people purport to know C++, but what they put together is more C-like than C++.  Learn the principles of OO design, then the programming will follow quite easy, whether it be C++, Java, or other OO language.

---

### Post by speedingbullet on 2007-12-22
Whats wrong with Kdevelop?


Anyways, Ill try that and see if it works, thanks.

---

### Post by dwhitney67 on 2007-12-22
Nothing.  I just think that one should learn and become intimate with the command line.  X11 may not be there on your next reboot.  Then what are you going to do if you are staring at the console?  I should also add that KDE might not be installed on every system either.

---

### Post by speedingbullet on 2007-12-23
Alright, its all working now.

Thanks!

---

