---
title: "Persistent compiler error - please help"
date: 2009-10-10
forum: Packaging and Compiling Programs
---

### Post by zolero on 2009-10-10
Hi all.

In the beginning I want to advise you that **I am not** a programmer, and have a very little clue about C progging language and others, but I am just an enthusiast average user. So, if you can and will help me, please do it at very low level for me, to be able to catch the point.

I was trying from a while to compile **libmpeg3** and **quicktime4linux** codec from source. First I had some problems with header locations, then few other minor things in configure and makefiles, but these are resolved. Now I have this message, when trying to compile:

```
root@bluestorm:~/downloads/buildworks/libmpeg3-1.8# ./configure --prefix=/usr
Configured successfully.  Type 'make' to build it.
root@bluestorm:~/downloads/buildworks/libmpeg3-1.8# make
Makefile:155: *** missing separator.  Stop.
root@bluestorm:~/downloads/buildworks/libmpeg3-1.8# make
gcc -c -D_REENTRANT `cat i386/c_flags`  audio/ac3.c -o i386/audio/ac3.o
gcc -c -D_REENTRANT `cat i386/c_flags`  audio/bit_allocation.c -o i386/audio/bit_allocation.o
audio/bit_allocation.c:230: error: expected ')' before '*' token
audio/bit_allocation.c:304: error: expected ')' before '*' token
audio/bit_allocation.c:362: error: expected ')' before '*' token
audio/bit_allocation.c:400: error: expected ')' before '*' token
make: *** [i386/audio/bit_allocation.o] Error 1
root@bluestorm:~/downloads/buildworks/libmpeg3-1.8#
```

I have tried to do some modifications in **bit_allocation.c**, but this was unsuccessful, and I've ran in other error messages from compiler.

First error giving portion of the code is the following:

```
void mpeg3audio_ac3_ba_compute_excitation[COLOR=Red](mpeg3audio_t *audio, [/COLOR]
        int start, 
        int end,
        int fgain,
        int fastleak, 
        int slowleak, 
        int is_lfe, 
        short bndpsd[],
        short excite[])
{
    int bin;
    int bndstrt;
    int bndend;
    int lowcomp = 0;
    int begin = 0;

/* Compute excitation function */
    bndstrt = mpeg3_masktab[start]; 
    bndend = mpeg3_masktab[end - 1] + 1; 
    
    if(bndstrt == 0) /* For fbw and lfe channels */ 
    { 
        lowcomp = mpeg3audio_ac3_calc_lowcomp(lowcomp, bndpsd[0], bndpsd[1], 0); 
        excite[0] = bndpsd[0] - fgain - lowcomp; 
        lowcomp = mpeg3audio_ac3_calc_lowcomp(lowcomp, bndpsd[1], bndpsd[2], 1);
        excite[1] = bndpsd[1] - fgain - lowcomp; 
        begin = 7 ; 
```

Other variants of **void mpeg3audio_ac3_ba_** are on lines 304, 362, and 400. Thus the error is the same on these portions, and one good solution will fix all of them. I've marked with red the incriminating code snippet on line 230.

I've also looked for the definition counterpart of this structure in the defined header file - unsuccessfull.  This file includes the following headers:

```
/* 
 *
 *    Copyright (C) Aaron Holtzman - May 1999
 *
 *
 *  This file is part of libmpeg3
 *    
 *  libmpeg3 is free software; you can redistribute it and/or modify
 *  it under the terms of the GNU General Public License as published by
 *  the Free Software Foundation; either version 2, or (at your option)
 *  any later version.
 *   
 *  libmpeg3 is distributed in the hope that it will be useful,
 *  but WITHOUT ANY WARRANTY; without even the implied warranty of
 *  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *  GNU General Public License for more details.
 *   
 *  You should have received a copy of the GNU General Public License
 *  along with GNU Make; see the file COPYING.  If not, write to
 *  the Free Software Foundation, 675 Mass Ave, Cambridge, MA 02139, USA. 
 *
 */

#include [COLOR=Red]"mpeg3audio.h"[/COLOR]
#include [COLOR=Red]<string.h>[/COLOR]

/* Bit allocation tables */

static short mpeg3_slowdec[]  = { 0x0f,  0x11,  0x13,  0x15  };
static short mpeg3_fastdec[]  = { 0x3f,  0x53,  0x67,  0x7b  };
static short mpeg3_slowgain[] = { 0x540, 0x4d8, 0x478, 0x410 };
static short mpeg3_dbpbtab[]  = { 0x000, 0x700, 0x900, 0xb00 };
```

But _**all content**_ of **mpeg3audio.h** file is this:

```
#ifndef MPEG3AUDIO_H
#define MPEG3AUDIO_H

#endif
```... thus I have no luck... OK, and what now? Can anyone give me a solution for this? Any tip, or thought will be highly appreciated. Thanks in advance,

Zolero.

---

### Post by NoaHall on 2009-10-10
```
 #include <mpeg3audio.h> 
```

and

```
 void mpeg3audio_ac3_ba_compute_excitation(mpeg3audio_t *audio) 
```

---

### Post by zolero on 2009-10-12
Thanks for your reply **NoaHall**,

... but I'm afraid that you missed something. Header file **[COLOR=black]mpeg3audio.h is already included[/COLOR]**[COLOR=black] in the source file. I've also tried to include **mpeg3proto.h** and **mpeg3private.h** (both at same time, and each separately), but without success... :(  Closing paranthesis after ***audio** was also tried, with same results. Maybe another tip will help...

Thanks anyway for trying,
Zolero.[/COLOR]

---

